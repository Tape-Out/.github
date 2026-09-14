---
name: Bug report
about: An IP or the tooling does something its specification or documentation says it should not.
title: '[Bug] '
labels: bug
assignees: ''
---

<!-- Fill every section unless it says optional. English or Chinese are both fine. -->

### Where

- **Repository and commit**:
- **Configuration**: <!-- the knobs, e.g. `-s smode=true -s mmu=true`, or the matrix point name that `ran test` prints -->
- **Tool versions**: <!-- output of `bsc -v`, and the xirang commit -->

### Steps to reproduce

<!-- The smallest command that shows it, usually `ran test <package> --point <point>`. -->

1.
2.

### What you expected

<!-- If a specification says so, quote the sentence and give its section. -->

### What happened

<!-- The first FAIL line, the G-code bsc printed, or the log lines around the failure. -->

### Checklist

- [ ] Reproduced on the latest commit of the default branch.
- [ ] Searched the existing issues.
