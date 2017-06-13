---
layout: wiki
title: "Pre-Build"
---

Making the Device Sources ready for the ROM to be built.

This is the Biggest Part of ScriBt. It _adds the Device to ROM Vendor_ as well as _make the Device tree usable for the ROM_. Doing this makes the Device Sources completely ready for getting the ROM built.

This is the part where I feel ScriBt helps the user. Actions of Pre-Build are entirely based on Observations of Working of ROM Vendors, each and every ROM supported by ScriBt.

Making an **Interactive Makefile** under the Device Tree (Identifiable by ROMs BuildSystem)

  * This was created in order to prevent unnecessary modifications to the files present in the Device Tree which may mess some Configurations.

  * Idea came into existence, When I saw most of the ROMs having these lines in one of the BuildSystem's files...

  ```# A ROMNIS build needs only the ROMNIS product makefiles.```

  ```ifneq ($(ROMNIS_BUILD),)```
     ```all_product_configs := $(shell ls device/*/$(ROMNIS_BUILD)/ROMNIS.mk)```

### Device Types

Device Type is asked when mentioning Device Details on Pre-Build. Choosing Device type builds Device-Specific Modules and things. Best Example of this is the Bootanimation Variants (...based on Resolution)

* ```full``` - This indicates that the Device has **Adequate Storage Space** for building Entire Android System for it
* ```mini``` - This indicates that the Device has **Low Storage Space**, so only Android Essentials are built ( Fewer Apps and Stuff )

* **common_full_phone, common_mini_phone** - An Android SmartPhone
* **common_full_tablet, common_mini_tablet, common_tablet** - An Android Tablet
* **common_full_tablet_lte** - A Tablet with LTE (4G) Functionality
* **common_full_tablet_wifionly** - A Tablet with Wi-Fi functionality
* **common_full_tv, common_mini_tv** - Android TV
* **common_full_hybrid_wifionly** - Android Device with any Size ( Phone / Tablet ) ( used if Device Type is unknown )

* NOTE : IF you're building for a Phone and common_full_phone / common_mini_phone isn't in the list, then press Enter (Leave Blank) as the ROM will consider the Device as a Phone.

