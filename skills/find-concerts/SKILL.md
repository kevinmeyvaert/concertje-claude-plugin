---
name: find-concerts
description: Find upcoming concerts and gigs in Belgium or the Netherlands with the Concertje tools. Use when the user asks what's on in a Belgian or Dutch city or venue, whether an artist plays there, or about ticket status, prices, on-sale or presale dates for such a show.
---

# Find concerts in Belgium and the Netherlands

Explicit user instructions take priority over this skill.

## 1. Pick the country

- Dutch city or venue (Amsterdam, Rotterdam, Utrecht, Paradiso, Melkweg…): pass `country: 'NL'`.
- Belgian, or no place given: pass `country: 'BE'` (the default).
- A place outside Belgium and the Netherlands: say Concertje only covers those two countries. Don't call a tool.
- City names work in English, Dutch or French ("Ghent", "Gent", "Gand").

## 2. Call the right tool

- Today or tonight: `concertje_todays_concerts`, with `city` when one is given.
- From today through Sunday: `concertje_this_weeks_concerts`.
- Any other dates: `concertje_search_concerts` with `dateFrom` and `dateTo` (YYYY-MM-DD).
- A genre ("post-punk", "techno"): pass `genre` as the user wrote it, on any of these three tools,
  instead of fetching everything and filtering yourself. An unknown genre is an error: try a broader one.
- A venue: `concertje_list_venues` for its ID (match on `name` or `aliases`), then
  `concertje_search_concerts` with `venueId`.
- An artist: `concertje_search_concerts` with `search` set to the name. For genres, bio or related
  artists, call `concertje_get_artist` with an artist `id` from those results.
- Price, on-sale or presale details for one show: `concertje_get_concert` with its `id`.
- Nothing found for an artist in one country: try the other country once before saying there are no shows.
- `pagination.total` larger than the results: page with `offset` only when the user wants more.

## 3. Answer

- Once you know which concerts you'll present, call `concertje_show_concerts` once with their `id`s
  (at most 20), in the order you list them. It shows them as cards; never call it for intermediate results.
- One line per concert: date, artists, venue and city, ticket status, price, and the `url` link.
- Sort by date. More than 10 concerts: show the first 10 and say how many more there are.
- Ticket status in words: `announced` (not on sale yet), `available`, `limited` (few left), `waitlist`, `sold_out`, `cancelled`, `unknown`.
- State only prices, dates and statuses a tool returned. A missing price or on-sale date is unknown, not free.
- No results: say so plainly and suggest a wider date range or a nearby city.

## Out of scope

- Buying, reserving or saving tickets: Concertje is read-only. Give the concert page link; tickets are sold
  by the venue or ticket seller.
- Concerts the tools didn't return: don't add them from memory.
