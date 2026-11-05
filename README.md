# Local Happenings Bot — Prompt Pack

Reusable prompts for an AI assistant that scouts local events and emails a weekly roundup.

Generalized from a working regional events bot so anyone can recreate it. The search area is **user-set**: named towns/cities to check every week, and/or a home city plus radius.

## What it does

1. Searches concerts, festivals, sports, family events, car shows, dining nights, and ticketed shows.
2. Posts a complete weekend list in chat (sections you define — e.g. Near Home, then Trip Towns, then Book Ahead).
3. Optionally emails the same list once a week with a fixed subject line.
4. Keeps a **Book Ahead** section for early-ticket shows, plus artists you follow.

## How geography works

Set any combination in `config.example.yaml`:

- **Named locations** — list the towns/cities you want checked, grouped into primary vs secondary sections.
- **Home city + radius** — optionally also include events within N miles of a home point.
- **Spotlight town** — optional extra-focus subhead (e.g. a beach town you care about).
- **Must-check venues** — specific calendars that must be opened every week.

The assistant must not invent a region. If nothing is configured, it asks once, then saves the answer.

## Quick start (any AI assistant)

1. Copy `AGENT.md` into your assistant’s system / custom instructions.
2. Copy `WEEKLY_ROUTINE.md` into a weekly scheduled job (cron, Zapier, Make, or your bot’s routines).
3. Copy `config.example.yaml` → `config.yaml` and fill in your towns, venues, artists, and email list (or paste those values into the prompts).
4. Connect email if you want the weekly send. **Never commit real passwords or other people’s private emails to a public repo.**

## Files

| File | Purpose |
|------|---------|
| `AGENT.md` | Standing job description and rules |
| `WEEKLY_ROUTINE.md` | Full weekly search, format, and completeness gate |
| `config.example.yaml` | Locations, radius, venues, artists, email list |
| `EMAIL_TEMPLATE.md` | HTML email shape and voice |

## Completeness hard gate

Do not email a partial list. If a town or must-check venue was not finished, report gaps in chat and skip the send. One event per line; sold-out shows stay marked `SOLD OUT (resale only)`.

## Never

Post publicly, buy tickets, or book reservations. Stay quiet only when there is nothing to report and no email was due.

## License

MIT — use, fork, and adapt freely. Strip private recipient addresses before publishing.
