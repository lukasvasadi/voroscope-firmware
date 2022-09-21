# Voroscope Marlin Firmware

Firmware for the Voroscope microscopy gantry system. Mechanical design based on the Voron V0 3D printer build. Firmware based on the Marlin configuration for the Creality Ender 3 Pro with a BTT SKR Mini E3 V2.0 motherboard (STM32F103RCT6).

## Design choices

The Voron V0 uses Klipper to compute the motion sequences for 3D printing. While Klipper offers some more advanced features over Marlin, which computes geometric motion on the microcontroller board directly, it puts more overhead on the Raspberry Pi controller. For the Voroscope microscopy platform, the Raspberry Pi acts as a central node connecting the SKR motherboard, Raspberry Pi HQ camera, and host computer with the control software, transacting data between the three asynchronously. Because of these high demands, we wanted to offload the computational heavylifting to prevent unnecessary throttling. In addition, due to the nature of the system, most, if not all, of the motion sequences should be simple linear movements between xy positions.

## Versioning

This firmware is a slightly modified version of the [Marlin 2.1.1 release](https://github.com/MarlinFirmware/Marlin/releases/tag/2.1.1) with matching [configurations](https://github.com/MarlinFirmware/Configurations) for the Creality Ender 3 Pro.

## Board flashing

Before flashing the BTT SKR MiniE3 V2.0 motherboard, with the STM32F103RCT6 MCU, download VS Code and install the [Auto Build Marlin](https://marlinfw.org/docs/basics/auto_build_marlin.html) extension. Open the firmware directory in the text editor and select "build" (hammer icon) in the Auto Build Marlin extension sidebar. Within the architecture list, select the build option for STM32F103RC_btt_USB_maple (256K). When the build completes, open the binary directory (folder icon underneath the architecture selection) and copy the firmware.bin file onto the mini SD card. Make sure that the board is powered down before inserting the SD card into the slot reader.
