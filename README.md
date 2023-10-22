# Notes
Please do keep in mind this EFI is heavily bloated, there's some useless stuffs present. "If it ain't broke, don't fix it" mentality going on here.

# Issues
For any issues, please open an issue or check if there's a solution already available in the issues section. Issues with solutions will be under closed issues. 

# macOS on ThinkPad X1C2
This repository is made to help run macOS on a ThinkPad X1C2. **Now with OCLP!!**

This should help you get started on hackintoshing and any updates can be applied later. I may occasionally update this repo if I find the time but there's no guarantee.

I recommend going through the [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/) once to fully understand everything that is going on here.

If doing a fresh install, please use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) to generate a new SMBIOS (Use MacBookPro14,1)

This hakcintosh will be complete with the following apps:
- [YogaSMC](https://github.com/zhen-zen/YogaSMC) - Enables features such as fan control, Led control, etc. The Lenovo Vantage for macOS of sorts
- [Opencore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) - **REQUIRED FOR POST INSTALL**. This will help patch the GPU so you can have acceleration in macOS. Select Post install root patches, after installing.

**CAUTION**: Test drive this configuration once using a USB flash drive before you move it to the main EFI partition. I am not responsible for any damages incurred.

# Hardware Info

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

# Screenshots

![Screenshot 2023-10-22 at 11 06 14 AM](https://github.com/Krissh-C/X1C2-macOS/assets/117280851/b22f42dc-7ee9-4c70-9cbe-46919ca95e9d)

# What Works
- Keyboard
- Trackpad and TrackPoint
- Battery indicator
- USB ports
- Display Auto-Brightness
- Touchscreen (check closed issues for more info)
- HDMI
- Audio (Speakers, Headphone Jack and Bluetooth)
- Bluetooth
- Ethernet
- iCloud Services (iMessage, FaceTime, iCloud Drive)
- GPU Acceleration (Please check closed issues for more info)
- Camera
- Microphone
- Sleep/Wake
- Trackpad with gestures
- CPU Power Management
- AirPlay
- DRM Content (more info below)
- FileVault
- Fan Control

# What doesn't work/Broken Stuff
**Please check the issues tab for more info/workarounds.**
- **MAJOR ISSUE:** Adaptive row does not work after sleep (Fn mode also will not switch)
- Handoff and everything else that depends on Handoff 
- AirDrop
- DRM on Safari, Apple TV, Quicktime, etc
- Universal Control, SideCar (wireless)

# Credits
- [Acidanthera](https://github.com/acidanthera)
- [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [Opencore post-install guide](https://dortania.github.io/OpenCore-Post-Install/)
- [Opencore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher)
- [CorpNewt](https://github.com/corpnewt)
- [YogaSMC](https://github.com/zhen-zen/YogaSMC)
