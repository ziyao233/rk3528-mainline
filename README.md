# Mainline Status of Rockchip RK3528 SoC

- Yao Zi (@ziyao233)
- Jonas Karlman (@kwiboo)
- @aiamadeus

are currently working on upstream support for RK3528 SoC.

## Linux Kernel

### Components that may involve driver changes

- clock and reset (CRU): Yao Zi, merged [v3](https://lore.kernel.org/all/20250217061142.38480-5-ziyao@disroot.org/)
  on 2025.02.27, should land in v6.15.
  - NOTE: reset driver isn't included in the series.
- reset driver: Jonas Karlman, merged [v1](https://lore.kernel.org/all/20250227175302.2950788-1-jonas@kwiboo.se/)
  on 2025.02.28, should land in v6.15
- gpio and pinctrl: Jonas Karlman, partially merged [v1](https://lore.kernel.org/all/20250228064024.3200000-1-jonas@kwiboo.se/)
  on 2025.03.04, should land in v6.15
  - LED/buttons/regulators DTS changes are merged into the LED/button series
    ("rockchip: Add support for leds and buttons on Radxa E20C")
- saradc: Jonas Karlman, partially merged [v1](https://lore.kernel.org/all/20250227184058.2964204-1-jonas@kwiboo.se/)
  - driver changes have been merged into IIO tree, should land in v6.15
  - DTS changes are merged into LED/button series
    ("rockchip: Add support for leds and buttons on Radxa E20C")
- SDHCI: Jonas Karlman, merged [v1](https://lore.kernel.org/all/20250305214108.1327208-1-jonas@kwiboo.se/)
  on 2025.03.12, should land in v6.15
  - HS400 mode: N/A
- SD/SDIO: Yao Zi, under review [v5](https://lore.kernel.org/all/20250506092206.46143-1-ziyao@disroot.org/)
  on 2025.05.06
- internal gmac: Jonas Karlman
  - depends on a clean up series, under review [v2](https://lore.kernel.org/all/20250308213720.2517944-1-jonas@kwiboo.se/)
    on 2025.03.08
  - driver changes, under review [v2](http://lore.kernel.org/20250309232622.1498084-1-jonas@kwiboo.se)
    on 2025.03.09
  - DTS changes, under review [v2](https://lore.kernel.org/all/20250310001254.1516138-1-jonas@kwiboo.se/)
    on 2025.03.10
- USB 2.0: Jonas Karlman, in progress
- OTP: Jonas Karlman, in progress
- TSADC: Jonas Karlman, in progress
- Hantro 1080P decoder: Jonas Karlman, in progress
- GPU: Jonas Karlman, in progress
- VOP: Jonas Karlman, in progress
- PCIe combined phy: Yao Zi, in progress
- Power Domain: Yao Zi, in progress
- PCIe controller: Yao Zi, in progress

### Componenets that require dt(-binding) changes only

- basic devicetree: Yao Zi, merged [v4](https://lore.kernel.org/all/20240829092705.6241-2-ziyao@disroot.org/),
  on 2024.10.12, should land in v6.13
- QoS (Quality of Service) syscons: @aiamadeus, merged [v2](https://lore.kernel.org/all/20250306123809.273655-1-amadeus@jmu.edu.cn/)
  on 2025.03.08, should land in v6.15
- LED/Buttons: Jonas Karlman, merged, [v2](https://lore.kernel.org/all/20250304201642.831218-1-jonas@kwiboo.se/)
  on 2025.03.08, should land in v6.15
- pwm: @aiamadeus
  - reverted [v1](https://lore.kernel.org/all/20250307120004.959980-1-amadeus@jmu.edu.cn/)
    had been merged on 2025.03.12
  - merged [v3](https://lore.kernel.org/all/20250401120020.976343-1-amadeus@jmu.edu.cn/)
    on 2025.05.06, should land in 6.16
- i2c: Yao Zi, merged [v2](https://lore.kernel.org/all/20250417120118.17610-3-ziyao@disroot.org/)
  on 2025.05.05, should land in v6.16
- sfc: Yao Zi, in progress
- spi: N/A
- watchdog: N/A
- rng: N/A

## U-Boot

- Jonas Karlman, merged [v2](https://lore.kernel.org/all/20250407224743.2423921-1-jonas@kwiboo.se/)
  on 2025.04.23, should land in v2025.07
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

- Radxa Rock 2A
  - 1/2/4 GiB RAM
  - Optional EMMC
  - One GbE port
  - 3 x USB 2.0
  - PCIe 2.0 x 1 lane
  - USB 3.0
  - With HDMI and Audio (!!!)
  - Optional WiFi/BT module
  - [Wiki Page](https://docs.radxa.com/en/rock2/rock2a)
  - [Schematic](https://dl.radxa.com/rock2/2a/v1.2/radxa_rock_2a_v1.2_schematic.pdf)
  - Note: PCIe 2.0 and USB 3.0 share the same PHY thus the USB port can only
    operate in 2.0 mode when PCIe is enabled.

- Radxa Rock 2F
  - 1/2/4 GiB RAM
  - Optional EMMC
  - HDMI and Audio (!!!)
  - 2 USB 2.0 Type-A Host ports
  - 1 USB 2.0 Type-C Host/OTG port
  - PCIe 2.0 x 1 lane
  - Optional WiFi/BT module
  - No Ethernet port
  - [Wiki Page](https://docs.radxa.com/en/rock2/rock2f)
  - [Schematic](https://dl.radxa.com/rock2/2f/radxa_rock2f_v1.01_schematic.pdf)

## Resources

- [Rockchip Linux tree](https://github.com/rockchip-linux/kernel)
- [Rockchip BL binaries (rkbin)](https://github.com/rockchip-linux/rkbin/)
- `rk3528/`-prefixed branches in
  [my kernel tree](https://github.com/ziyao233/linux)
- `rk3528`-suffixed branches in
  [Jonas Karlman's kernel tree](https://github.com/Kwiboo/linux-rockchip/)
