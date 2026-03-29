---
name: CLI over console
description: User prefers CLI commands over manual Firebase Console steps for Firestore operations
type: feedback
---

When Firestore operations are needed (seeding data, checking state), use CLI scripts or node one-liners rather than directing the user to the Firebase Console.

**Why:** User explicitly said "just do this with cli" when given Firebase Console instructions for creating a room document.

**How to apply:** For any Firestore data operations, write a quick script or use firebase CLI tools. If rules block writes, temporarily open rules → seed → restore rules → redeploy.
