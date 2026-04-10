---
name: automated-ui-test
description: Create and run end-to-end browser tests using Playwright with error screenshots and test reports
---

# Automated UI Test

## Overview
Creates and runs end-to-end browser tests using Playwright. Generates test scripts from user flows, handles authentication, captures error screenshots, and produces test reports covering happy paths, edge cases, and regression scenarios.

## When to Use This Skill
- Before deploying a new feature
- After making UI changes that could break existing flows
- Setting up regression test suites
- Verifying critical user journeys work end-to-end

## Process

### Step 1: Flow Definition
Identify the user flows to test:
- List each step the user takes
- Define expected outcomes at each step
- Identify required test data (credentials, form values)
- Note any prerequisites (logged in, specific state)

### Step 2: Test Script Generation
Generate Playwright test files:

```javascript
import { test, expect } from '@playwright/test';

test('user can complete checkout', async ({ page }) => {
  await page.goto('/products');
  await page.click('[data-testid="add-to-cart"]');
  await page.click('[data-testid="checkout-button"]');
  await expect(page.locator('.order-confirmation')).toBeVisible();
});
```

**For each test:**
- Use data-testid selectors (most resilient)
- Add meaningful test names
- Include assertions at each critical step
- Add screenshot capture on failure

### Step 3: Test Execution
- Run tests in headed mode first (to verify visually)
- Then run headless for CI/CD integration
- Capture screenshots on failure automatically
- Record traces for debugging complex failures

### Step 4: Report Generation
- Pass/fail summary
- Screenshots of failures
- Timing data per test
- Flaky test identification
- Suggested fixes for failures

## Key Rules
- Test user journeys, not implementation details
- Use data-testid attributes for selectors (never CSS classes)
- Each test should be independent (no test ordering dependencies)
- Clean up test data after each run
- Screenshot on every failure — it's the fastest way to debug
