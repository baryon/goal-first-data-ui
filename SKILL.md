---
name: goal-first-data-ui
description: >-
  Design or review operational, transactional, and data-heavy user-facing UI
  pages so they optimize for the user's current goal, decision, trust, and next
  action instead of specs or decorative chrome. Use for dashboards,
  account/profile pages, forms, list/detail views, mobile app screens, and
  finance/Web3/SaaS product surfaces — especially pages that feel
  wizard-like, chrome-heavy, or engineer-centered, and multi-screen flows
  where users need continuity. Do not apply as a blanket aesthetic for
  marketing, editorial, brand-storytelling, or education-first pages unless
  the user explicitly wants a task-flow audit. Guides a 10-step audit: define
  goals, decide route boundaries, map element jobs, establish one visual
  hero, place actions beside data, cut wizard residue, rewrite copy in the
  user's voice, preserve feedback, calibrate density, and gate every element
  by whether it changes a decision.
---

# Goal-First Data UI

A discipline for designing task and data pages around the user's current decision. The page is not a place to display the implementation, the component library, or a generic onboarding script. It is a decision surface: show the data, context, trust signals, feedback, and actions the user needs now; remove or demote everything else.

Use this skill as a UX audit for operational interfaces. It is strongest for dashboards, forms, account states, finance/Web3/SaaS flows, and data-backed product screens. For marketing pages, narrative onboarding, education, or brand expression, use this skill only for the task-oriented parts of the experience.

## Core Rule

The user's current decision is the page.

- Data is valuable only when it helps the user answer a question, build trust, or act.
- Minimalism means removing irrelevant material, not hiding necessary feedback, risk, or context. The principle is "less, but better" (Rams 5), not "less is more."
- Guidance should come from layout first, copy second, and forced step-by-step flows only when risk or complexity demands them.
- Technical truth still matters, but raw implementation details belong in progressive disclosure unless the primary user is technical.

## Workflow

Run this audit before changing layout or code. The steps build on each other; do not skip Step 2 (page scope) — most "page is overloaded" complaints are actually missing-route complaints.

**At a glance:**

1. Define the user goal and decision.
2. Decide page scope — split unrelated goals into routes.
3. Map every element to a job.
4. Prioritize the first viewport with one hero.
5. Place actions next to decision-driving data.
6. Guide without wizard residue.
7. Speak the user's language — vocabulary, voice, length.
8. Preserve feedback and recovery.
9. Balance density with rhythm.
10. Calibrate every element — always render, state-triggered, or not at all.

Step 10 is a discipline that runs alongside Steps 3–9, not a final cleanup pass. Whenever you map an element (Step 3), pick a hero (Step 4), or write a label (Step 7), also ask: does this always render, only on a triggering state, or never?

### 1. Define the user goal and decision

*Anchor: Cooper — goal-directed design (About Face); design serves the user's goal, not the task sequence or the implementation model.*

Write 3-5 bullets in this form:

> Opening this page, the user wants to know / decide / do: ...

Include the user's likely stage when it changes the design: first-time, returning, power user, admin, investor, operator, or support user. Also name the trust anxiety if one exists: "Is my money safe?", "Did this submit?", "Can I undo this?", "Is this number current?"

If you cannot infer these with confidence, ask. Designing without the user's goal is guessing.

### 2. Decide page scope and route boundaries

*Anchor: Cooper (goal-directed design, posture); Raskin (single locus of attention); Nielsen H8 (every extra unit competes with relevant units).*

Before laying out content, decide what this page is. A single screen carrying two unrelated goals is two screens that crashed into each other. Most "page feels overloaded" problems are routing problems, not density problems.

Split into separate routes when any of the following holds:

- Two or more goals from Step 1 use different mental models (e.g., "how am I doing" vs. "move money").
- A goal carries irreversible or high-value risk and currently shares the surface with read-only viewing.
- Goal frequency differs by an order of magnitude (daily glance vs. quarterly settings).
- Co-locating creates choice paralysis, accidental clicks, or stretches the page beyond a single coherent scan.

Three placements, in priority order:

