# Running your own

## What is Param's

Only the specimen. Everything the reader sees before _Make your own_ is invented and marked so.

| Thing                                     | Where                      | Replace with                               |
| ----------------------------------------- | -------------------------- | ------------------------------------------ |
| The specimen card, deck, note and its day | `SPECIMEN` in `index.html` | a card and a note of your own, or leave it |
| The footer's name and date                | `<footer>` in `index.html` | yours                                      |

The starter deck is not Param's: it is fifty-six prompts written for this page, in its own
words, and ships with the instrument.

## What is the instrument

The seeded shuffle, the decks and striking, adding and pasting a deck, taking a card back,
the note on what a card turned up, the readings, the hand-off and the drawn borders. All of it
is in `index.html`; the shared parts are the `capp:` blocks and are the same in every
instrument on the contract.

## Running it against your own life

1. Clone the repo, or copy `index.html` and `fonts/` together.
2. Open `index.html`. It opens on the specimen; press _Make your own_.
3. Deal. Type a card of your own into _your deck_, or paste a deck you own, one card per
   paragraph. Strike any deck to leave it out.
4. Your decks and notes are in this browser under `pp-oblique`. Clear the site's data and
   they are gone; nothing else holds them.

## What will not work yet

- A deck kept before 0.2.0 (no `v: 1` envelope) is not read back.
- Decks do not travel between browsers; there is no export.
- The sitting is forgotten on reload by design.
