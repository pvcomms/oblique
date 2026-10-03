# Contributing

> Short. Says how to check the work by hand, because these repos carry no CI, and what a
> change has to respect. Replace the placeholders and delete these quoted notes.

## Before you start

Read `AGENTS.md`, then `docs/ARCHITECTURE.md`. That is the map. Do not crawl the tree to get
oriented; if the map is wrong, fixing the map is the first contribution.

## The unit of work

One feature is one file in `docs/features/`, numbered in creation order and never renumbered.
Pick one whose status is `next`, or write a new one in the same shape and open it as a pull
request before building it. A spec ends with acceptance checks that are commands with
expected output, not adjectives.

## Check by hand

```bash
…    # the command that proves the repo still works
```

There is no CI. Run it before opening a pull request and paste the output in the description.
A pull request that says "tests pass" without the output is not finished.

## What a change must respect

Local by default: no telemetry, no analytics, no fonts or scripts from a CDN, no request the
spec did not name. Flat files: markdown for what a person writes, JSON for what a program
writes. The tool never decides for the person: nothing ranks, scores or recommends. No new
dependency without a dated entry in `docs/DECISIONS.md` saying why.

## Style

Plain declarative prose in docs, no emoji. Code matches its neighbours. Commit subjects say
what changed and why it mattered, in one line.

## Reporting

Bugs and ideas are issues on the repository. Anything about data leaving the machine is
`SECURITY.md`.
