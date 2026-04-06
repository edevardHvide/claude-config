---
name: Balance computations must stay in sync
description: Every component showing available balance must use identical committedStake logic matching getCommittedStake()
type: feedback
---

If multiple components compute `availableBalance = balance - committedStake`, they MUST use the same committedStake formula. The canonical source is `getCommittedStake()` in bet.service.ts.

**Why:** BetPostForm only counted poster stakes but missed taker stakes on pending bets, causing it to show a different available balance than AppShell's balance card. User caught the 1kr discrepancy in production.
**How to apply:** When adding or modifying any committedStake calculation, grep for all other instances and verify they match. Currently: AppShell.tsx and BetPostForm.tsx both compute it. Consider extracting to a shared hook if a third consumer appears.
