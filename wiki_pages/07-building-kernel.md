---
permalink: wiki/building-kernel.html
title: Building Kernel
---

## Steps involved in building a Kernel include

### 0. Pointing ScriBt to the Kernel Source

**Enter the location of the Kernel Source from '/' (Root)** 
 
### 1. Setting up the Defconfig

Kernel Definition Config (defconfig) is a complete set of Kernel parameters which allow the Kernel's buildsystem to build the kernel with the specified parameters.  

ScriBt then searches for the Defconfig under the kernel source by prompting for the Device's codename. A defconfig has the following naming convention  

`[#]_[CODENAME]_[#]_defconfig`

Anything can be there in place of '[#]', but presence of Device's Codename [CODENAME] is mandatory.  
Ex. ```viskan_huashan_defconfig``` ```huashan_defconfig``` ```huashan_akernel_defconfig```  

Since a kernel can be with multiple CPU architectures for a device, ScriBt mentions the complete path of the DefConfig from the source tree, which also contains the CPU architecture. User can select any defconfig keeping in mind that they are selecting the correct Architecture too  

Ex.  
1. arch/**arm**/configs/board_device_defconfig  
2. arm/**arm64**/defconfigs/board_device_defconfig  

1 would select the defconfig with the CPU Architecture as **ARM**  
2 would select the defconfig with the CPU architecture as **ARM64**  

![Where am I ?](https://github.com/ScriBt/images/raw/master/KernelInit.png)  

## 2. Setting up the Toolchain

User is prompted to enter the path to the Kernel Toolchain. **User has to mention the location from '/'**. After entering the path, a check for finding the Toolchain binaries is performed, and the Toolchain prefix is shown after the check is successful.  

Collection of these prompts are required to setup the CROSS_COMPILE variable which points to the path of Kernel Toolchain  

`CROSS_COMPILE=[toolchain-path]/bin/[prefix]-`  

![TC](https://github.com/ScriBt/images/raw/master/KernelTCSetup.png)  

## 3. Cleaning the Kernel source  

There are two ways (based on their extent) of cleaning a Linux (or Android) Kernel source  

a. `clean`  

This option cleans the intermediate `object files (.o)` , `kernel modules (.ko)`, and other intermediates  

b. `mrproper`  

This option, in addition with performing `clean` also cleans the Kernel configuration file (`.config`), which is equivalent to a complete cleanup. Do note that the defconfig has to be set again since `.config` is deleted  

![Clean it](https://github.com/ScriBt/images/raw/master/KernelClean.png)  

## 4. Building the Kernel

Starts building the Kernel with the provided parameters.
