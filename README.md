# Notes
Please do keep in mind this EFI is heavily bloated, there's some useless stuffs present. "If it ain't broke, don't fix it" mentality going on here.

# Issues
For any issues, please open an issue or check if there's a solution already available in the issues section. Issues with solutions will be under closed issues. 

# macOS on ThinkPad X1C2
This repository is made to help run macOS on a ThinkPad X1C2.

This should help you get started on hackintoshing and any updates can be applied later. I may occasionally update this repo if I find the time but there's no guarantee.

I recommend going through the [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/) once to fully understand everything that is going on here.

Keep in mind that you have to generate your own serial numbers and ID's and stuff using [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) if you're doing a fresh install. Use your old ones from your old config.plist if you're just changing EFI's (TIP: Use MacBookPro11,4 but I've included that in the plist)

This hakcintosh will be complete only with [YogaSMC](https://github.com/zhen-zen/YogaSMC). After installing, please use the app and the system preferences add on as it enables some features for this to be complete.

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

![Screen Shot 2023-08-08 at 10 15 33 AM](https://github.com/Krissh-C/X1C2-macOS/assets/117280851/84479f72-5d85-4293-97bf-294dce649721)

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
- GPU Acceleration
- Camera
- Microphone
- Sleep/Wake
- Trackpad with gestures
- CPU Power Management
- Handoff, Continuity
- AirPlay
- DRM Content (more info below)
- FileVault (Once configured. Check [FileVault | Opencore](https://dortania.github.io/OpenCore-Post-Install/universal/security/filevault.html)) (may release new version soon)
- Fan Control using [YogaSMC](https://github.com/zhen-zen/YogaSMC)

# What doesn't work/Broken Stuff
**Please check the issues tab for more info/workarounds.**
- **MAJOR ISSUE:** Adaptive row does not work
- AirDrop
- DRM on Safari, Apple TV, Quicktime, etc
- Universal Control, SideCar (This is a SMBIOS limitation. Using [OCLP](https://dortania.github.io/OpenCore-Legacy-Patcher/) to get to Ventura should fix this. [FeatureUnlock](https://github.com/acidanthera/FeatureUnlock) does make the options available, but they do not work.)

# Not Tested
- USBMap may not include all ports (One Link connector, Mini DP and Mini Ethernet may not work as I have never tested them, please remap if you wish to use these ports)

# Credits
- [Acidanthera](https://github.com/acidanthera)
- [Opencore install guide](https://dortania.github.io/OpenCore-Install-Guide/)
- [Opencore post-install guide](https://dortania.github.io/OpenCore-Post-Install/)
- [CorpNewt](https://github.com/corpnewt)
- [YogaSMC](https://github.com/zhen-zen/YogaSMC)
- The lovely folks over on the [r/hackintosh subreddit](https://www.reddit.com/r/hackintosh/)
