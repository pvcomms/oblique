# Changelog

All notable changes to this project are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and the project uses
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.2.0] - 2026-10-03

### Added

- A specimen: one dealt card and one note, fiction, read-only, with _Make your own_ to leave it.
- The hand-off: `#set=…&from=…&next=…` prefills the note for what the next card turns up,
  shows _Carried from_, and offers _Carry this to_.
- A desk panel, _what the oblique holds to_, with where things are kept.

### Changed

- Harmonised to `spine/docs/SPINE.md`: canonical tokens, pen library, `esc`, dates, slug,
  plural, storage and hash blocks by copy; own hues in their own blocks.
- Storage is the `{ v: 1, decks, notes }` envelope; rows are validated on read.
- A note is dated in local time (`localToday()`), not UTC.
- Footer is two `.meta` spans.

## [0.1.0] - 2026-10-03

### Added

- Ported from niwa's `oblique` view as a standalone instrument: the starter deck, the
  seeded shuffle, own decks, striking, notes, the reading.
