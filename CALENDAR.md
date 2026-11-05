# Calendar export (.ics)

Optional. Turn on with `calendar.enabled: true` in `config.yaml`.

## What it is

An `.ics` file is a standard calendar file. It opens in Apple Calendar, Google Calendar, and Outlook.

## What the bot builds

One `VEVENT` per verified event from `calendar.include` (`book_ahead`, `weekend`, or `both`):

- `SUMMARY` — event name
- `DTSTART` / `DTEND` — when known; all-day (`DTSTART;VALUE=DATE`) if only the date is known
- `LOCATION` — venue + town
- `DESCRIPTION` — short note + event URL
- `URL` — event page

Rules:

- Never invent times. If the time is unknown, use all-day or omit `DTEND`.
- Sold-out shows still get an entry; put `SOLD OUT (resale only)` in the description.
- Only build the file after a complete search (same hard gate as the email).

## Delivery

- `attach_to_email: true` — attached to the weekly email.
- `save_file_for_owner: true` — saved and offered to the owner in chat.

## Adding it to your calendar

- **iPhone:** tap the `.ics` attachment or file, then "Add All".
- **Android / Google Calendar:** open the attachment in Google Calendar, or on a computer go to Google Calendar → Settings → Import & export → Import.
- **Outlook / Mac:** double-click the file.

## Reminder

The calendar is informational only. The bot never buys tickets or books anything.
