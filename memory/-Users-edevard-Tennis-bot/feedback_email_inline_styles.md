---
name: Email HTML must use inline styles for mobile
description: All HTML email components must have inline style attributes — mobile clients strip style blocks, causing invisible text
type: feedback
---

Always use inline `style` attributes on every HTML element in emails, not just CSS classes in `<style>` blocks.

**Why:** Mobile email clients (Gmail app, iOS Mail dark mode) strip `<style>` blocks entirely. This caused white text on yellow/amber backgrounds — invisible on mobile while looking fine on desktop web.

**How to apply:** When composing email HTML (send-email skill, operations-bot celebratory emails, or any email template), duplicate all critical CSS properties (especially `color`, `background`, `background-color`, `font-size`, `padding`) as inline `style` attributes. The `<style>` block is a progressive enhancement for desktop — inline styles are the baseline that must always be present.