1. **Separate route** — distinct goal, frequent enough to deserve its own URL, or risky.
2. **Same page, collapsed by default** — reference content that supports a goal without competing for attention.
3. **Drawer / sheet / modal** — short context the user needs mid-flow without losing their place.

Default to splitting. Only fuse goals onto one page when the user genuinely thinks of them as one ("check and adjust" is often one goal; "check and also configure account settings" is two).

A "dashboard" that is actually home + activity + analytics + settings + transfers is an app pretending to be a page. The fix is routing, not more cards.

**Worked split.** A "wallet" page currently shows: portfolio metrics, an inline transfer panel, a settings drawer, a swap widget, and recent activity. Step 2 splits it into:

- `/portfolio` (this page, read-only): net value, allocation, recent activity collapsed.
- `/transfer`: deposit and withdraw on their own route — the mental model and risk profile differ from viewing.
- `/settings`: rare, deep configuration; its own route.
- Swap and bridge: separate routes if they are real product surfaces; otherwise removed.

After this step, the page carries one goal ("how am I doing?"), and Steps 3–10 have a much smaller surface to discipline.

### 3. Map every element to a job

*Anchor: Norman — every visible signifier must communicate an affordance or state, otherwise it is noise (The Design of Everyday Things); Tufte — data-ink ratio: every pixel must earn its place by carrying meaning.*

For each visible element, assign one job:

- **Core evidence**: data that answers the user's top question.
- **Context**: comparison, trend, timestamp, source, or explanation needed to interpret the data.
- **Trust/risk**: safety, permissions, fees, irreversible effects, verification links, custody, data freshness.
- **Action**: the next thing the user can do from this state.
- **Feedback/recovery**: loading, success, failure, retry, undo, receipt, support, or back path.
- **Advanced detail**: raw IDs, hashes, internal params, logs, or expert controls.

Delete, demote, or collapse anything that does not serve one of these jobs for the current user goal.

### 4. Prioritize the first viewport, with one hero

At 375 x 800, before scrolling, the user should see:

- one core answer or metric;
- one contextual action tied to that answer, if action is possible;
- state visibility when something is loading, pending, risky, stale, or failed;
- no decorative chrome occupying the first 25% of the viewport.

A header may exist, but it should earn its space. Locale, theme, badges, long brand titles, and account vanity cards usually belong in a footer, drawer, settings page, or compact top bar.

**Single hero rule.** *Anchor: Tufte (layered hierarchy, smallest effective difference); Müller-Brockmann (grid hierarchy).*

The first viewport has exactly one visually dominant element — the answer to the user's top question. Everything else steps down at least one tier (size, weight, contrast, or position).

- A row of three equal-weight metric cards is three equally unimportant numbers. Pick the lead; demote the rest to supporting evidence.
- Use the smallest effective difference: `16/regular → 18/semibold` often beats `18 → 56`. Reserve dramatic contrast for the actual hero.
- Squint test: shrink the screen to 30%, or close your eyes most of the way. If the hero is not identifiable within one second, hierarchy has failed.

Equal-weight grids are layout, not hierarchy.

### 5. Place actions next to decision-driving data

*Anchor: Norman — perceived affordance is spatial: an action signifies its target by proximity (The Design of Everyday Things); Gestalt principle of proximity — elements that belong together are read together; Fitts's law — closer targets are faster and less error-prone.*

Trace the psychological chain:

> Seeing X, the user thinks Y, and wants to do Z.

Place Z physically next to X. Examples:

- Balance -> Deposit / Withdraw near the balance.
- Claimable reward -> Claim near the reward.
- Chain allocation -> Deposit to that chain beside the chain row.
- Failed transaction -> Retry / View details / Contact support beside the failure.

Avoid top action bars that treat rare, frequent, safe, risky, and unrelated actions as equal. Use page-level CTAs only for actions that are truly global.

### 6. Guide without wizard residue

*Anchor: Cooper — perpetual intermediates and the critique of wizards as "engineer-think" forced on users (About Face); Raskin — modes are the leading source of user error and split locus of attention (The Humane Interface); Nielsen H7 — flexibility and efficiency of use, accelerators for returning users.*

