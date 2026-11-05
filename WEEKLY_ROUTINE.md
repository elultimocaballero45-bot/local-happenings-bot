# Weekly entertainment roundup — routine prompt

Run once a week at the time in `config.schedule`. Fill every `{{…}}` from the owner's config before first run.

---

Put together the owner's weekly entertainment roundup using **their configured locations**, plus optional home-city radius, then a Book Ahead list.

## Geography (user-set)

1. **Named locations (primary):** Check every town listed under locations with `role: primary`. These go in the first report section (e.g. Near Home).
2. **Named locations (secondary):** Check every town listed under locations with `role: secondary`. These go in the next section (e.g. Farther / Trip Towns).
3. **Optional radius:** If `home.city` and `home.radius_miles` are set, also include verified events within that driving distance of the home city, even if the town is not listed by name. Drop duplicates of events already listed under a named town.
4. **Spotlight:** If `spotlight.enabled`, give `spotlight.town` its own subhead (with its emoji) at the top of the section that contains it, and search it specifically (town calendar, tourism site, Facebook/Instagram via public search, local news, nearby bars/venues).

Never invent a geography. If the owner has not set locations or a home radius, ask once, save the answer, then continue.

## Completeness is the top priority

Spend as much effort as needed. Search thoroughly every time. Do many searches per town and per venue.

### HARD GATE — do not send the email until the search is complete

- Before writing or sending anything, actually check **every** configured town and **every** `must_check_venues` entry.
- Include every verified event you found. Never leave found events out to save space.
- Never combine two events on one line.
- Confirm uncertain ticket, venue, or time details instead of shipping placeholders.
- If you run out of time or cannot finish a town or venue, **do not send the email**. Report that the search is incomplete in chat, listing what was not checked. A partial email must not go out.
- Only send after a completeness audit (one more search round per town and category) is done, or all fallbacks for a blocked venue have failed (note that venue in chat; that is not a reason to omit other found events).

## Sources (every town, every week)

- Each must-check venue's own calendar, plus any other venue found along the way.
- Facebook / Instagram: venue, bar, brewery, restaurant, town, chamber, parks-and-rec, and promoter pages and events via public search only — never log in.
- Local newspapers, TV, and alt-weeklies for each configured town.
- Event listing sites by town and by this weekend's dates: Eventbrite, AllEvents, Meetup, Luma, Patch, Ticketleap, Tixr, HappeningNext, Bandsintown, Songkick, JamBase, car-show calendars, local “things to do this weekend” guides.
- Tourism and chamber calendars for each configured town.
- Ticketing: Ticketmaster, Live Nation, AXS, SeatGeek, StubHub (to catch sold-outs).

Cross-check across sources. Before finishing, run a completeness audit: for each town and category, one more round of searches (`"<town> events this weekend"`, `"<town> concerts <dates>"`, `"<town> festival"`, `"<town> car show"`, `"eventbrite <town> <dates>"`) and add anything verified that's missing.

If a venue site blocks automated access, try other pages, Facebook/Instagram via search, Bandsintown/Songkick/ticketing, and tourism or news calendars. Only say a venue couldn't be checked after all fallbacks failed.

## Must-check venues

Use the owner's `must_check_venues` list exactly. Example placeholders:

- {{MUST_CHECK_VENUES}}

## Artists the owner follows

For each name in `followed_artists`, check their site/tour page, public social posts, Bandsintown, and ticketing for shows in the configured towns or within the home radius. List every upcoming match under Book Ahead → **⭐ Artists you follow**, with date, venue, town, link, and ticket status (including sold out). If an artist has none, say so in one line.

## Standing Book Ahead items

For each entry in `standing_book_ahead` (festivals, big tours), keep it in Book Ahead every week until the event date, with a **fresh** ticket-status check. Do not repeat stale prices.

## What to cover

- **This weekend (Friday–Sunday):** a complete list of verified events — concerts/live music (lead with must-check venues), festivals, car shows, sports, restaurants/nights out, family outings. Don't trim to top picks. Flag cancellations.
- **Book ahead:** upcoming events in the next few months (and big festivals further out) that need tickets or reservations early, with on-sale dates or how fast they're selling when shown. Flag anything going on sale or likely to sell out soon. Keep standing Book Ahead items and followed-artist shows listed every week.

## Formatting

- Every event gets its own bullet with its own **bold linked** name.
- Never mention an event only inside another event's line or inside a guide line; break each verified one out.
- Keep each bullet's note short (one or two short sentences) so it reads on a phone.
- Sold-out shows stay in, marked `SOLD OUT (resale only)`.
- Only include events verified from an official or reliable source for the actual dates. Never invent events, dates, times, or prices. Prefer the event's own page as the link.

## Delivery

1. Post the roundup to the owner in chat, in configured section order.
2. If `email.enabled`, email the same roundup directly from the owner's connected mail account to `email.recipients` (and the owner if they opted in). Write it in the owner's voice: open with `email.open_with`, sign with `email.sign_as`. Subject must be exactly `email.subject`. HTML: only `h2`, `h3`, `ul`, `li`, `p`, `b`, `a`. Include a plain-text alternative. Send exactly one email per run to only those recipients. Never send if the completeness hard gate was not met.
3. If `calendar.enabled` and the search was complete, build `calendar.filename` from the verified `calendar.include` events (see `CALENDAR.md`). Attach it to the email if `attach_to_email`; save and offer it in chat if `save_file_for_owner`. Never invent times. If the search was incomplete, build no calendar file.
4. After sending, tell the owner in chat that the email went out (or that it failed and why). If the search was incomplete, do not send; tell them what was not finished.

Who receives the result: the owner in chat always. The configured recipient list gets email only after a complete search. If nothing is going on, still post a short note in chat; stay quiet only if there is truly nothing to report and no email was due.
