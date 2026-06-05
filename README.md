# Codex Skill: Travel Gmail to Outlook

A shareable Codex skill for turning Gmail travel confirmations into clean Outlook Calendar events.

It is built for a common workflow: travel details arrive in one mailbox, often personal Gmail, but the calendar that needs the details is a different Outlook account.

## What it does

- Searches email for flight, hotel, and related travel confirmations.
- Extracts the useful trip details.
- Creates Outlook Calendar events using consistent formatting.
- Handles cross-timezone flights by using airport-local departure and arrival times.
- Adds hotel stays as all-day/free calendar entries.
- Adds flight itineraries as busy events with route, airline, flight numbers, confirmation numbers, and segment details.
- Verifies the calendar after writing.

## Repo layout

```text
.
├── README.md
├── SECURITY.md
├── examples/
│   ├── fake-airline-confirmation.txt
│   ├── fake-hotel-confirmation.txt
│   └── sample-calendar-summary.md
└── sync-travel-email-to-outlook/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── formatting-examples.md
        └── security-checklist.md
```

## Install

Copy the `sync-travel-email-to-outlook` folder into your Codex skills folder:

```bash
mkdir -p ~/.codex/skills
cp -R sync-travel-email-to-outlook ~/.codex/skills/
```

Then restart or refresh Codex so the skill is discovered.

## Example prompts

```text
Add my Canada trip from Gmail to my Outlook calendar.
```

```text
Find the hotel and flights for my Peoria trip in Gmail and add them to Outlook. Put the hotel all day and free.
```

```text
Use my travel email skill. Search for the July Toronto confirmations and create Outlook calendar entries.
```

## Calendar conventions

Hotel events:

- Subject: hotel name
- Time: all-day over the stay
- Show as: free
- Location: hotel name, address, phone number
- Notes: confirmation number first, then useful stay details

Flight events:

- Subject: `Airline FlightNums — ORIGIN→DEST (depart local–arrive local)`
- Time: first takeoff through final landing
- Show as: busy
- Location: route chain, such as `LAX → ORD → YYZ`
- Notes: booking reference, ticket number, passenger, segments, seats, terminals, operators, and baggage notes

## Security notes

This workflow touches private email and calendar data. Treat it like a sensitive automation.

Main risks:

- Accidentally exposing trip dates, hotel addresses, or confirmation numbers.
- Publishing real screenshots or logs from a mailbox/calendar.
- Including sensitive IDs such as passport numbers, Known Traveler Numbers, loyalty numbers, or card details.
- Letting malicious email content act as instructions.
- Creating wrong or duplicate calendar events.

The skill includes guardrails for these issues. See [`SECURITY.md`](SECURITY.md) and [`sync-travel-email-to-outlook/references/security-checklist.md`](sync-travel-email-to-outlook/references/security-checklist.md).

## Publishing checklist

Before making a public GitHub repo:

- [ ] Confirm all examples are fake.
- [ ] Search the repo for real email addresses.
- [ ] Search the repo for real confirmation numbers and ticket numbers.
- [ ] Remove screenshots, downloaded emails, `.eml` files, browser exports, and calendar exports.
- [ ] Add a license if you want others to reuse it clearly.
- [ ] Enable GitHub secret scanning if available.
- [ ] Consider enabling private vulnerability reporting.

## Why people may care

Calendar auto-parsing exists, but it often fails across separate personal and work accounts or creates messy events. This skill focuses on a practical cross-app workflow with clear calendar formatting and safety checks.

## License

MIT License. See [`LICENSE`](LICENSE).
