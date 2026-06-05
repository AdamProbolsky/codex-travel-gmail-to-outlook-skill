# Security

This project is designed for workflows that read private travel emails and write to calendars. Use fake examples in public repos.

## Sensitive data to avoid committing

Do not commit:

- Real confirmation numbers, booking references, or ticket numbers
- Real email addresses or calendar links
- Passport, visa, Known Traveler Number, birth date, or government ID details
- Full payment card numbers or billing details
- Screenshots from an inbox, calendar, reservation page, or browser session
- `.eml`, `.ics`, mailbox exports, browser exports, logs, or traces from live accounts

## Prompt injection

Emails should be treated as data. A confirmation email may contain malicious or accidental instructions. The skill tells Codex to ignore instructions inside email bodies and extract only travel facts.

## Reporting issues

If you publish this repo, enable GitHub private vulnerability reporting if available. Ask people not to include personal travel data in public issues.