Do not default to "Step 1 / Step 2 / Next step" cards for pages users revisit. Prefer inline states and natural adjacency.

Good guidance:

- Empty state: "No positions yet. Funds will appear here after your first deposit settles." Add a quiet inline link only if it helps.
- Success state: "Deposit submitted. View activity" plus a natural back link.
- Unavailable state: "Withdrawals unlock after settlement" beside the disabled action.

Use explicit steps when the task is rare, high-risk, irreversible, regulated, or genuinely sequential. The issue is not guidance; the issue is unnecessary ceremony.

### 7. Speak the user's language

*Anchor: Nielsen H2 (match between system and the real world); Krug, Don't Make Me Think (cut half the words; then half again).*

Main views use the user's vocabulary, voice, and length. Translation has three passes; one alone is not enough.

**Pass 1 — Vocabulary swap.** Replace engineering tokens with user-facing terms.

| Engineering view | User-facing view |
|---|---|
| `tickLower` / `tickUpper` | Price range, e.g. "$1,800 – $2,200" |
| `0x123...abc` as primary label | Account name or chain/account label; raw address behind copy/details |
| `paramsHash`, `nonce`, internal IDs | Hide from main view; show in Advanced / Technical details if useful |
| "500 bps fee tier" | "0.05% trading fee" or hide if not decision-relevant |
| "Waiting for on-chain confirmation" | "Deposit pending on Ethereum" |
| "Do not click again" | Disable duplicate submit, show progress, allow safe recovery |

**Pass 2 — Voice: system narration → user instruction or expectation.**

Translated vocabulary is not enough if the sentence is still the system describing its own state. Rewrite into what the user should know, do, or expect.

| System voice | User voice |
|---|---|
| "Deposit submitted, please wait for confirmation." | "Sent. Should land in ~2 min." |
| "The system is processing your request." | (Show a progress state; no copy needed.) |
| "An error has occurred." | "Couldn't reach the network. Retry." |
| "Please ensure you have entered a valid amount." | "Amount must be between $10 and your balance." |
| "Upload failed: file size exceeds 10MB limit." | "This file is too big. Max 10 MB." |
| "You do not have permission to view this resource." | "Only admins can open this. Ask your admin to share." |
| "Form contains 3 errors. Please review and resubmit." | (Highlight the 3 fields inline; no banner needed.) |
| "Search returned 0 results matching your query." | "Nothing matched 'foo'. Try fewer words." |

**Pass 3 — Length: Krug's halving.**

Write the copy. Delete half. Delete half again. What survives is usually closer to right. Watch for:

- Filler: "in order to", "please note that", "for a better experience".
- Self-narration: "we are now loading", "the system is processing".
- Stating the obvious: "click the button below to continue".
- Polite hedging where directness is kinder: "if you'd like, you can…".

**Read-aloud test.** Read the page to a real user without pointing at the screen. Where you cringe, hedge, or have to add context, the copy is wrong. Voice and length are not done until this test passes.

Never solve a copy problem by narrating the implementation. Tell the user the state, the consequence, and the recovery path — in that order — and use only as many words as carry the meaning.

### 8. Preserve feedback and recovery

*Anchor: Nielsen H1 — visibility of system status; H9 — help users recognize, diagnose, and recover from errors; Norman — every action must produce immediate, perceivable feedback that closes the gulf of evaluation.*

A disabled button plus spinner is not enough for slow, costly, or high-risk actions. Show:

- what is happening in user terms;
- whether the user can leave the page;
- what happens next;
- how to retry, cancel, undo, view receipt, or get help;
- a durable activity record when the action has external consequences.

Favor inline messages over modals unless the user must make a blocking decision.

### 9. Balance density with rhythm

*Anchor: Tufte — data-ink ratio and layered hierarchy: information density is good, chartjunk and decorative chrome are not (The Visual Display of Quantitative Information); Müller-Brockmann — the grid is a system of rhythm, not a cage; whitespace and alignment do the work that borders and shadows pretend to do (Grid Systems in Graphic Design).*

The data is not automatically the page; the interpreted decision is the page. Use density to reduce effort, not to create a spreadsheet wall.

