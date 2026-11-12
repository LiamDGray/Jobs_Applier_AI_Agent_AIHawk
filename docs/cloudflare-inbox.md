# Cloudflare inbox

AIHawk can read a verification code or link from a Cloudflare Email Worker instead of Gmail or Outlook. This is useful when the application address is on a domain you control.

## What the Worker provides

The Worker in `jerbs` (`infra/cloudflare/email-worker`) receives mail for `subteaching@liamdgray.com`, extracts the code and links, and exposes:

- `GET /api/messages?to=<address>` — latest messages as JSON
- `GET /api/messages/<id>` — one message
- `GET /inbox?token=<token>` — a small HTML inbox the browser can open

It requires `INBOX_TOKEN` and returns `401` without it.

## Configure AIHawk

1. Set the inbox URL, including its token, in the environment that runs AIHawk:

   ```bash
   export AIHAWK_INBOX_URL='https://jerbs-inbox.mrgray.workers.dev/inbox?token=<token>'
   ```

   Keep the token out of shell history where possible: load it from a secret manager or a mode-0600 file.

2. Start AIHawk, press `e`, then **Your mail**.

3. Enter the application address (`subteaching@liamdgray.com`). When AIHawk asks where the mailbox is, enter `cloudflare`.

4. AIHawk stores the authenticated URL as the sealed `mail_url` answer and uses the `cloudflare.md` mailbox plugin on every form. It does not open a sign-in page and does not ask for a Gmail or Outlook password.

## Notes

- `AIHAWK_INBOX_URL` must be HTTPS; the provider refuses anything else.
- The URL and its token are sealed at rest and redacted from the dry-run trace.
- If the URL is missing, the TUI says so and leaves mail for later rather than opening a browser.
- The Worker's `/inbox` page is a normal web page; it works in the invisible-playwright Firefox that AIHawk uses.
