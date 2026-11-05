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

## First-run setup wizard

Do these once, in order.

1. **Get the files.** Fork this repo or download it as a ZIP.
2. **Make your config.** Copy `config.example.yaml` → `config.yaml`. Never commit real emails or passwords to a public repo.
3. **Set who and where.** Fill in `owner` (name, email), then `locations` (towns to check) and/or `home` (city + radius). Optional: a `spotlight` town.
4. **Add your favorites.** List `must_check_venues` and `followed_artists`.
5. **Load the prompts.** Paste `AGENT.md` into your assistant's system / custom instructions. If your assistant can't read `config.yaml`, paste your values into the `{{PLACEHOLDERS}}` in `WEEKLY_ROUTINE.md`.
6. **Schedule it.** Create a weekly job (Thursday morning recommended) that runs `WEEKLY_ROUTINE.md`.
7. **Email (optional).** Connect a mail account, then set `email.subject`, `recipients`, `open_with`, and `sign_as`.
8. **Calendar (optional).** Set `calendar.enabled: true` to get a weekly `.ics` file. See `CALENDAR.md`.
9. **Test run.** Run the routine once by hand in chat (no email) and check the list before trusting the first send.
10. **Confirm the hard gate.** Make sure the bot never emails a partial list (see below).

## Files

| File | Purpose |
|------|---------|
| `AGENT.md` | Standing job description and rules |
| `WEEKLY_ROUTINE.md` | Full weekly search, format, and completeness gate |
| `config.example.yaml` | Locations, radius, venues, artists, email list |
| `EMAIL_TEMPLATE.md` | HTML email shape and voice |
| `CALENDAR.md` | Optional .ics calendar export |

## Completeness hard gate

Do not email a partial list. If a town or must-check venue was not finished, report gaps in chat and skip the send. One event per line; sold-out shows stay marked `SOLD OUT (resale only)`.

## Never

Post publicly, buy tickets, or book reservations. Stay quiet only when there is nothing to report and no email was due.

## License

MIT — use, fork, and adapt freely. Strip private recipient addresses before publishing.
