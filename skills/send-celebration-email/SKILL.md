---
name: send-celebration-email
description: Send a styled HTML celebration email via SMTP after resolving issues or deploying features. Each project has its own branded send_email.py script and .env SMTP credentials.
---

# Send Celebration Email

Send a beautifully styled HTML email celebrating that a user's feedback/issue was resolved.

## When to Use

Call this skill from operations-bot or similar automation after:
- A GitHub issue has been implemented and deployed
- User feedback has been addressed
- A feature request has been shipped

Only send if the issue/feedback contains a contact email.

## How It Works

Each project has a `scripts/send_email.py` that handles SMTP sending with project-specific branding (colors, logo, footer, CTA). The script reads SMTP credentials from `.env`.

### Required `.env` keys

```
EMAIL_FROM=app@gmail.com
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=app@gmail.com
SMTP_PASS=xxxx-xxxx-xxxx-xxxx
```

Use a Gmail App Password (not the account password). Generate at https://myaccount.google.com/apppasswords.

## Steps

1. **Extract email** from the GitHub issue body. Look for `**Contact:** email@example.com` or similar. If no email, skip.

2. **Write body HTML** to a temp file. Use the project's template CSS classes:
   - `.content-lead` for the opening paragraph
   - `.feature-card` with `.feature-header` + `.feature-body` for each change
   - `.cta-section` + `.cta-button` for the call-to-action link

   Example body content:
   ```html
   <p class="content-lead">
     Thanks to your report, we shipped a fix. Here's what changed:
   </p>
   <div class="feature-card">
     <div class="feature-header"><span class="feature-title">Bug Fix: Tooltip positioning</span></div>
     <div class="feature-body">The analysis box now stays on screen when clicking near edges.</div>
   </div>
   <div class="cta-section">
     <a href="https://powpredictor.info" class="cta-button">Check it out →</a>
   </div>
   ```

3. **Send the email:**
   ```bash
   echo "send" | python3 scripts/send_email.py \
     --to "user@example.com" \
     --subject "Pow Predictor: Your bug fix is live!" \
     --body-file /tmp/celebration_email.html \
     --badge-text "Shipped" \
     --header-title "Your bug fix is live!"
   ```

   Pipe `echo "send"` to auto-confirm (script prompts for confirmation in TTY).

4. **Report** back that the email was sent.

## Tone

- Warm, celebratory, human
- Not corporate or robotic
- Short — respect the reader's time
- Credit their contribution ("Thanks to your report...")

## Per-Project Setup

To add email support to a new project:

1. Copy `scripts/send_email.py` from an existing project
2. Customize the `TEMPLATE` HTML (colors, header gradient, footer text, CTA button)
3. Add SMTP credentials to `.env` (gitignored)
4. The template uses `%%PLACEHOLDER%%` markers (not `{}`) to avoid conflicts with CSS braces

## Important

- NEVER send to addresses that look auto-generated or are clearly not personal
- NEVER include internal details (Lambda names, AWS resources, code paths)
- Always pipe `echo "send"` to auto-confirm in non-TTY contexts
- Use `python3` not `python` on macOS
