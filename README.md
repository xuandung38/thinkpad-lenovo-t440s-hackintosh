# MacOS ThinkPad T440/T440s

MacOS Mojave,Catalina,BigSur beta 9  on ThinkPad T440/T440s

## Pre-Installation

### 1. Warning: check you BIOS version

**You should update(downgrade) BIOS to v2.36 or MOD BIOS to remove Wireless Whitelist if you want use Another Wifi card!**

### 2. BIOS settings

| Item | Setting |
| ------------- | ------------ |
| Security Chip | Disabled |
| Memory Protection Execution Prevention | Enabled |
| Virtualization | Enabled |
| Fingerprint Reader | Disabled |
| Secure Boot | Disabled |
| UEFI/Legacy Boot | UEFI Only |
| CSM Support | YES |
| Boot Mode | Quick |


### 3. Specs

| Specifications      | Detail                                      |
| ------------------- | ------------------------------------------- |
| Processor           | Intel Core i5-4300U                         |
| Memory              | Samsung DDR3L 8GB Bus 1600MHz               |
| Hard Disk           | Samsung SSD P851                            |
| Integrated Graphics | Intel HD Graphics 4400                      |
| Monitor             | FHD IPS 1920x1080                           |
| Sound Card          | Realtek ALC292                              |
| Wireless            | Intel Dual Band Wireless-AC 7260 (Replace to BCM94360CS2   |

### 4. Current Status

#### What will work

- Intel HD 4400 Graphics QE/CI
- USB Ports
- Intel Ethernet
- Audio (All Inputs & Outputs with combojack)
- Sleep and Wake
- Mini DisplayPort and Mini DisplayPort Audio
- CPU and IGPU Power Management
- Battery Status
- Brightness
- Function Keys (Fn)
- ClickPad and TrackPad
- Integrated Camera
- Wireless (Intel) work with itlwm (enable in config)

#### Not working

- Fingerprint Reader
- VGA ()

### 5. Wireless

Inbuilt Intel Wi-Fi now can work with [OpenIntelWireless](https://github.com/OpenIntelWireless).

But I still suggestions using the apple wifi card (with adapter) for smoother operation.

I sell wifi card so please contact me if you need (only ship in Vietnam)

## Installation

### 1. BootLoader
- OpenCore 0.6.2

### 2. Kexts used

- [AppleALC.kext](https://github.com/acidanthera/AppleALC)
- [CodecCommander.kext](https://github.com/Sniki/EAPD-Codec-Commander)
- [IntelMausi.kext](https://github.com/acidanthera/IntelMausi)
- [Lilu.kext](https://github.com/acidanthera/Lilu)
- [Sinetek-rtsx.kext](https://github.com/cholonam/Sinetek-rtsx)
- SMCBatteryManager.kext
- SMCLightSensor.kext
- SMCProcessor.kext
- USBPorts.kext
- [VirtualSMC.kext](https://github.com/acidanthera/VirtualSMC)
- [VoodooPS2Controller.kext](https://github.com/acidanthera/VoodooPS2) (use latest version)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen)

### 3. Tool

- Hackintool
- ALCPluginFix to fix issue combojack
- [ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant/releases) to use full function key.
- GenSMBIOS to generate new System Info

## Post Install
- 
- Download [ALCPluginFix](https://github.com/Sniki/ALCPlugFix)
- Extracted *ALCPlugFix* folder into Desktop.
- Open *Terminal* and enter the following commands 1by1:

```
    sudo spctl --master-disable
    sudo mkdir /usr/local/bin/
    cd desktop/ALCPlugFix
    ./install.sh
```

- Added *-rtsx_mimic-linux* <b>boot-arg</b> to fix SD Card Detection and initialization after wake from sleep.

- Add MAC address of Builtin Ethernet to Config.plist > PlatformInfo > Generic > ROM.

- Replace platform info (use genSMBIOS) Model MacBookPro11,1

## Known Issues:

- Docking Station Audio Jack has no input support, only output because we can't use two inputs as LineIn.
- SD Card Reader after wake from sleep can't eject normally, you have to Force Eject.
- Kernel Panic into an Instant Reboot when attempting sleep, restart or Shutdown while External Display connected on one of the Docking Station Video Ports (DisplayPort, DVI, VGA)
- No DisplayPort Audio when using the Docking Station DisplayPort

## Thanks to

- @MSzturc
- @Sniki
- @acidanthera and OpenCore Team
- All
