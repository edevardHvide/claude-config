---
name: Post-refactor architecture (2026-04-02)
description: Feature-based folder structure, shared UI primitives, React Router — the current codebase organization
type: project
---

Major refactoring completed 2026-04-02 (phases 4-7):

**Folder structure** is now feature-based:
```
src/features/betting/    — BetFeed, BetPostForm, MyOpenBets, ActiveContracts, FinishedBets, bet.service, bets.listener
src/features/admin/      — AdminView, AdminBetList, AdminPastBets, AdminTopUpRequests, AdminPlayerList, kick.service, resolution.service
src/features/identity/   — JoinFlow, identity.service, user.listener
src/features/topup/      — TopUpButton, topup.service, topup.listener
src/features/leaderboard/ — Leaderboard, leaderboard.listener
src/shared/              — ConfirmationPopup, InstallHint, RulesModal
src/ui/                  — Button, Modal, Input, Card (shared primitives)
src/pages/               — AppShell (layout)
```

**Routing** via react-router-dom v7: `/join` (public), `/` (protected), `/admin` (protected). ProtectedRoute redirects to /join if no session.

**App name** is PolyParty (renamed from Polymarkets Finse). Firebase project ID stays `polymarkets-finse`.

**Why:** Refactored for maintainability — new features should land in one feature folder, not touch 5 layer folders.
**How to apply:** New components/services go in the relevant feature folder. Cross-feature imports are fine. Use shared UI primitives (Button, Modal, Input, Card) instead of inline Tailwind.
