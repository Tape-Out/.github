# .github

Organisation defaults: reusable CI workflows, issue templates and the contribution guide.

![maturity](https://img.shields.io/badge/maturity-planned-lightgrey) ![license](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0%20OR%20MulanPSL--2.0-blue)

Part of the [Tape-Out](https://github.com/Tape-Out) IP library: Bluespec IP over the
bus-neutral contracts in [`hwcore`](https://github.com/Tape-Out/hwcore), assembled by
[`xirang`](https://github.com/Tape-Out/xirang). Maturity runs `planned` -> `simulated` ->
`fpga-proven` -> `asic-ready` -> `silicon-proven`.

## What is here

| Path | What |
|:--:|:--:|
| [`.github/workflows`](.github/workflows) | `ip.yml`, the pipeline every repository calls; `asic.yml` and `resume.yml`, the backend of a tape-out design and its continuation past the six-hour limit |
| `.github/ISSUE_TEMPLATE`, `.github/pull_request_template.md` | the forms issues and pull requests start from |
| `.github/CODEOWNERS` | who reviews what |
| `profile` | the organisation's front page |

## License

任选其一：

- [MIT](LICENSE-MIT)
- [Apache 2.0](LICENSE-APACHE)
- [木兰宽松许可证 第2版](LICENSE-MULAN)

`SPDX-License-Identifier: MIT OR Apache-2.0 OR MulanPSL-2.0`

除非另行说明，你提交的贡献按上述三者同时授权，不附加其他条件。
