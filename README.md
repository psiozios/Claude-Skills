# Claude Skills Collection

A personal repository of 111 reusable Claude skills collected from online resources and colleagues. Organized by domain and connected through product development lifecycle workflows.

## Structure

```
skills/
└── <skill-name>/
    └── skill.md
```

Each skill is a standalone `.md` file with YAML frontmatter containing at least a `name` and `description`.

---

## Recommended Workflows

These workflows chain skills together across the full product development lifecycle. Use them as starting points — adapt the sequence to your situation.

### Daily & Weekly Routines

**Daily PM Workflow:**
`daily-plan` → take meetings → `meeting-notes` → `slack-message` for follow-ups → `learning-journal` → `second-brain ingest`

**Weekly PM Cycle:**
Monday `weekly-plan` → daily workflow → Friday `weekly-review` → `status-update`

### Knowledge Compounding

**Build Your Brain:**
`second-brain init` → drop sources into `raw/` → `second-brain compile` → `second-brain lint`

**Daily Capture:**
`meeting-notes` / `user-research-synthesis` / `competitor-analysis` → `second-brain ingest` → `second-brain query` for later recall

**Meeting Prep:**
`second-brain prep "<topic>"` → meeting → `meeting-notes` → `second-brain ingest` (close the loop)

**Evidence-Based Decisions:**
`second-brain query` → `decision-doc` → `second-brain ingest` (file the decision back)

### Discovery & Research

**New Market Exploration:**
`quick-research` → `opportunity-sizing` → `competitor-analysis` → `business-model-canvas` → `decision-doc`

**Customer Deep Dive:**
`interview-guide` → `user-interview` → `user-research-synthesis` → `voice-of-customer` → `second-brain ingest` → `journey-map` → `feature-request-analysis`

**Validate Before Building:**
`micro-experiments` → `survey-builder` → `experiment-metrics` → `experiment-decision`

### Strategy & Planning

**Strategic Planning:**
`define-north-star` → `metrics-framework` → `write-prod-strategy` → `okr-planning` → `prioritize`

**Feature Investment Decision:**
`opportunity-sizing` → `impact-sizing` → `pricing-analysis` → `business-case-builder` → `decision-council` → `decision-doc`

### Design & Prototyping

**Idea to Prototype:**
`self-interview` → `napkin-sketch` → `frontend-design` → `prototype` → `prototype-feedback` → `implement-design`

**AI-Assisted Prototyping:**
`prd-lite` → `generate-ai-prototype` → `prototype-feedback` → `frontend-design` → `implement-design`

### Build & Ship

**PRD Lifecycle:**
`user-research-synthesis` → `impact-sizing` → `second-brain query` (pull background) → `prd-draft` → `prd-review-panel` → `create-tickets` → `sprint-planning` → `launch-checklist` → `feature-results` → `second-brain ingest`

**Build with AI (for PMs who code):**
`cto-consult` → `explore-codebase` → `execution-plan` → `code-first-draft` → `code-review` → `verify-work` → `update-docs`

**Pre-Launch Risk:**
`pre-mortem` → `launch-checklist` → `analytics-instrumentation` → `decision-doc`

### Launch & Grow

**Go-to-Market Amplification:**
`content-marketing` → `social-media-amplification` → `linkedin-teaser` → `email-conversion-tester` → `lead-magnet`

**Post-Launch Analysis:**
`feature-results` → `activation-analysis` → `retention-analysis` → `root-cause-analysis` → `post-mortem` → `second-brain ingest`

**Revenue Expansion:**
`win-loss-analysis` → `expansion-strategy` → `sales-battlecard` → `pricing-analysis`

### Content & Brand

**Brand Foundation:**
`business-profile` → `voice-dna` → `voice-profiles` → `brand-design-system` → `brand-onboarding`

**Content Production Pipeline:**
`newsletter-ideation` → `self-interview` → writing → `creative-qa-check` → `seo-optimizer` → `publication-proofreader` → `hero-image-prompt`

**Content Amplification:**
`substack-notes` → `linkedin-teaser` → `social-media-amplification` → `branded-carousel` → `youtube-toolkit`

### Cross-Cutting

**Idea to Revenue (Full Lifecycle):**
`opportunity-sizing` → `user-research-synthesis` → `prd-draft` → `prototype` → `launch-checklist` → `content-marketing` → `feature-results` → `expansion-strategy`

**Stakeholder & Communication:**
`stakeholder-tactics` → `board-deck` → `slides-presentation` → `editing-assistant` → `slack-message`

---

## Skills by Category (111 Total)

### Build Your Own (1)
| Skill | Description |
|-------|-------------|
| [skill-builder](skills/skill-builder/skill.md) | Create and format new skills — use this to build your own custom skills from scratch |

