# Mainline Status of Rockchip RK3528 SoC

- Yao Zi (@ziyao233)
- Jonas Karlman (@kwiboo)

are currently working on upstream support for RK3528 SoC.

## Linux Kernel

### Components that may involve driver changes

- clock and reset (CRU): Yao Zi, merged [v3](https://lore.kernel.org/all/20250217061142.38480-5-ziyao@disroot.org/)
  on 2025.02.27, should land in v6.15.
  NOTE: reset driver isn't included in the series.
- reset driver: Jonas Karlman, merged [v1](https://lore.kernel.org/all/20250227175302.2950788-1-jonas@kwiboo.se/)
  on 2025.02.28, should land in v6.15
- gpio and pinctrl: Jonas Karlman, under review [v1](https://lore.kernel.org/all/20250228064024.3200000-1-jonas@kwiboo.se/)
  on 2025.02.28
- SD/SDIO: Yao Zi, under review [v1](https://lore.kernel.org/all/20250301104250.36295-1-ziyao@disroot.org/)
- SDHCI: Jonas Karlman, in progress
- internal gmac: N/A
- combined USB/PCIe phy: N/A
- PCIe

### Componenets that require dt(-binding) changes only

- basic devicetree: Yao Zi, merged [v4](https://lore.kernel.org/all/20240829092705.6241-2-ziyao@disroot.org/),
  should land in v6.13
- i2c: Yao Zi, in progress
- saradc: Jonas Karlman, under review [v1](https://lore.kernel.org/all/20250227184058.2964204-1-jonas@kwiboo.se/)
  on 2025.02.28
- spi: N/A
- pwm: N/A
- watchdog: N/A
- sfc: N/A
- rng: N/A
- thermal sensor: N/A

## U-Boot

- Jonas Karlman, under review [v1](https://lore.kernel.org/u-boot/20250123224844.3104592-1-jonas@kwiboo.se/)
  on 2025.01.23
  - clk
  - pinctrl
  - rng
  - SD-card
  - eMMC
  - generic board and Radxa E20C, tested on ArmSoM Sige1, Radxa E20C and Radxa
    Rock 2A

## Boards

- Radxa E20C
  - 1-4GiB RAM
  - optional EMMC.
  - Dual GbE ports. One is provided by onboard RTL8111H, which occupies the
    only PCIe 2.0 lane.
  - Onboard serial to usb converter.
  - No HDMI, no audio, it's designed as a headless (networking) device.
  - [Official Documentation](https://docs.radxa.com/en/e/e20c)
  - Single USB 2.0 port.
  - Mainline devicetree, I'm primarily working on it.
  - [Wiki page](https://docs.radxa.com/en/e/e20c)
  - [Schematic](https://dl.radxa.com/e/e20c/v1.10/radxa_e20c_v1100_schematic.pdf)

- FriendlyElec NanoPi Zero 2
  - 1-4GiB RAM
  - Optional EMMC
  - Single GbE port through integrated GMAC and external RTL8211F phy.
  - No HDMI, no audio.
  - M.2 Key PCIe port.
  - Single USB 2.0 port.
  - Will submit a devicetree when more peripherals are available.
  - [Wiki page](https://wiki.friendlyelec.com/wiki/index.php/NanoPi_Zero2)
  - [Schematic](https://wiki.friendlyelec.com/wiki/images/3/37/NanoPi_Zero2_2407_SCH.pdf)

- ArmSOM Sige1
  - 4GiB RAM
  - 32GiB eMMC
  - One 2.5GbE port and one GbE port
  - With HDMI and Audio (!!!)
  - [Wiki page](https://docs.armsom.org/armsom-sige1)
  - [Schematic](https://drive.google.com/drive/folders/15uvc2lcOAKP0enXezASUhVFLuzkq3IEX)

## Resources

- [Rockchip Linux tree](https://github.com/rockchip-linux/kernel)
- [Rockchip BL binaries (rkbin)](https://github.com/rockchip-linux/rkbin/)
- `rk3528/`-prefixed branches on
  [my kernel tree](https://github.com/ziyao233/linux)
