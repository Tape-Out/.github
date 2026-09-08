# workflows

`ip.yml` is the organisation-wide pipeline every IP repository calls. A repository's own
CI is six lines:

```yaml
name: ci
on: [push, pull_request]
jobs:
  ip:
    uses: Tape-Out/.github/.github/workflows/ip.yml@main
```

Gates run cheapest first: manifest and lock, then generation, then the bsc type check,
then the schedule check. Only a change under `bsv/`, `ip.yaml` or `regmap.yaml` triggers
synthesis, because the price list is a fixed term plus a slope and only moves when the
logic does.

The schedule gate is the one worth knowing about. It fails on G0004, G0021, G0006 and
G0035, which are the scheduling conflicts and lifted implicit conditions that otherwise
only show up as a simulation that hangs.

Areas are written by the bot to an `area` branch, unsigned. Every commit on a main
branch in this organisation is signed by a person; the bot never touches one. A human
reviews what landed on `area` and moves the numbers across.
