# Disclaimer

Hi everyone, 

I created this repo for my latest Hackintosh ITX build based on the AsRock Z490 Phantom Gaming ITX/TB3.

The config is built based on https://dortania.github.io/OpenCore-Install-Guide/ and https://github.com/SchmockLord/Hackintosh-Intel-i9-10900k-AsRock-Z490-Phantom-ITX-TB3

Because my spec is different from the original spec so I changed a lot of things.

Please consider my config or the original config for your build.

**Current Bootloader**: OpenCore

# Hardware
- Intel i5-10600k
- AsRock Z490 Phantom Gaming ITX/TB3:
    - Audio: Realtek ALC1220-VB
    - Ethernet: Realtek RTL8125B-CG
    - 1x USB-C, there is no USB-C Header for an additional Front USBC
    - 1x Thunderbolt 3 ports
- RAM: VENGEANCE® LPX 16GB (2 x 8GB) DDR4 DRAM 3200MHz C16 Memory Kit - Black
- IGPU (working): Intel® UHD Graphics 630
- DGPU (not working, disabled via boot-args): ASUS GeForce RTX 3070 KO-RTX3070-O8G-GAMING 8GB
- Wifi/BT (not working, replaced with BCM94360NG): Intel AX201
- Case: MasterBox NR200P | Cooler Master

# Some notes:

1. For installation

* Remove the power cable of the DGPU before installing
* Update BIOS to enable IGPU multi-monitor and use iGPU as primary display
* Use `install` branch to install because I removed some unnecessary kexts and ACPI

2. For kexts I use

```
EFI/OC/Kexts
├── AppleALC.kext
├── Lilu.kext
├── LucyRTL8125Ethernet.kext
├── SMCProcessor.kext
├── SMCSuperIO.kext
├── USBInjectAll.kext
├── USBWakeFixup.kext
├── VirtualSMC.kext
└── WhateverGreen.kext
```

- AppleALC for audio
- Lilu, WhateverGreen for graphic fix
- VirtualSMC, SMCSuperIO, SMCProcessor for processer
- USBInjectAll, USBWakeFixup for USB port
- LucyRTL8125Ethernet for LAN internet

3. For ACPI I use

```
EFI/OC/ACPI
├── SSDT-AWAC.aml
├── SSDT-EC-USBX.aml
├── SSDT-PLUG.aml
├── SSDT-SBUS-MCHC.aml
├── SSDT-TB3HP.aml
├── SSDT-UIAC-ASROCK-Z490-ITX-TB3.aml
└── SSDT-USBW.aml
```

- Fixes AWAC system clock
- Improves SMBus Support
- USB-port configuration
- Enables Thunderbolt 3 Hot Plug
- For the USBWakeFixup.kext to fix the issue, that it takes two keystrikes to wakeup the display, if you wakeup your PC with the keyboard.


# Working

- **MacOS**: Big Sur
- **Wifi and Bluetooth** (via BCM94360NG Wireless Card).
- **Audio**: Realtek ALC1220-VB
- **Ethernet: Realtek RTL8125B-CG** (requires LucyRTL8125Ethernet.kext)
- **Handoff**: test with my iphone and ipad
- **Unlock**: with Apple Watch
- **SideCar**: test with my ipad pro 11 inch 2020
- **DRM**: AppleTV, Amazon Prime Video and Netflix in Safari and other browsers
- **Sleep/Wake**
- **Shutdown**
- **Restart**

# Haven't test

- **USB** (I didnt have time to check every ports)
- **Thunderbolt 3**

# Not working
