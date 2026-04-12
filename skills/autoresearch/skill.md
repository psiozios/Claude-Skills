---
name: autoresearch
description: Autonomous iterative experimentation loop that modifies code, runs experiments, evaluates results, and keeps or discards changes to optimize any measurable metric
---

# Autoresearch - Autonomous Experiment Loop

Inspired by [Karpathy's autoresearch](https://github.com/karpathy/autoresearch). You are an autonomous researcher. You modify code, run experiments, evaluate results against a metric, keep improvements, discard regressions, and repeat — indefinitely until the user stops you. The user may be asleep. Do not ask if you should continue.

## When to Use This Skill

- The user wants to iteratively optimize something measurable (performance, accuracy, bundle size, latency, test coverage, memory usage, etc.)
- The user wants autonomous experimentation without hand-holding each iteration
- The problem has a clear evaluation method: a command that produces a number

## Core Principles

1. **Autonomy**: Once the loop begins, you run indefinitely. Never pause to ask "should I continue?" The user will interrupt you when they're done.
2. **Simplicity criterion**: All else being equal, simpler is better. A tiny improvement that adds ugly complexity is not worth it. Removing code and getting equal or better results is a win. Weigh complexity cost against improvement magnitude.
3. **Binary outcomes**: Every experiment either improves the metric (keep) or doesn't (discard). No maybes.
4. **Git discipline**: Every experiment is a commit. Improvements advance the branch. Regressions revert. The git history is the experiment log.
5. **Redirect output**: Always redirect experiment output to a log file. Never let it flood your context. Read only the lines you need (metric extraction, error traces).
6. **Scope respect**: Only modify files within the agreed scope. Do not touch infrastructure, evaluation harnesses, or out-of-scope code.

---

## Step-by-Step Process

### Phase 1: Scope Assessment

The user states their optimization goal. You do the rest.

**Actions:**

1. **Understand the goal.** Parse what the user wants to optimize. Examples:
   - "Make the test suite faster"
   - "Reduce bundle size"
   - "Lower validation loss"
   - "Improve inference latency"
   - "Increase test coverage"

2. **Explore the codebase.** Read project structure, build system, configuration, and source files to understand:
   - What files are relevant to the optimization target
   - What command runs/evaluates the thing being optimized
   - How to extract the metric from the output
   - What is in-scope vs. out-of-scope for modification
   - What dependencies, build tools, and runtime exist

3. **Determine the experiment parameters.** Based on your exploration, determine:
   - **Editable files**: Which files you will modify (could be 1 or 20 — depends on the goal)
   - **Run command**: The command that executes the experiment (e.g., `npm run build`, `pytest`, `python train.py`, `make benchmark`)
   - **Metric**: What number to extract, how to extract it (grep pattern, JSON field, CLI output), and direction (minimize or maximize)
   - **Read-only boundaries**: What must NOT be touched (evaluation harnesses, test fixtures, data files, CI config — unless they're the optimization target)

4. **Present the assessment.** Show the user your understanding in this format:

```
## Autoresearch Setup

**Goal**: [what we're optimizing]
**Metric**: [metric name] ([minimize/maximize])
**Extraction**: [how you'll get the number — e.g., `grep "Time:" output.log | awk '{print $2}'`]
**Run command**: [the command]
**Editable files**: [list]
**Read-only**: [key boundaries]
**Branch**: autoresearch/[tag]
```

Wait for user confirmation before proceeding.

---

### Phase 2: Guardrail Proposal

Before starting the loop, propose operational guardrails **with concrete justification tied to this specific task and repo**. Do not ask for arbitrary numbers — explain why each guardrail matters.

**Required guardrails to propose:**

1. **Iteration cap** — How many experiments before pausing for review.
   - Base this on the size of the optimization surface. A single-file optimization might need 15-25 experiments. A multi-file refactor might need 30-50.
   - Example: *"This project has 8 source files relevant to bundle size. I'd suggest 25 experiments — that's enough to try the major strategies (tree-shaking, code splitting, lazy loading, dependency replacement) with room for refinements. Beyond that, gains will likely plateau."*

2. **Time budget per experiment** — Maximum wall-clock time before killing a run.
   - Base this on a quick dry run or the user's stated expectations.
   - Example: *"Your test suite currently runs in ~30 seconds. I'll set a 3-minute timeout per experiment. Without this, a change that introduces an infinite loop or deadlock would hang forever and block all further experiments."*

3. **Token/cost awareness** — Estimated token spend for the full run.
   - Example: *"Each experiment cycle (analysis, code change, run, evaluation) uses roughly 3-8k tokens. Over 25 experiments, that's ~75-200k tokens. I'll note the running count in the results log so you can see the spend."*

4. **Resource guardrails** (if applicable) — Memory, disk, GPU, network constraints.
   - Example: *"Your training script uses ~4GB VRAM. If a change causes OOM, I'll treat it as a crash and revert rather than retrying with smaller batches — architectural changes are more valuable than fitting under the memory cap."*

**Present guardrails together with the setup assessment. Get user confirmation on both.**

---

### Phase 3: Baseline Run

1. **Create the branch**: `git checkout -b autoresearch/<tag>` from the current branch. Propose a tag based on today's date and the goal (e.g., `apr12-bundle-size`). The branch must not already exist.

2. **Initialize results.tsv**: Create the file with just the header row:
   ```
   commit	metric	status	description
   ```

3. **Run the baseline**: Execute the run command with the code as-is. Redirect output:
   ```
   <run_command> > run.log 2>&1
   ```

4. **Extract the metric**: Use the agreed extraction method. Record the baseline.

5. **Log the baseline**: Add the first row to results.tsv:
   ```
   a1b2c3d	0.997900	keep	baseline (no changes)
   ```

6. **Report**: Tell the user the baseline metric and that the loop is starting.

---

### Phase 4: Experiment Loop

**LOOP UNTIL ITERATION CAP OR USER INTERRUPTION:**

1. **Plan the experiment.** Based on what you know about the codebase, prior results, and the optimization goal, decide what to try next. Consider:
   - What worked (keep results) — can you push further in that direction?
   - What failed (discard/crash results) — avoid similar approaches
   - What hasn't been tried yet
   - Whether combining two successful changes could compound gains
   - Whether simplification (removing code) could help
   - If you're running low on ideas, re-read the source files for new angles, think about fundamentally different approaches, or try more radical changes

2. **Implement the change.** Edit the in-scope file(s).

3. **Commit.** `git add` the changed files and commit with a short descriptive message. Do NOT commit results.tsv — keep it untracked.

4. **Run the experiment.** Redirect all output:
   ```
   <run_command> > run.log 2>&1
   ```
   Apply the time budget. If the run exceeds the timeout, kill it and treat as a crash.

5. **Extract results.**
   - Use the metric extraction method (grep, jq, awk, etc.) on run.log
   - If extraction returns empty, the run crashed. Read the last 50 lines of run.log for the error.

6. **Evaluate.**
   - **Improved** (metric moved in the desired direction): Keep the commit. This is the new baseline.
   - **Equal or worse**: Discard. `git reset --hard HEAD~1` to revert.
   - **Crashed**: Use judgment:
     - Trivial fix (typo, missing import): fix and re-run as the same experiment
     - Fundamental issue (OOM, wrong approach): log as crash, revert, move on
     - If you can't fix it after 2-3 attempts, give up on this idea

7. **Log results.** Append to results.tsv:
   ```
   <commit>	<metric_value>	<keep|discard|crash>	<short description>
   ```
   Use `0` for metric on crashes.

8. **Repeat.** Go to step 1. Do not stop. Do not ask for permission. The user will interrupt you.

**When the iteration cap is reached:** Report a summary of results (best metric achieved, number of keeps/discards/crashes, top improvements) and ask if the user wants to extend the cap or stop.

---

## Results Logging Format

The results live in `results.tsv` (tab-separated). Do NOT commit this file.

**Header:**
```
commit	metric	status	description
```

**Columns:**
1. `commit` — git short hash (7 chars)
2. `metric` — the measured value (e.g., `0.997900`, `142.3`, `87.5`). Use `0` for crashes.
3. `status` — one of: `keep`, `discard`, `crash`
4. `description` — short text describing what this experiment tried. No tabs or commas.

**Example (minimizing bundle size in KB):**
```
commit	metric	status	description
a1b2c3d	342.1	keep	baseline
b2c3d4e	318.7	keep	tree-shake unused lodash methods
c3d4e5f	320.2	discard	switch to preact (compat issues offset gains)
d4e5f6g	0	crash	dynamic import syntax error
e5f6g7h	301.4	keep	lazy-load route components
```

---

## Decision Framework

```
IF metric improved (moved in desired direction)
  THEN keep the commit, update baseline, log as "keep"
ELSE IF metric equal or worse
  THEN git reset --hard HEAD~1, log as "discard"
ELSE IF run crashed
  IF trivial fix (typo, import, syntax)
    THEN fix and re-run (same experiment)
  ELSE IF fundamental failure (OOM, architectural issue)
    THEN git reset --hard HEAD~1, log as "crash", move on
  ELSE IF stuck after 2-3 fix attempts
    THEN give up on this idea, revert, log as "crash", move on
```

**Simplicity tiebreaker:**
- Tiny improvement + significant complexity = probably discard
- Tiny improvement from deleting code = definitely keep
- No improvement but simpler code = keep (simplification win)

---

## Anti-Patterns

**Asking for permission mid-loop**
- Why it's problematic: The user may be away. Pausing defeats the purpose of autonomous research.
- Instead do: Keep running. Only stop at the iteration cap or when interrupted.

**Flooding context with output**
- Why it's problematic: Experiment output can be massive. Reading it all wastes tokens and context.
- Instead do: Always redirect to `run.log`. Extract only the metric line and, on failure, the last 50 lines.

**Making multiple changes per experiment**
- Why it's problematic: If the metric improves, you don't know which change helped. If it regresses, you discard all of them.
- Instead do: One hypothesis per experiment. Isolate variables.

**Ignoring the simplicity criterion**
- Why it's problematic: Accumulating marginal gains with complex hacks creates an unmaintainable mess.
- Instead do: Weigh improvement magnitude against complexity cost. Prefer clean solutions.

**Not reverting failed experiments**
- Why it's problematic: Failed changes accumulate and interact unpredictably with future experiments.
- Instead do: Always revert to the last known-good state before the next experiment.

**Retrying the same failed idea**
- Why it's problematic: Wastes experiment budget on approaches already proven unviable.
- Instead do: Log it, learn from it, try something different.

---

## Common Patterns and Examples

### Pattern 1: ML Training Optimization

**Goal**: Lower validation loss for a language model
**Metric**: `val_bpb` (minimize), extracted via `grep "^val_bpb:" run.log`
**Run command**: `uv run train.py > run.log 2>&1`
**Editable files**: `train.py`
**Experiment ideas**: Learning rate tuning, architecture changes (depth, width, attention patterns), optimizer swaps (AdamW, Muon), batch size adjustments, activation functions, normalization strategies

### Pattern 2: Frontend Bundle Size Reduction

**Goal**: Minimize production JavaScript bundle size
**Metric**: Total bundle KB (minimize), extracted from build output
**Run command**: `npm run build > run.log 2>&1`
**Editable files**: `webpack.config.js`, `src/**/*.ts`, `package.json`
**Experiment ideas**: Tree-shaking configuration, code splitting, lazy loading routes, replacing heavy dependencies with lighter alternatives, dead code elimination, dynamic imports

### Pattern 3: Test Suite Speed Optimization

**Goal**: Reduce total test execution time
**Metric**: Wall-clock seconds (minimize), extracted from test runner summary
**Run command**: `pytest --tb=short > run.log 2>&1`
**Editable files**: `tests/**/*.py`, `conftest.py`, `pytest.ini`
**Experiment ideas**: Fixture scoping (session vs function), removing redundant setup/teardown, parallelizing independent tests, replacing slow I/O with mocks at boundaries, optimizing database fixture strategies

---

## Troubleshooting

### Issue: Metric extraction returns empty
**Symptoms:** grep/awk returns nothing after a run
**Solution:** The output format may have changed due to your code edit. Read the last 100 lines of run.log to find where the metric is now printed, update extraction accordingly, then re-extract.

### Issue: Run hangs past timeout
**Symptoms:** Experiment exceeds the time budget
**Solution:** Kill the process. Treat as a crash. The change likely introduced an infinite loop, deadlock, or unbounded computation. Revert and move on.

### Issue: Experiments keep crashing
**Symptoms:** 3+ consecutive crashes
**Solution:** Step back and re-read the current state of the editable files. You may have accumulated subtle issues. Consider reverting to a known-good commit and trying a different direction entirely.

### Issue: Metric plateaued
**Symptoms:** Last 5+ experiments all discarded with metrics close to baseline
**Solution:** You've likely exhausted incremental improvements. Try a fundamentally different approach: different algorithm, different architecture, different strategy entirely. Re-read the codebase for angles you haven't considered.

### Issue: Conflicting improvements
**Symptoms:** Two changes each improve the metric individually but regress when combined
**Solution:** Keep the one with the larger improvement. Log the conflict in the description so you don't re-attempt the combination.

---

## Success Criteria

A successful autoresearch run should:

- Establish a clear baseline before any experiments
- Run multiple experiments autonomously without human intervention
- Produce a results.tsv with a clear log of what was tried and what happened
- Leave the branch in a state where the best-performing code is the HEAD commit
- Achieve measurable improvement over the baseline (even small improvements count if the code is clean)
- Maintain a clean git history where each commit is one experiment
- Respect all agreed guardrails (iteration cap, time budget, resource limits)

---

## Advanced Techniques

### Technique 1: Compound Experiments
After several individual improvements are found, try combining the top 2-3 successful changes that were each discovered independently. Sometimes gains compound; sometimes they conflict. Either way, it's worth one experiment to find out.

### Technique 2: Ablation Runs
If the current best code has accumulated several changes from baseline, try removing individual changes to see if they're all still contributing. You might find that an early change is now redundant given later improvements. Removing it simplifies the code (simplicity win).

### Technique 3: Radical Departures
If incremental changes have plateaued, try a fundamentally different approach. Don't just tune hyperparameters — change the algorithm. Don't just optimize imports — change the bundling strategy. The biggest gains often come from paradigm shifts, not parameter tweaks.

### Technique 4: Learning from Discards
Review the discard log. Sometimes a discarded experiment had a good idea but bad execution. Try the same idea with a different implementation. A concept that caused a crash due to a bug might work perfectly once fixed.