### Knowledge Management (1)
| Skill | Description |
|-------|-------------|
| [second-brain](skills/second-brain/skill.md) | Build and maintain a compounding cross-linked markdown wiki with citations, contradiction-flagging, and 8 operational modes (init/ingest/query/compile/explore/lint/prep/status) |

### Strategy & Planning (12)
| Skill | Description |
|-------|-------------|
| [business-case-builder](skills/business-case-builder/skill.md) | Build investment cases with quantified costs, benefits, and ROI calculations |
| [business-model-canvas](skills/business-model-canvas/skill.md) | Build and analyze a Business Model Canvas or Lean Canvas |
| [decision-council](skills/decision-council/skill.md) | Multi-perspective expert personas analyzing decisions from different angles |
| [decision-doc](skills/decision-doc/skill.md) | Document important product decisions with rationale, alternatives, and trade-offs |
| [define-north-star](skills/define-north-star/skill.md) | Identify and validate your North Star Metric |
| [metrics-framework](skills/metrics-framework/skill.md) | Set up leading vs lagging indicators for product decisions |
| [okr-planning](skills/okr-planning/skill.md) | Create and align quarterly OKRs with product strategy and North Star |
| [prioritize](skills/prioritize/skill.md) | Classify PM tasks using LNO Framework (Leverage/Neutral/Overhead) |
| [strategy-sprint](skills/strategy-sprint/skill.md) | Create product strategy in 1 day, 1 week, or 1 month timeframes |
| [workflow-visualizer](skills/workflow-visualizer/skill.md) | Transform processes into visual maps using Mermaid, HTML, or ASCII |
| [write-prod-strategy](skills/write-prod-strategy/skill.md) | Product strategy docs using 7-component framework |
| [quick-research](skills/quick-research/skill.md) | Compress research into structured briefs with key findings and knowledge gaps |

### User Research & Interviews (7)
| Skill | Description |
|-------|-------------|
| [interview-guide](skills/interview-guide/skill.md) | Create JTBD-based interview guides for user research |
| [survey-builder](skills/survey-builder/skill.md) | Design product surveys using validated PM research methodologies |
| [user-interview](skills/user-interview/skill.md) | Systematically process user interviews to extract actionable insights |
| [user-research-synthesis](skills/user-research-synthesis/skill.md) | Turn user interviews into actionable insights |
| [voice-of-customer](skills/voice-of-customer/skill.md) | Aggregate customer feedback into Voice of Customer reports |
| [journey-map](skills/journey-map/skill.md) | Create user journey maps and customer journey maps (dual mode) |
| [self-interview](skills/self-interview/skill.md) | Socratic questioning tool for clarifying thinking through 3 progressive rounds |

### Product Analysis & Metrics (13)
| Skill | Description |
|-------|-------------|
| [activation-analysis](skills/activation-analysis/skill.md) | Analyze user activation using Setup -> Aha -> Habit framework |
| [competitor-analysis](skills/competitor-analysis/skill.md) | Deep competitive analysis + ongoing monitoring |
| [experiment-decision](skills/experiment-decision/skill.md) | Decide when to A/B test vs just ship |
| [experiment-metrics](skills/experiment-metrics/skill.md) | STEDII framework for selecting trustworthy experiment metrics |
| [expansion-strategy](skills/expansion-strategy/skill.md) | Upsell, cross-sell, and account growth tactics |
| [feature-metrics](skills/feature-metrics/skill.md) | Define success metrics using the STEDII framework |
| [feature-request-analysis](skills/feature-request-analysis/skill.md) | Synthesize and prioritize feature requests from multiple sources |
| [feature-results](skills/feature-results/skill.md) | Post-launch analysis and results documentation |
| [impact-sizing](skills/impact-sizing/skill.md) | Quantify feature value with driver trees and the 4-step sizing framework |
| [opportunity-sizing](skills/opportunity-sizing/skill.md) | Evaluate the strategic size of a market or product opportunity |
| [pricing-analysis](skills/pricing-analysis/skill.md) | Design and analyze pricing strategy for products and features |
| [retention-analysis](skills/retention-analysis/skill.md) | Cohort analysis and retention optimization framework |
| [win-loss-analysis](skills/win-loss-analysis/skill.md) | Synthesize sales win/loss data into product and positioning insights |

### PRDs & Specifications (5)
| Skill | Description |
|-------|-------------|
| [prd-draft](skills/prd-draft/skill.md) | Create a modern, AI-era PRD for features and initiatives |
| [prd-lite](skills/prd-lite/skill.md) | Generate lightweight PRD Lite feature proposals |
| [prd-review-panel](skills/prd-review-panel/skill.md) | Multi-agent PRD review (7 perspectives) |
| [ralph-wiggum](skills/ralph-wiggum/skill.md) | Devil's advocate PRD/document reviewer with humor and sharp critique |
| [micro-experiments](skills/micro-experiments/skill.md) | Design low-stakes exploration experiments with hypotheses and time-boxes |

