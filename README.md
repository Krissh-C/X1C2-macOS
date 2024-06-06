<div align="center">
             <img src="images/AppIcon.png" alt="X1C2 macOS Logo" width="256" />
             <h1>macOS on X1 Carbon Gen 2</h1>
</div>

A project using [Acidanthera's OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) and [Dortania's Opencore-Legacy-Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher).

My main goal with this is get unsupported macOS versions and features up and running on this hackintosh after hardware support has been lost using OCLP

----------

### Notable features of this EFI:
* Compatible with macOS Sonoma
* Working WiFi + Bluetooth
* Working Touchscreen (if available)
* GPU Acceleration (Only with OCLP)
* iCloud Services
* YogaSMC support for features like CPU fan control, performance bias, most <kbd>Fn</kbd> Key shortcuts working, additional OSD overlays, etc.

----------

### Issues:
* macOS will not display properly at native 1440p resolution
* Adaptive row will not wake up after system has been woken up from sleep
* USB ports will sometimes complain of high power usage

----------

### Future Goals:
* Fix adaptive row issue
* Fix native 1440p screen glitching issue
* Add better GPU framebuffer patch
* Improve CPU power management for better performance and battery life

----------

> [!CAUTION]
> 
> Upgrading from to macOS 14.3.1 to 14.4 or up via `System Update` causes a Kernel Panic during install! Disable `AiportItlwm` and enable `itlwm` instead. Set `SecureBootModel` to `Disabled`, Reset NVRAM and run the update again. If this does not work, follow this [workaround](https://github.com/5T33Z0/OC-Little-Translated/blob/main/W_Workarounds/macOS14.4.md) (Thanks to [5T33Z0](https://github.com/5T33Z0) for this) to install macOS 14.4 on a new APFS volume. Use Migration Manager afterwards to get your data onto the new volume!

----------

### Hardware Info:

|**Component**|**Model**|
|:-|:-|
|**CPU**|Intel Core i7-4550u|
|**GPU**|Intel HD Graphics 5000|
|**RAM**|8GB 1600 MHz DDR3|
|**Storage**|256GB Samsung MZNTE256HMHP-000L7|
|**WiFi/Bluetooth**|Intel Wireless N-7260|
|**Touchpad**|Synaptics|
|**Display**| 14" 2560x1440 Touch|
|**Camera**| 720p HD|
|**Battery**| Single 45 Wh|

----------

## Get Started!

> [!Important]
>
> If you haven't already, I recommend going through the [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/) once to fully understand everything that is going on here and to help with troubleshooting incase of any problems

### Prerequisites:
* Any plist editor (Highly recommend [Propertree](https://github.com/corpnewt/ProperTree))
* [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate SMBIOS information (Use `MacBookPro15,2` **only** as the USB map will not work with other SMBIOSes)
* [OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) for access to it's utilities, specifically `macrecovery` to download an online macOS installer if needed
* [Opencore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) as it is **required** for enabling GPU acceleration right after installation
* [YogaSMC](https://github.com/zhen-zen/YogaSMC)
* [MountEFI](https://github.com/corpnewt/MountEFI)
* A compatible storage medium

### Instructions:
* Download the [latest](https://github.com/Krissh-C/X1C2-macOS/releases/latest) version of the EFI
* Extract it and place the EFI folder in the root of your USB drive
* Open `config.plist` using a plist editor
* Generate SMBIOS information using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) and paste it into the config.plist
* **Optional:**
  * Edit `boot-args` to your liking.
    * Add `-v`, `debug=0x100` and `keepsyms=1` to help with debugging incase of any issues
  * Tweak your `config.plist` to your liking. Most users will not need to do this
* Save your `config.plist`
* Navigate to the Opencore folder and go to `Utilities/macrecovery`
* Open a terminal in this folder and download the latest release of Sonoma. (Refer [here](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/) on how to do so)
* Place the `com.apple.recovery.boot` folder in the root of your USB after downloading
* **Optional:**
  * Place `MountEFI`, `Propertree`, `YogaSMC`, `Heliport` and `OpenCore-Patcher` in a separate folder on the USB. This will help save time later on
* Reboot to the BIOS and follow below

### BIOS Configuration
Tested on BIOS version `GRET63WW (1.40)` and EC version `GRHT39WW (1.20)`
Change settings so your BIOS looks like this:
|**Category**|**Setting**|
|:-|:-|
**Config** | **Network** <ul> <li> Wake On LAN: `Disabled` </ul> </li> **USB** <ul> <li> USB UEFI BIOS Support: `Enabled` </li> </ul> **CPU** <ul> <li> Intel (R) Hyper-Threading Technology: `Enabled` </li> </ul>
**Security** | **Security Chip** <ul><li>Security Chip: `Disabled` </ul> **Memory Protection** <ul> <li> Execution Prevention: `Enabled`</ul></ul> **Virtualization** <ul><li> Intel (R) Virtualization Technology: `Enabled` <li> Intel (R) VT-d Feature: `Enabled` </ul> **Anti-Theft** <ul><li> Intel AT Module Activation: `Disabled` <li> Computrace Module Activation: `Disabled` </ul> **Secure Boot** <ul><li> Secure Boot: `Disabled` </ul>
**Startup** | **UEFI/Legacy Boot:** `UEFI Only` <ul> <li> **CSM Support:** `Yes` </li> </ul> Boot Mode: `Quick`

> [!CAUTION]
>
> Test drive your configuration once using a USB flash drive before you move it to the main EFI partition. I am not responsible for a broken OS/loss of data, etc...

> [!Important]
>
> If you have a 1440p display and upon booting into the macOS or the installer you have a garbled screen, add `-igfxvesa` to `boot-args` in your `config.plist`. It is required to remove it later on and switch to a lower resolution if you want graphics acceleration. Do note that macOS Sonoma and up will boot automatically with no acceleration and so it's not required to add this boot argument

### Post Installation
Congratulations you've successfully booted your hackintosh! Here's some things to do before moving forward:
> [!Important]
>
> Remove the `-igfxvesa` boot argument from your `config.plist` if added. It will be hard to see but navigate to System Settings and turn down the resolution to anything below 1440p

* **Graphics Acceleration:**
  * Open [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher/releases/latest)
  * Allow all the necessary permissions and click on Post-install root patches
  * It should automatically bring up a patch for graphics
  * Install and reboot and you should have graphics acceleration

* **YogaSMC:**
  * Open the YogaSMC `.dmg` file and install the `.prefpane` and move the app to your applications folder
  * Open YogaSMC and in the menu bar, click on `Start at Login`
  * Open System Settings and navigate to YogaSMC settings and you're done!

* **Booting without USB:**
  * Open [MountEFI](https://github.com/corpnewt/MountEFI)
  * Mount the macOS EFI partition
  * Copy your EFI folder from the USB to the EFI partition now available
  * Reboot your machine without the USB plugged in

* **Heliport:**
  * This is only if you are using the `itlwm` kext
  * Open [Heliport](https://github.com/OpenIntelWireless/HeliPort/releases) and install it
  * You should now be able to connect to WiFi

* **Additional:**
  * Open System Settings and navigate to Battery
  * Scroll down to `Options...` and do the following:
    * Enable Power Nap: `Never`
    * Put hard disks to sleep when possible: `Never`
    * Wake for network access: `Off`
  * Run the follwing, one line at a time:
    
      ```
      sudo pmset autopoweroff 0
      sudo pmset powernap 0
      sudo pmset standby 0
      sudo pmset proximitywake 0
      sudo pmset tcpkeepalive 0
      ```
      
* **Beauty Treatment (Optional):**
  * In `config.plist`
      * Remove `-v` from `boot-args` to turn off Verbose Mode
      * Turn off the picker
      * Change the scan policy to `2687747` to hide all NTFS drives from Opencore
      * Turn on Auto login
      
----------

### Screenshots:

<div align="center">
             <img src="images/AboutX1C2-14.5.png" alt="About this mac screen open on macOS desktop" />
             <h5>14.5 running on X1C2</h5>
</div>

----------

### What Works:
* Keyboard
* Trackpad and TrackPoint
* Battery indicator
* USB ports
* Display Auto-Brightness
* Touchscreen
* HDMI
* Audio (Speakers, Headphone Jack and Bluetooth)
* Bluetooth
* Ethernet
* iCloud Services
* GPU Acceleration (with OCLP)
* Camera
* Microphone
* Sleep/Wake
* Trackpad with gestures
* CPU Power Management
* AirPlay
* DRM Content
* FileVault (Disabled for OCLP patches)
* Fan Control

### What doesn't work:
**Please check the issues tab for more info/workarounds**
* Adaptive row does not wake up after sleep and <kbd>Fn</kbd> mode will not switch (SMC Issue maybe)
* AirDrop, iMessage, Universal Control, Wireless Sidecar (Wifi Kext Limitation)
* DRM on Safari, Apple TV, Quicktime, etc (Use Chromium based broswer/Firefox)

### Not tested:
* iPhone widgets (Part of Handoff)

----------

### Credits:
* [Acidanthera](https://github.com/acidanthera)
* [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/)
* [Opencore post-install guide](https://dortania.github.io/OpenCore-Post-Install/)
* [Opencore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher)
* [CorpNewt](https://github.com/corpnewt)
* [YogaSMC](https://github.com/zhen-zen/YogaSMC)
* [The community](https://www.reddit.com/r/hackintosh/)
