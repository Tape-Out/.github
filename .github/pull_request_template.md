<!-- Keep both sections. One line is enough where one does not apply. -->

### Change

<!-- What changed and why. For a conformance fix, the clause it follows. -->

### Verification

<!-- The commands and their result, e.g. `ran lint <package>` and `ran test <package>`. For a fix, the check that failed before it. -->

### Checklist

- [ ] Every commit is signed off and signed (`git commit -s -S`).
- [ ] `ran lint` and `ran test` pass for every package this touches.
- [ ] If `bsv/`, `ip.yaml` or `regmap.yaml` changed, the price list was measured again with `ran recal <package> --apply`, or the description says who will measure it.
- [ ] No credentials, local paths or vendor PDK files are committed.
