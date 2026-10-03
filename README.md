# Oblique

## What it argues

Going round in circles is staying at the one angle you keep choosing. A card
you did not choose, taken literally, puts you somewhere you would not have
stood, and what you see from there is yours to say. The instrument picks no card
over another and never says what one means.

It deals the card. The ten minutes and what they turned up are yours.

## What it does

One card at a time, dealt from a seeded shuffle of every deck that isn't struck.
Nothing repeats until the pool is out, and then it is shuffled again.

- **The card.** Click it, press space or → to deal. ← goes back along this
  sitting's draws, and the strip of draws under the card takes you to any of
  them. _Shuffle_ deals the pool again in a new order.
- **The shuffle.** Every deck is in until you strike it. Struck decks leave the
  shuffle and are crossed through on the desk.
- **Your own decks.** Type a card into _your deck_, or name a new deck and put
  cards into that. Paste a whole deck you own and each paragraph becomes a card
  (a leading dash or star is dropped, and a line starting with `#` is read as a
  heading, not a card). A card of yours can be taken back while it is showing.
- **What it turned up.** Under the card, a note on what ten minutes with it
  turned up, kept beside the card it was about.
- **The reading.** How many cards are in how many decks, how many are in the
  shuffle now, how many were dealt this sitting, how many notes are kept. These
  are counts, never a verdict on any card.

It opens on a specimen: one card from a sitting that never happened, and what it
turned up, labelled fiction and read-only. _Make your own_ starts a sitting of
yours on the starter deck: fifty-six prompts in the page's own words. The
form is borrowed from Brian Eno and Peter Schmidt's _Oblique Strategies_
(1975), and that deck is theirs. If you own it, type or paste the cards you want
into a deck of your own.

## What it keeps, and where

Your decks and your notes are kept in this browser's `localStorage` under one
key, `pp-oblique`, and nowhere else. If the browser won't store them, the page
still deals and tells you the card wasn't kept. The sitting itself (what was
dealt, which decks are struck, the shuffle's seed) lives in page memory and is
forgotten on reload. There is no backend, no account, no analytics and no
third-party request. The two typefaces are served from `fonts/` (OFL).

## Run

```bash
open index.html
```

## Where it came from

This is the `oblique` view of niwa, Param's local garden, made to stand alone.
What changed:

- **The garden doesn't deal.** In niwa the garden added cards of its own from
  the reader's notes: a stone lying fallow, a ghost never written, one of their
  terms or values, something touched lately. Without a garden there is nothing
  to deal those from, so only the decks remain.
- **Decks live in the browser, not in files.** niwa kept each deck as a markdown
  file beside the vault, one card per paragraph. Here a deck is kept in
  `pp-oblique`. Pasting a deck reads it by the same rules the file did, and
  you can name a new deck from the page.
- **The margin becomes the note under the card.** niwa put the card on its desk
  so that a note in the margin could say what it turned up. Here the note is
  written under the card and listed in the reading.
- **No links out.** The view switcher, the theme toggle, `?id=` and the link
  from a card to its stone are gone.

The shuffle (Fisher–Yates on mulberry32), the deck rules and the readings are
ported by hand from niwa's `lib/oblique.ts`, and the drawn borders from
`lib/hand.ts`.

## Status

Prototype, 3 October 2026. Public under the MIT licence. The two typefaces in
`fonts/` stay under the SIL Open Font License.
