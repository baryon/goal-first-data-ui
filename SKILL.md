---
name: goal-first-data-ui
description: >-
  Design or review operational, transactional, and data-heavy user-facing UI
  pages so they optimize for the user's current goal, decision, trust, and next
  action instead of specs, implementation details, or decorative chrome. Use for
  dashboards, account/profile pages, forms, list/detail views, mobile app
  screens, finance/Web3/SaaS product surfaces, pages that feel
  wizard-like/chrome-heavy/engineer-centered, or multi-screen flows where users
  need continuity. Do not apply as a blanket aesthetic for marketing, editorial,
  brand-storytelling, or education-first pages unless the user explicitly wants a
  task-flow audit. Guides Codex through a goal-first audit: identify user
  decisions, keep the data/context/trust/action needed for those decisions,
  remove irrelevant ceremony, place actions next to decision-driving data,
  translate engineering jargon, preserve feedback/recovery, and verify mobile
  density/accessibility.
---

# Goal-First Data UI

A discipline for designing task and data pages around the user's current decision. The page is not a place to display the implementation, the component library, or a generic onboarding script. It is a decision surface: show the data, context, trust signals, feedback, and actions the user needs now; remove or demote everything else.

Use this skill as a UX audit for operational interfaces. It is strongest for dashboards, forms, account states, finance/Web3/SaaS flows, and data-backed product screens. For marketing pages, narrative onboarding, education, or brand expression, use this skill only for the task-oriented parts of the experience.

## Core Rule

The user's current decision is the page.

- Data is valuable only when it helps the user answer a question, build trust, or act.
- Minimalism means removing irrelevant material, not hiding necessary feedback, risk, or context.
- Guidance should come from layout first, copy second, and forced step-by-step flows only when risk or complexity demands them.
- Technical truth still matters, but raw implementation details belong in progressive disclosure unless the primary user is technical.

## Workflow

Run this audit before changing layout or code.

### 1. Define the user goal and decision

Write 3-5 bullets in this form:

> Opening this page, the user wants to know / decide / do: ...

Include the user's likely stage when it changes the design: first-time, returning, power user, admin, investor, operator, or support user. Also name the trust anxiety if one exists: "Is my money safe?", "Did this submit?", "Can I undo this?", "Is this number current?"

If you cannot infer these with confidence, ask. Designing without the user's goal is guessing.

### 2. Map every element to a job

For each visible element, assign one job:

- **Core evidence**: data that answers the user's top question.
- **Context**: comparison, trend, timestamp, source, or explanation needed to interpret the data.
- **Trust/risk**: safety, permissions, fees, irreversible effects, verification links, custody, data freshness.
- **Action**: the next thing the user can do from this state.
- **Feedback/recovery**: loading, success, failure, retry, undo, receipt, support, or back path.
- **Advanced detail**: raw IDs, hashes, internal params, logs, or expert controls.

Delete, demote, or collapse anything that does not serve one of these jobs for the current user goal.

### 3. Prioritize the first viewport

At 375 x 800, before scrolling, the user should see:

- one core answer or metric;
- one contextual action tied to that answer, if action is possible;
- state visibility when something is loading, pending, risky, stale, or failed;
- no decorative chrome occupying the first 25% of the viewport.

A header may exist, but it should earn its space. Locale, theme, badges, long brand titles, and account vanity cards usually belong in a footer, drawer, settings page, or compact top bar.

### 4. Place actions next to decision-driving data

Trace the psychological chain:

> Seeing X, the user thinks Y, and wants to do Z.

Place Z physically next to X. Examples:

- Balance -> Deposit / Withdraw near the balance.
- Claimable reward -> Claim near the reward.
- Chain allocation -> Deposit to that chain beside the chain row.
- Failed transaction -> Retry / View details / Contact support beside the failure.

Avoid top action bars that treat rare, frequent, safe, risky, and unrelated actions as equal. Use page-level CTAs only for actions that are truly global.

### 5. Guide without wizard residue

Do not default to "Step 1 / Step 2 / Next step" cards for pages users revisit. Prefer inline states and natural adjacency.

Good guidance:

