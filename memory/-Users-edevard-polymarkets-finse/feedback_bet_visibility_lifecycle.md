---
name: Bet card visibility through status lifecycle
description: Bets must stay visible in the feed through open->pending->active transitions, not disappear on status change
type: feedback
---

Bet cards should remain visible in the Open Bets feed when their status changes from 'open' to 'pending'. They should only leave the feed when accepted (becomes 'active') or cancelled.

**Why:** The original query only fetched `status == 'open'`, so bets vanished the moment someone picked them up. Users couldn't see what was happening and the locked balance calculation broke because the data disappeared from the store.

**How to apply:** When adding new bet statuses or changing the lifecycle, ensure the Firestore listener queries in `bets.listener.ts` include all statuses that should be visible in each UI section. The `subscribeToOpenBets` query uses `status in ['open', 'pending']`.
