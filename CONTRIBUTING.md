# Contributing to Tape-Out

Tape-Out is an open hardware IP library in Bluespec. Each IP lives in its own repository, describes itself in `ip.yaml` and `regmap.yaml` as defined in [`spec`](https://github.com/Tape-Out/xrspec), and is generated, tested and priced by [`xirang`](https://github.com/Tape-Out/xirang).

## Setting up

    git clone https://github.com/Tape-Out/xirang
    cd xirang && uv sync && uv run ran --help

You also need [bsc](https://github.com/B-Lang-org/bsc) on `PATH`. Clone the IP repositories you work on side by side in one directory and run `ran` from there; `ran -p <dir>` adds another place to look for packages.

## Before you open a pull request

    ran lint <package>
    ran test <package>

`ran test` goes over every point of the package's configuration matrix: the schedule gate, the register map consistency check and the package's own behaviour tests. The default configuration passing says nothing about the others.

If you changed `hwsrc/`, `ip.yaml` or `regmap.yaml`, the price list no longer matches the design and `ran lint` says so. Measuring it again needs the ICS55 PDK, which public runners do not have. If you do not have it either, say so in the pull request.

## How IP is written here

- **BSV or BH by the nature of the block.** Rules, state and scheduling are written in BSV. Pure combinational tables, folds over vectors, type-level work and pattern matching are written in BH. Both live in `hwsrc/`.
- **Write the check first and watch it fail where you expect.** A check that passes on its first run proves nothing until a mutation of the design makes it fail.
- **Every rejection needs a check that only it can catch.** Two conditions that reject the same case hide each other: removing one changes nothing.
- **Unknown keys are errors.** Nothing in a manifest is silently ignored.
- **A conformance fix quotes the standard**: the section, the page and the sentence.

## Commits

Sign off and sign every commit (`git commit -s -S`). Titles follow `type(scope): summary.`, for example `fix(eswitch): forward a learned unicast only to an enabled port.`

## Licences

Tools, contracts and buses are Apache-2.0; IP implementations are Mulan PSL v2. Code under GPL or AGPL cannot be brought in, translated into Bluespec or otherwise; read it for ideas only.