- Empty state: "No positions yet. Funds will appear here after your first deposit settles." Add a quiet inline link only if it helps.
- Success state: "Deposit submitted. View activity" plus a natural back link.
- Unavailable state: "Withdrawals unlock after settlement" beside the disabled action.

Use explicit steps when the task is rare, high-risk, irreversible, regulated, or genuinely sequential. The issue is not guidance; the issue is unnecessary ceremony.

### 6. Translate engineering language into business language

Main views should use the user's vocabulary. Keep raw values accessible but secondary.

| Engineering view | User-facing view |
|---|---|
| `tickLower` / `tickUpper` | Price range, e.g. "$1,800 - $2,200" |
| `0x123...abc` as primary label | Account name or chain/account label; raw address behind copy/details |
| `paramsHash`, `nonce`, internal IDs | Hide from main view; show in Advanced / Technical details if useful |
| "500 bps fee tier" | "0.05% trading fee" or hide if not decision-relevant |
| "Waiting for on-chain confirmation" | "Deposit pending on Ethereum" plus expected wait/recovery if known |
| "Do not click again" | Disable duplicate submit, show progress, allow safe recovery |

Never solve copy problems by narrating the implementation. Explain the user-visible state, consequence, and recovery path.

### 7. Preserve feedback and recovery

A disabled button plus spinner is not enough for slow, costly, or high-risk actions. Show:

- what is happening in user terms;
- whether the user can leave the page;
- what happens next;
- how to retry, cancel, undo, view receipt, or get help;
- a durable activity record when the action has external consequences.

Favor inline messages over modals unless the user must make a blocking decision.

### 8. Balance density with rhythm

The data is not automatically the page; the interpreted decision is the page. Use density to reduce effort, not to create a spreadsheet wall.

- Prefer typography, grouping, alignment, and dividers over heavy card chrome.
- Reserve bordered/shadowed cards for real semantic separation or confirmation moments.
- Avoid stacking more than 3 heavy cards in a row unless the domain truly benefits from card scanning.
- Give numbers comparison: previous period, trend, target, freshness, source, or allocation.
- Check long labels, localized text, and 200% text zoom before declaring the layout efficient.

## Design Master Sanity Checks

Use these as quick lenses when a page feels uncertain:

- **Don Norman**: Are affordances, signifiers, feedback, and the user's conceptual model clear?
- **Jakob Nielsen**: Is system status visible, language familiar, errors preventable/recoverable, and irrelevant content removed?
- **Dieter Rams**: Is the design useful, understandable, honest, thorough, and "less but better" rather than merely sparse?
- **Edward Tufte**: Does the page maximize meaningful data/context and minimize chartjunk, while preserving comparison and truthfulness?
- **Alan Cooper / goal-directed design**: Are you optimizing for the user's goal, not merely the task sequence or implementation model?

## Common Anti-Patterns

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Top-of-page wizard card on a returning dashboard | Treats every visit as onboarding | Inline incomplete states where the missing data appears |
| "Never explain, just show data" | Hides risk, status, and recovery | Explain consequences and state in user language |
| Stacked metric cards with border + shadow + large padding | Spends mobile viewport on chrome | Continuous stat row, table/list, or light section dividers |
| Decorative brand/header occupying mobile first screen | Delays the user's core answer | Compact top bar with one useful status chip, or move to drawer/footer |
| Equal-weight action chip bar | Misrepresents frequency, risk, and context | Put actions beside the data that motivates them |
| Per-token grid for delegated investing | Uses wallet mental model for investor mental model | Show invested value, earnings, chain/account allocation, freshness |
| Raw addresses, hashes, ticks, params in main view | Exposes implementation instead of meaning | Friendly labels in main view, raw values in Advanced details |
| "Submitted; wait; do not click again" copy | Narrates system anxiety | Disable duplicate action, show pending state, receipt, and recovery |
| Changing nav items based on state | Breaks spatial memory | Stable nav with disabled or empty states |
| Empty-state CTA billboard | Commands users before they understand state | Descriptive empty state with optional inline next action |
| Hiding fees/risk for minimalism | Creates false simplicity | Show risk/fee/custody details where they affect decisions |

## Page Patterns

### Dashboard / home

Typical user goals:

- How much do I have?
- Did it change or earn recently?
- Where exactly is my money?
- Is anything pending, stale, risky, or actionable?

