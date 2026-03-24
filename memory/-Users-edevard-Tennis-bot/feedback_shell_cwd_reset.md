---
name: feedback_shell_cwd_reset
description: Shell cwd resets to primary working directory when working in other repos — use pushd/popd
type: feedback
---

When working in a different repo than the primary working directory (e.g. alpine-wind while launched from Tennis-bot), `cd` resets after each Bash call.

**Why:** Claude Code resets shell cwd to the primary working directory between tool calls.

**How to apply:** Always use `pushd /path/to/other/repo > /dev/null && <commands>; popd > /dev/null` when running commands in a different repo. Never rely on `cd` persisting.