- Prefer typography, grouping, alignment, and dividers over heavy card chrome.
- Reserve bordered/shadowed cards for real semantic separation or confirmation moments.
- Avoid stacking more than 3 heavy cards in a row unless the domain truly benefits from card scanning. Step 4's single-hero rule still wins inside the first viewport — three "small enough" cards there is still hierarchy failure.
- Give numbers comparison: previous period, trend, target, freshness, source, or allocation.
- Check long labels, localized text, and 200% text zoom before declaring the layout efficient.

### 10. Calibrate, don't just minimize

*Anchor: Dieter Rams principle 5 — "less, but better" (explicitly not "less is more"); Tesler's law of conservation of complexity (every system has irreducible complexity; someone must bear it).*

This discipline runs alongside Steps 3–9, not after them. Every time you map an element to a job (Step 3), pick a hero (Step 4), or write a label (Step 7), you are also deciding whether this element should always render, render only on a triggering state, or never render at all. Treat Step 10 as the question that disciplines all earlier steps, not as a final cleanup pass.

The reflex after going through the workflow is to remove. That reflex is half right. The discipline is calibration, not subtraction.

For every element — copy, control, card, icon, link, helper text — assign exactly one of three states:

1. **Always render** — its absence would cause a wrong decision, missed risk, or lost recovery path. Examples: fees on a transaction screen, freshness on a quoted price, status of a pending submission, irreversibility warnings.
2. **Render only on triggering state** — invisible most of the time; appears precisely when needed. Examples: insufficient-balance hint, retry-after-failure block, stale-data warning, validation errors, permission-blocked notice.
3. **Never render** — decoration, product self-introduction, repetition of obvious context, premature explanation, defensive disclaimers nobody acts on.

Decision procedure for each element, in order:

1. Without this, will the user make a wrong decision, miss a risk, or lose a recovery path? → **Always render.**
2. Is there a specific state where it becomes necessary? → **Render only in that state.** Don't grey it out by default. Don't bury it behind an icon.
3. Otherwise → **don't render at all.**

**Tesler's complement.** The irreducible complexity of the underlying task does not disappear when the UI hides it. A spotless form for a complex action either exposes the complexity in a way that builds user competence and trust, or silently transfers it to support tickets, mistakes, and reversal flows later. Hiding ≠ simplifying. The honest move is to surface the right complexity at the right moment, not to manufacture an empty page.

This step is the antidote to two opposite failures: maximalist clutter on one side; reflexive minimalism that strips out risk, fees, freshness, and recovery on the other.

## Design Master Sanity Checks

Use these as principles to invoke while applying the workflow, not as a separate final pass. Each lens is the active discipline for specific steps.

- **Alan Cooper / Jef Raskin — goal-directed design, single locus of attention** (Steps 1–2): one goal per page, one focus per moment. Multiple unrelated goals on one screen are missing routes.
- **Edward Tufte — layered hierarchy, smallest effective difference** (Steps 4, 9): use the smallest visual delta that carries the meaning; reserve dramatic deltas for the actual hero. Maximize meaningful data; minimize chartjunk while preserving comparison and truthfulness.
- **Don Norman — affordances, signifiers, feedback, conceptual model** (Steps 4–5, 8): the user can see what is actionable, what is happening, and what will happen next.
- **Jakob Nielsen — heuristics**: H1 visibility of system status (Step 8), H2 match between system and the real world (Step 7), H8 aesthetic and minimalist design (Step 10) — every extra unit competes with the relevant ones.
- **Steve Krug — Don't Make Me Think** (Step 7): cut half the words, then half again; read-aloud test.
- **Dieter Rams — "less, but better"** (Step 10): useful, understandable, honest, thorough. Sparse and good are not the same word.
- **Larry Tesler — conservation of complexity** (Step 10): irreducible task complexity does not vanish when the UI hides it; it moves to the user, to support, or to rollback.

## Common Anti-Patterns

Grouped by the workflow step where the audit catches them.

**Goal & mental model (Steps 1, 3)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Per-token grid for delegated investing | Uses wallet mental model when the user is an investor, not a token manager | Show invested value, earnings, chain/account allocation, freshness |