Pattern:

- Net value plus recent change, freshness, and source.
- Trend or comparison when it changes interpretation.
- Allocation by the unit the user thinks in: chain, account, strategy, category, not raw token unless they manage tokens.
- Contextual actions beside each relevant balance/allocation/state.
- Recent activity with durable receipts for external actions.
- Descriptive empty states without onboarding theater.

### Account / profile

Typical user goals:

- What is the current account state?
- Is anything blocked, pending, expired, risky, or actionable?

Pattern:

- State rows with status, consequence, and action.
- Hide selectors when there is only one account.
- Keep verification, permissions, and security visible enough to build trust, but avoid making them the hero unless they are the task.

### Forms: deposit / withdraw / submit

Typical user goals:

- What is available?
- What will this cost or risk?
- What amount/option should I choose?
- Did it work, and what happens next?

Pattern:

- Relevant balance, fee/risk, and constraints above or beside the input.
- Amount input with sensible quick-fill chips.
- Only the selectors needed for the main path.
- Primary submit disabled when invalid, with the reason visible.
- Pending/success/failure states inline, with receipt, retry, and back path.
- Use explicit confirmation for irreversible, high-value, or regulated actions.

### List view

Typical user goals:

- Browse items.
- Compare key state quickly.
- Drill into one item.

Pattern:

- Rows sorted by recency, relevance, risk, or user-selected sort.
- Each row has a clear headline, key metric, status, and timestamp/freshness when meaningful.
- Make the whole row clickable when drill-in is the main action.
- Avoid tiny "Details" targets as the only path.

### Detail view

Typical user goals:

- Understand the full state of this thing.
- Decide whether to act.
- Verify technical details if needed.

Pattern:

- Translated summary at top: status, value, trend, risk, freshness.
- Actions near the data that drives the decision.
- Timeline/activity for external or asynchronous state.
- Collapsed Advanced / On-chain / Technical details for raw identifiers and logs.

### Onboarding and high-risk flows

Use more explicit guidance when the user cannot safely infer the next action.

- Break steps only when sequence matters.
- Explain consequences before irreversible actions.
- Keep progress visible, but do not let progress UI replace the actual task data.
- Let returning users resume or skip already-completed setup.

## Multi-Page Flow Continuity

When page A sends the user to page B:

- Pass enough context for page B to focus the relevant chain/account/item/action.
- Highlight or scroll to the target element when appropriate.
- Preserve user input across back/forward when safe.
- After completion, show an inline back link or natural next step.
- Keep a durable activity/receipt path for async external systems.

The user should never wonder: "Where did I end up, what happened, and how do I get back?"

## Acceptance Criteria

A page passes this skill when:

1. The 3-5 user goals/decisions are documented, including stage and trust anxiety when relevant.
2. Every kept element maps to core evidence, context, trust/risk, action, feedback/recovery, or advanced detail.
3. Mobile 375 x 800 with zero scroll shows a core answer and, when applicable, a contextual action or visible state.
4. Decorative chrome does not occupy the first 25% of the mobile viewport.
5. Actions are adjacent to the data/state that creates the user's intent.
6. Labels are readable by a non-engineer; raw technical values are hidden or demoted unless the audience is technical.
7. Loading, pending, success, failure, and unavailable states explain what happened and how to recover.
8. Empty states describe reality and offer a next action only when it genuinely helps.
9. Risk, fee, permission, freshness, and source information are visible wherever they affect decisions.
10. The layout passes basic accessibility: keyboard path, visible focus, screen-reader labels, live regions for async status, sufficient contrast, 44px touch targets, 200% text zoom, and sane localized text wrapping.
11. No more than 3 heavy card blocks are stacked without a strong semantic reason.
12. Multi-page flows preserve context and close the loop with a back path, next step, or durable receipt.
13. A realistic user can answer the page's top question within a few seconds and recover from the most common error.

If any criterion fails, iterate before shipping.

## Origin

This skill grew from repeated corrections of a delegated-LP investment dashboard: removing wizard residue, replacing wallet-template assumptions, translating engineer copy, cutting space-wasting chrome, and closing cross-page flow gaps. The current version generalizes that lesson: do not worship data for its own sake. Design around the user's goal, decision, trust, and next action.
