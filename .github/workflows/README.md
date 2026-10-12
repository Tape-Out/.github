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
then the schedule check. Only a change under `hwsrc/`, `ip.yaml` or `regmap.yaml` triggers
synthesis, because the price list is a fixed term plus a slope and only moves when the
logic does.

The schedule gate is the one worth knowing about. It fails on G0004, G0021, G0006 and
G0035, which are the scheduling conflicts and lifted implicit conditions that otherwise
only show up as a simulation that hangs.

Areas are written by the bot to an `area` branch, unsigned. Every commit on a main
branch in this organisation is signed by a person; the bot never touches one. A human
reviews what landed on `area` and moves the numbers across.

`asic.yml` runs the backend of a tape-out design from RTL to layout with the same `ran asic`
used on a workstation, and keeps the outputs as an artifact. It takes hours, so a repository
calls it from a workflow that is only started by hand:

```yaml
name: asic
on: workflow_dispatch
jobs:
  asic:
    uses: Tape-Out/.github/.github/workflows/asic.yml@main
```

ECC, the synthesis tools and the ICS55 PDK come from the installer ECOS publishes; the `ecc`
input selects its version.

A hosted runner gives a job six hours. `resume.yml` picks up a backend run that hit that
limit: it takes the run's artifact and continues from the step that was not finished, or
from the step named in `from`.

A test that does not fit one job runs as a relay in `ip.yml`: `keep` leaves a directory of
the repository as an artifact, `restore` brings it back in a later job of the same run,
`stage` and `from` name the legs, and `tasks` runs the listed tasks instead of the matrix.
`to2610-soc` boots Linux on its netlist this way.

`dep-refs`, in both `ip.yml` and `asic.yml`, takes dependencies from a branch instead of
their default one, as `repo=branch` pairs. It is for a run started by hand: a chip is
tested against a change in a dependency before that change is merged. Every job prints
the commit it took of each dependency.

```yaml
on:
  workflow_dispatch:
    inputs:
      dep_refs:
        default: ''
jobs:
  ip:
    uses: Tape-Out/.github/.github/workflows/ip.yml@main
    with:
      dep-refs: ${{ inputs.dep_refs }}
```
