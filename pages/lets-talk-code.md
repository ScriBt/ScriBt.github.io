---
layout: wiki
title: "Let's talk \"Code\""
---

## Advice : Developers ONLY!

**WikiPage which describes each file in the source tree.**  

**ROM.sh** is the heart of ScriBt.  

`ScriBt="ROM.sh";`

Files in **src/** are **Not Code** - but are Informational Modules, which are required by ScriBt to execute any module.  

`ROM_NAME` is the full name of a ROM, which is shown to the user.  

`ROMNIS` - **ROM** **N**ame **I**n **S**ource - eg. `cm`, `lineage`, `aosp`, `full`, etc.

## `src` - Directory Structure  
  
### distro/[distro_codename].rc

* Folder containing `*.rc` files for each Supported distro, named after the **ID** of each distro.  
  - `ID` as in the file `/etc/os-release`
* Contains Package-List assignments according to its **Year of Release**  

### info/*.rc

* `rc` files containing echo statements, which act as explanatory statements to certain prompts  

### misc/banner.rc

* Contains the ScriBt startup banner

![Banner](https://cloud.githubusercontent.com/assets/14874906/25773497/ea75ad0e-329b-11e7-92fb-e373d11fdd4b.png)  

Yeah, this one.  

### misc/device_types.rc

* Consists of an array TYPES which contains various Device-Types  
  - What are [Device Types](https://github.com/ScriBt/ScriBt/wiki/Pre-Build#device-types)  

### misc/intmake.rc

* Contains the Content of the Apache2 License, which is included in Device-ROM Target makefiles  

### pkgs/Dxy.rc

* Folder containing `*.rc` files which contain Package Lists according to the **Year of Release**  
  - `xy` denotes the Last two digits of **Release Year**  
  - Required for Ubuntu/Debian based GNU/Linux distributions

* Arch Linux packages list is present in [archcommon.rc](https://github.com/404/)

### roms/caf/[ROM_NAME].rc

* Consists of Information on a ROM's Source in GitHub (or any code-hosting website)
* ROM present in here should be buildable for CAF (Qualcomm) devices, as well as for Pixel/Nexus Devices    
* Information required by a ROM  
  - ROM's GitHub Organization/User name (eg. LineageOS)
  - Name of ROM's manifest repo (eg. android.git)
  - ROM's codename (lineage)
  - If the ROM source contains both CAF as well as Non-CAF (Pure AOSP) sources, AND if their CAF branches contain the word 'caf' in it (DirtyUnicorns/NitrogenOS for instance), then a variable 'CNS' is required to be set to 'y' in this way  
  `CNS="y";`  

### roms/aosp/[ROM_NAME].rc

* Same information as above, except for a change in Point 2  
  - The ROM is buildable only for Pixel/Nexus Devices  

### utils/[binary_file]

* Contains certain binaries which are required by the Tools Installer  
  - [Tools](https://github.com/ScriBt/ScriBt/wiki/Tools)  

### strat/[ROMNIS].rc

* Contains strategies to add a Device to a ROM vendor  
* Files are named after ROM's codename
* Non-CAF (AOSP) based ROMs - containing **vendor/[ROM_NAME]/products** folder require these strats  

### upScriBt.sh

* A script which updates **ScriBt** to the latest version  
* Provides changelog from **local tag** to the **latest tag**  
* Inspired from JustArchi's updater-code for the [ArchiKitchen Project](https://github.com/JustArchi/ArchiKitchen)
* Initially developed by me, re-written later by [Tim Schumacher](https://github.com/TimSchumi)  

### dist_db.rc

* Script to detect a distro and assign a package list according to its **Version** as well as its **Year Of Release**  

### color_my_life.rc

* Script to provide colors to ScriBt  

### usage.rc

* Script which talks about the [Usage of ScriBt](https://github.com/ScriBt/ScriBt/wiki/Usage)  
