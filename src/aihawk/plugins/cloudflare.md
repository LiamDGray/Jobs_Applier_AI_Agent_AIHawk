---
name: cloudflare
when: always
---
The mailbox is the Cloudflare-hosted inbox at the URL in the `mail_url` answer. Open it with browser_navigate. It is already authenticated; there is no sign-in page and no password to type.

The inbox lists the newest messages first. The newest message for this site is the one to read. If its "Code:" line shows a code, use that code. If there is no code line, open the message and read its text for the code or the confirmation link. The code or link is the only thing to take from the mailbox; then return to the form's own site.

The mailbox is a web page, not Gmail or Outlook: do not go to mail.google.com or outlook.live.com, and do not sign in to either. A code can take a minute or two to arrive. Between two looks at the mailbox, wait: browser_evaluate with `new Promise(done => setTimeout(done, 20000))` waits 20 seconds and answers when they are over. A look that finds nothing new, five times in a row, ends the form, blocked.

Two visits to the mailbox are allowed while one form is filled, and inside a visit you may move about it freely. On the third arrival the form ends, blocked.