**Page scope and routing (Step 2)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| One page bundling viewing, transacting, and configuring | Forces context-switching and competes for first-viewport real estate | Split into separate routes by goal and frequency |
| Changing nav items based on state | Breaks spatial memory across visits | Stable nav with disabled or empty states |

**First viewport and hierarchy (Step 4)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Three equal-weight metric cards as the page top | No hero — three equally unimportant numbers | Pick one lead metric; demote the rest to supporting evidence |
| Decorative brand/header occupying the mobile first screen | Delays the user's core answer | Compact top bar with one useful status chip, or move to drawer/footer |
| Stacked metric cards with border + shadow + large padding | Spends mobile viewport on chrome | Continuous stat row, table/list, or light section dividers |

**Action placement (Step 5)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Equal-weight action chip bar at top | Misrepresents frequency, risk, and context | Put actions beside the data that motivates them |

**Wizard residue (Step 6)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Top-of-page wizard card on a returning dashboard | Treats every visit as onboarding | Inline incomplete states where the missing data appears |
| Empty-state CTA billboard | Commands users before they understand state | Descriptive empty state with optional inline next action |

**Language: vocabulary, voice, length (Step 7)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Translated but system-voice copy ("X submitted, please wait") | Reads like the system narrating itself, not the user being told what to expect | Rewrite into user voice: state, consequence, expectation |
| Verbose helper text everywhere "for completeness" | Adds noise; users skip it; signal-to-noise drops | Krug halving: cut half, then half again, then read aloud |
| Raw addresses, hashes, ticks, params in main view | Exposes implementation instead of meaning | Friendly labels in main view, raw values in Advanced details |
| "Submitted; wait; do not click again" copy | Narrates system anxiety | Disable duplicate action, show pending state, receipt, and recovery |
| "Never explain, just show data" | Hides risk, status, and recovery | Explain consequences and state in user language |

**Calibration: always / on-state / never (Step 10)**

| Anti-pattern | Why it fails | Better pattern |
|---|---|---|
| Reflexive minimalism that strips fees, freshness, risk, recovery | Creates false simplicity; user makes wrong decisions | Always-render the things that change decisions |
| Hiding fees/risk for minimalism | Same failure, narrower scope | Show risk/fee/custody details where they affect decisions |
| Greyed-out controls and placeholder cards "for consistency" | Visual clutter pretending to be UI | Don't render unless the triggering state is active |

## Worked Audit Example

A "wallet" page in a delegated-LP investment app currently shows: brand banner, account selector, six metric cards (deposited, current value, total earnings, IL, fees, APY), a per-token allocation grid, an inline activity list, a "Step 1: Connect / Step 2: Deposit / Step 3: Track" wizard card on top, an inline settings panel at the bottom, and a top action bar (Deposit · Withdraw · Swap · Bridge · Settings · Help).

**Step 1 — Goals.** Returning investor: net value, performance vs last week, where the money is, anything pending or stale. Trust anxiety: "Is the number current? Is anything at risk?"

**Step 2 — Page scope.** Split into routes: `/portfolio` (this page, read-only), `/transfer` (deposit + withdraw — risky, infrequent), `/settings` (rare). Swap and Bridge get their own routes if they are real product surfaces, otherwise removed. Activity stays inline as supporting context, collapsed to the latest five rows.

**Step 3 — Element jobs.** Brand banner → never render. Wizard card → never render for the returning user. Six equal cards → one hero (current value + change + freshness) plus two or three supporting; demote IL/fees/APY to a "details" disclosure unless they trigger a state. Per-token grid → wrong mental model, replace with chain/account allocation.

**Step 4 — First viewport, one hero.** Net value + 7-day change + freshness chip is the hero. Subordinate row: invested, earnings (smaller weight, secondary color). No card chrome around the hero — typography carries the hierarchy.

**Step 5 — Action adjacency.** Deposit/Withdraw move from the top bar onto the chain-allocation row. Claim sits beside any claimable reward. Settings link moves to nav or page footer, not a top action.

**Step 6 — No wizard residue.** Delete the Step 1/2/3 card. Empty state for new users: "Funds will appear here after your first deposit settles" plus one quiet inline link.

