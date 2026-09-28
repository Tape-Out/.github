# Tape-Out

An open hardware IP library in Bluespec, assembled by the XiRang package manager.

Every IP is a repository of the same shape: an `ip.yaml` that names its knobs, contracts and measured area, a `regmap.yaml` for its registers, Bluespec sources, and behaviour tests that run over its whole configuration matrix. [`xirang`](https://github.com/Tape-Out/xirang) resolves, generates, tests and prices them, and [`xrspec`](https://github.com/Tape-Out/xrspec) says what the files mean.

| Layer | Repositories |
|:--:|:--|
| Tools and specifications | `xirang` · `xrspec` · `xrskel` · `index` · `pdk` · `.github` |
| Contracts and buses | `hwcore` · `amba` · `tilelink` · `wishbone` · `bridge` |
| Processors and accelerators | `rvcore` · `lacore` · `xxcore` · `aacore` · `cache` · `yolo` · `npu` |
| Upstream cores, as black boxes | `picorv32` · `serv` · `ibex` · `cv32e40p` · `cva6` · `ao486` · `ne16` · `open-la500` · `vortex` · `verigpu` · `miaow` · `xiangshan` |
| Interrupts, timers and system | `aclint` · `plic` · `imsic` · `rcu` · `pinmux` · `mbox` · `dma` · `pmu` |
| Peripherals | `uart` · `spi` · `i2c` · `gpio` · `timer` · `wdt` · `rtc` · `pwm` · `sram` · `rom` and more |
| Networking | `emac` · `eswitch` · `erouter` |
| Reference SoCs | `soc-mcu` (no MMU) · `soc-mpu` (MMU) · `soc-smp` · `soc-amp` · `soc-noc` · `soc-switch`, none with RTL of its own |

Maturity runs `planned` → `simulated` → `fpga-proven` → `asic-ready` → `silicon-proven`, and every repository shows its level as a badge. See [CONTRIBUTING](https://github.com/Tape-Out/.github/blob/main/CONTRIBUTING.md) to take part.
