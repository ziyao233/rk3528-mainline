# Mainline Status of Rockchip RK3528 SoC

I'm currently working on upstream support for RK3528 SoC.

## Linux Kernel

### Components that may involve driver changes

- clock and reset driver (CRU): Accepted [v3](https://lore.kernel.org/all/20250217061142.38480-5-ziyao@disroot.org/)
  2025.02.27, should land in v6.15
- gpio and pinctrl: N/A
- mmc: N/A
- internal gmac: N/A
- combined USB/PCIe phy: N/A

### Componenets that require dt(-binding) changes only

- basic devicetree: merged [v4](https://lore.kernel.org/all/20240829092705.6241-2-ziyao@disroot.org/), should land in v6.13
- i2c
- spi
- pwm
- watchdog
- sfc
- rng

## Boards

- Radxa E20C
  - 1-4GiB RAM
  - optional EMMC.
  - Dual GbE ports. One is provided by onboard RTL8111H, which occupies the
    only PCIe 2.0 lane.
  - Onboard serial to usb converter.
  - No HDMI, no audio, it's designed as a headless (networking) device.
  - [Official Documentation](https://docs.radxa.com/en/e/e20c)
  - Mainline devicetree, I'm primarily working on it.

## U-Boot

Planned, but I'm busy :/

Please let me know if you're willing to take the work.

## Resources

- [Rockchip Linux tree](https://github.com/rockchip-linux/kernel)
- [Rockchip BL binaries (rkbin)](https://github.com/rockchip-linux/rkbin/)
- `rk3528/`-prefixed branches on
  [my kernel tree](https://github.com/ziyao233/linux)
