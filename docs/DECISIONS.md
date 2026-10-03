# Decisions

Append-only. One entry per real decision, dated, with the reasoning — especially
the reasoning that would otherwise be lost. A dependency added without an entry
here is a dependency added by accident.

## 2026-10-03 — adopted into the constellation

This repo now carries the shared contract: a generated node card, the kernel
from `spine/KERNEL.md`, and `.cursor/rules/capp.mdc`. Registered in
`spine/projects.json` as **oblique** (instrument, capp).

## 2026-10-03 — harmonised to SPINE.md

The file now carries the canonical blocks from `instruments/spine/index.html` (`tokens`,
`hand`, `esc`, `dates`, `slug`, `plural`, `store`, `hash`) by copy, as the contract says, and
keeps its own hues (`--rule-2`, `--accent-wash`) in their own blocks after the tokens. The
page opens on a specimen (`S.specimen`) and the button that leaves it reads _Make your own_.
The hand-off's `set` prefills the note for what the next card turns up, since that is the
field the reader writes in their own words here. Storage moved to the `{ v: 1 }` envelope;
earlier decks are not migrated, because nothing had been kept outside Param's own browser.