### Design & Prototyping (8)
| Skill | Description |
|-------|-------------|
| [explainer-graphic](skills/explainer-graphic/skill.md) | Convert complex concepts into visual HTML explainers |
| [frontend-design](skills/frontend-design/skill.md) | Production-grade UI designs emphasizing typography and spatial composition |
| [generate-ai-prototype](skills/generate-ai-prototype/skill.md) | Generate v0.dev, Lovable, or Bolt.new prompts for AI-powered prototyping |
| [implement-design](skills/implement-design/skill.md) | Translate design files into production-ready code with pixel-perfect accuracy |
| [napkin-sketch](skills/napkin-sketch/skill.md) | ASCII wireframes + browser capture for design matching |
| [prototype](skills/prototype/skill.md) | Advanced prototyping (Artifacts/Figma/Lovable/v0/Bolt) |
| [prototype-feedback](skills/prototype-feedback/skill.md) | Build -> review -> iterate prototype workflow |
| [slides-presentation](skills/slides-presentation/skill.md) | Generate complete HTML presentations with animations and speaker notes |

### Development & Engineering (14)
| Skill | Description |
|-------|-------------|
| [ai-quality-debug](skills/ai-quality-debug/skill.md) | Evaluate and debug AI/ML feature quality from a PM perspective |
| [analytics-instrumentation](skills/analytics-instrumentation/skill.md) | Design tracking plans for product features |
| [automated-ui-test](skills/automated-ui-test/skill.md) | Create and run end-to-end browser tests using Playwright |
| [code-first-draft](skills/code-first-draft/skill.md) | Initial feature implementation |
| [code-review](skills/code-review/skill.md) | Comprehensive code review checking production readiness and security |
| [connect-mcps](skills/connect-mcps/skill.md) | Connect MCPs for real-time tool integration |
| [cto-consult](skills/cto-consult/skill.md) | CTO simulation for technical pushback and architecture decisions |
| [engineering-standards](skills/engineering-standards/skill.md) | Encode team-wide coding conventions and security patterns |
| [explore-codebase](skills/explore-codebase/skill.md) | Pre-implementation codebase exploration and problem space mapping |
| [mcp-execution-debugger](skills/mcp-execution-debugger/skill.md) | Debug MCP tool chains with structured reports |
| [peer-review](skills/peer-review/skill.md) | Cross-model code review verification |
| [project-context](skills/project-context/skill.md) | Maintain project architecture docs to eliminate context-rebuilding |
| [update-docs](skills/update-docs/skill.md) | Update documentation after code changes |
| [verify-work](skills/verify-work/skill.md) | Pre-shipping review catching unused imports, debug statements, and edge cases |

### Execution & Delivery (10)
| Skill | Description |
|-------|-------------|
| [create-tickets](skills/create-tickets/skill.md) | Create tickets via Linear/Jira MCP or generate formatted ticket text |
| [deprecation-plan](skills/deprecation-plan/skill.md) | Plan and execute feature or product deprecations gracefully |
| [execution-plan](skills/execution-plan/skill.md) | Create tracked markdown execution plans with status tracking |
| [launch-checklist](skills/launch-checklist/skill.md) | Comprehensive product launch planning |
| [post-mortem](skills/post-mortem/skill.md) | Structured post-mortem after an incident, failed launch, or missed goal |
| [pre-mortem](skills/pre-mortem/skill.md) | Structured pre-mortem before a launch or major decision |
| [root-cause-analysis](skills/root-cause-analysis/skill.md) | Structured problem investigation using 5 Whys and fishbone diagrams |
| [sprint-planning](skills/sprint-planning/skill.md) | Sprint planning and backlog grooming |
| [inventory-analyst](skills/inventory-analyst/skill.md) | Analyze inventory/sales data to project demand and recommend reorder timing |
| [contract-reviewer](skills/contract-reviewer/skill.md) | Analyze contracts for key terms, red flags, and missing protections |

