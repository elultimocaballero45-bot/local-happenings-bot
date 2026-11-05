# Weekly email shape

**Subject:** exactly `{{email.subject}}` (example: `Weekend Update`)

**From:** owner's connected mail account  
**To:** everyone in `email.recipients` (and `owner.email` if they opted in)

## Body (HTML)

Allowed tags only: `h2`, `h3`, `ul`, `li`, `p`, `b`, `a`. No `style` attributes.

```html
<p>Hey everyone,</p>
<p>Here’s what’s going on this weekend, plus a few things worth booking ahead.</p>

<h2>🌳 NEAR HOME</h2>
<h3>Hometown</h3>
<ul>
  <li>🎵 <b><a href="https://example.com/event">Event Name</a></b> — Fri Nov 6, 8 PM, Venue, Town. $25.</li>
</ul>

<h2>🌊 FARTHER / TRIP TOWNS</h2>
<!-- optional spotlight subhead -->
<h3>🏖️ Spotlight Town</h3>
<ul>
  <li>…</li>
</ul>

<h2>🎟️ BOOK AHEAD</h2>
<h3>⭐ Artists you follow</h3>
<ul>
  <li>…</li>
</ul>
<h3>Other upcoming shows</h3>
<ul>
  <li>…</li>
</ul>

<p>J</p>
```

Replace the sign-off with `{{email.sign_as}}`.

## Plain text

Same words; put URLs in parentheses after each event name.
