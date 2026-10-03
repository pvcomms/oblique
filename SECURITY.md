# Security

## What it reads

| Path                      | Why                                                    |
| ------------------------- | ------------------------------------------------------ |
| `localStorage.pp-oblique` | the reader's own decks and notes, validated row by row |
| `location.hash`           | the hand-off (`set`, `from`, `next`), then cleared     |
| `fonts/`                  | the two typefaces beside the file                      |

## What it writes

| Path                      | What                                                                  |
| ------------------------- | --------------------------------------------------------------------- |
| `localStorage.pp-oblique` | `{ v: 1, decks, notes }`, only when the reader keeps a card or a note |

## What never leaves the machine

The reader's decks and notes. They are kept in the browser that wrote them and nowhere else:
not synced, not exported, not read by any other instrument. The specimen is never written.
The hash fragment is read by the page and never reaches a server.

## Network requests today

| Host | When | Why |
| ---- | ---- | --- |
| none |      |     |

The page is served under `default-src 'self'; connect-src 'self'; form-action 'none'` and
makes no request beyond its own file and fonts.

## Reporting

Open a private report through the repository's Security tab on GitHub, under "Report a vulnerability". Say what you found and how to reproduce it.