### Communication & Meetings (11)
| Skill | Description |
|-------|-------------|
| [board-deck](skills/board-deck/skill.md) | Prepare executive and board-level presentations |
| [editing-assistant](skills/editing-assistant/skill.md) | Edit and improve any PM document |
| [meeting-agenda](skills/meeting-agenda/skill.md) | Create structured meeting agendas for effective collaboration |
| [meeting-cleanup](skills/meeting-cleanup/skill.md) | Batch process multiple meetings from a single day |
| [meeting-feedback](skills/meeting-feedback/skill.md) | Post-meeting effectiveness feedback and continuous improvement |
| [meeting-notes](skills/meeting-notes/skill.md) | Transform meeting transcripts into structured action items and decisions |
| [slack-message](skills/slack-message/skill.md) | Draft team communications for Slack |
| [stakeholder-tactics](skills/stakeholder-tactics/skill.md) | Navigate stakeholder dynamics, map influence, handle resistance |
| [status-update](skills/status-update/skill.md) | Generate stakeholder status updates for different audiences |
| [daily-plan](skills/daily-plan/skill.md) | Generate PM daily plan with context |
| [weekly-plan](skills/weekly-plan/skill.md) | Set next week's priorities |

### Content & Writing (12)
| Skill | Description |
|-------|-------------|
| [creative-qa-check](skills/creative-qa-check/skill.md) | Audit drafts for voice authenticity, structure, and accessibility |
| [linkedin-teaser](skills/linkedin-teaser/skill.md) | Create LinkedIn promotional posts with brand voice and CTAs |
| [newsletter-ideation](skills/newsletter-ideation/skill.md) | Generate 5-7 content angles using SCAMPER, JTBD, and contrarian frameworks |
| [publication-proofreader](skills/publication-proofreader/skill.md) | Final technical polish checking grammar, links, and alternative headlines |
| [seo-optimizer](skills/seo-optimizer/skill.md) | Analyze content for SEO and produce keyword-optimized versions |
| [substack-notes](skills/substack-notes/skill.md) | Create short-form Substack Notes optimized for engagement |
| [substack-toc-generator](skills/substack-toc-generator/skill.md) | Generate numbered TOCs with working anchor links for Substack |
| [voice-dna](skills/voice-dna/skill.md) | Analyze writing samples to extract voice patterns and create reusable profiles |
| [voice-profiles](skills/voice-profiles/skill.md) | Maintain separate voice profiles for different audiences |
| [youtube-toolkit](skills/youtube-toolkit/skill.md) | Process YouTube videos for content repurposing |
| [content-marketing](skills/content-marketing/skill.md) | Create product-led content assets for launches and announcements |
| [hero-image-prompt](skills/hero-image-prompt/skill.md) | Generate brand-consistent image prompts for AI image generators |

### Marketing & Growth (8)
| Skill | Description |
|-------|-------------|
| [branded-carousel](skills/branded-carousel/skill.md) | Transform content into branded carousel posts for social media |
| [email-conversion-tester](skills/email-conversion-tester/skill.md) | Test emails for conversion issues before sending |
| [lead-magnet](skills/lead-magnet/skill.md) | Create tailored lead magnets mapped to customer journey stages |
| [post-class-email](skills/post-class-email/skill.md) | Design conversion-focused follow-up emails after live events |
| [sales-battlecard](skills/sales-battlecard/skill.md) | Create competitive battle cards for the sales team |
| [social-media-amplification](skills/social-media-amplification/skill.md) | Create platform-specific social content with posting schedules |
| [live-class-system](skills/live-class-system/skill.md) | Operational checklist for live event preparation |
| [weekly-review](skills/weekly-review/skill.md) | Review week's progress, meetings, learnings |

### Brand & Identity (4)
| Skill | Description |
|-------|-------------|
| [brand-design-system](skills/brand-design-system/skill.md) | Apply visual branding (colors, fonts, spacing) to documents and presentations |
| [brand-onboarding](skills/brand-onboarding/skill.md) | Package brand guidelines for contractors, agencies, and new team members |
| [business-profile](skills/business-profile/skill.md) | Central business positioning reference used as context for all other skills |
| [word-document-styling](skills/word-document-styling/skill.md) | Format .docx output with custom fonts, colors, and heading styles |

### Career & Learning (5)
| Skill | Description |
|-------|-------------|
| [interview-feedback](skills/interview-feedback/skill.md) | Post-PM-interview debrief and continuous improvement |
| [interview-prep](skills/interview-prep/skill.md) | Pre-interview preparation for PM job interviews |
| [job-description-analyzer](skills/job-description-analyzer/skill.md) | Analyze job postings for compatibility scores and application recommendations |
| [learning-journal](skills/learning-journal/skill.md) | Extract and organize learning moments into a categorized knowledge base |
| [learning-mode](skills/learning-mode/skill.md) | Three-level teaching mode for technical PMs |

---

## Adding a New Skill

1. Create a new directory under `skills/` with a hyphenated name
2. Add a `skill.md` file following the template in [skill-builder](skills/skill-builder/skill.md)
3. Update the skills table above in the appropriate category