**Step 7 — Language.** Vocabulary: replace "Impermanent Loss (IL)" with "vs holding"; "0.05 ETH at tickLower 196500" → "ETH at $1,800–$2,200". Voice: "Position pending finalization" → "Settling in ~2 min." Length: cut tooltip from 38 words to 9. Read-aloud test passes.

**Step 8 — Feedback/recovery.** Pending deposit shows "Sent. Receipt →" inline; failure shows "Couldn't reach Ethereum. Retry · Contact support" beside the row, not in a modal.

**Step 9 — Density.** Maximum three supporting metrics in a row, and only outside the first viewport. Dividers between sections, not card borders. The hero gets the largest white-space gap on the page.

**Step 10 — Calibrate.** Always render: net value, freshness, fees on the transfer route. State-triggered: stale-data warning, insufficient-balance hint, retry block, claimable-reward chip. Never render: brand banner, wizard card, settings inline panel, IL helper text in default state.

Result: first viewport is one number, one trend, one freshness chip, one stable nav. Everything else is one decision-driven scroll on this route or one click to another.

## Page Patterns

### Dashboard / home

Typical user goals:

- How much do I have?
- Did it change or earn recently?
- Where exactly is my money?
- Is anything pending, stale, risky, or actionable?

Pattern:

- Net value plus recent change, freshness, and source — as the single hero of the first viewport.
- Trend or comparison when it changes interpretation.
- Allocation by the unit the user thinks in: chain, account, strategy, category, not raw token unless they manage tokens.
- Contextual actions beside each relevant balance/allocation/state.
- Recent activity with durable receipts for external actions.
- Descriptive empty states without onboarding theater.
- Non-dashboard goals (settings, deep analytics, transfer flows) live on their own routes.

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
2. Each goal lives on a route appropriate to its mental model and frequency; no page bundles unrelated goals (Step 2).
3. Every kept element maps to core evidence, context, trust/risk, action, feedback/recovery, or advanced detail.
4. The first viewport has exactly one visually dominant hero; the squint-to-30% test identifies it within one second.
5. Mobile 375 x 800 with zero scroll shows the hero answer and, when applicable, a contextual action or visible state.
6. Decorative chrome does not occupy the first 25% of the mobile viewport.
7. Actions are adjacent to the data/state that creates the user's intent.
8. Labels are in the user's vocabulary (Pass 1), the user's voice (Pass 2), and the user's length (Pass 3 / Krug halving). The read-aloud test passes; no system self-narration survives.
9. Loading, pending, success, failure, and unavailable states explain what happened and how to recover.
10. Empty states describe reality and offer a next action only when it genuinely helps.
11. Risk, fee, permission, freshness, and source information are visible wherever they affect decisions.
12. Every visible element answers "why is this rendered right now?" — always-render, state-triggered, or removed; no defensive grey-out or placeholder clutter (Step 10).
13. The layout passes basic accessibility: keyboard path, visible focus, screen-reader labels, live regions for async status, sufficient contrast, 44px touch targets, 200% text zoom, and sane localized text wrapping.
14. No more than 3 heavy card blocks are stacked without a strong semantic reason.
15. Multi-page flows preserve context and close the loop with a back path, next step, or durable receipt.
16. A realistic user can answer the page's top question within a few seconds and recover from the most common error.

If any criterion fails, iterate before shipping.

## Origin

This skill grew from repeated corrections of a delegated-LP investment dashboard: removing wizard residue, replacing wallet-template assumptions, translating engineer copy, cutting space-wasting chrome, and closing cross-page flow gaps. The first version generalized that lesson: do not worship data for its own sake. Design around the user's goal, decision, trust, and next action.

The current revision adds explicit anchors to specific master principles — Cooper / Raskin (page scope and locus of attention), Tufte / Müller-Brockmann (single visual hero and smallest effective difference), Nielsen H2 + Krug (user vocabulary, voice, and length), Rams 5 + Tesler (calibration over reflexive minimalism) — after observing that earlier audits removed obvious clutter but still left over-loaded pages, equal-weight grids, system-voice copy, and reflexive blanks where calibrated content was needed.
