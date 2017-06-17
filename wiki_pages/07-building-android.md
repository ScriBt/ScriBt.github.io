---
permalink: wiki/building-android.html
title: Building Android
---

* **Jack** was introduced as a **Toolchain** from Marshmallow onwards for **Apps and Frameworks**.
    - Uses a Java VM for compilation of Java Source Code '.java' to '.dex' (**D**alvik **Ex**ecutable) files
    - Recommended for Systems with >8GB RAM.
    - Systems with 4GB RAM can use it too, but it may cause lag during compilation, so using Swap is recommended for such users.

* **Ninja** was introduced from Android Nougat (7.x.x) as an alternative **Build System**.
    - No compatibility requirements.
    - Some features of it are quicker incremental builds, and showing progress of the build on compilation

* Companions for Ninja, which were also introduced in Nougat are...
    - [Kati](https://android.googlesource.com/platform/build/kati/#kati)  
      This is a tool which helps in generation of a .ninja file, in BluePrint Language, which guides through the build process...
    - [Soong](https://android.googlesource.com/platform/build/soong#Soong)
    - [BluePrint](https://android.googlesource.com/platform/build/blueprint/#Blueprint-Build-System)  
    A Language, possible successor of the Makefile Language

So, the ways of building Android are...

* Using **Normal** Build System
    - **with** Jack Toolchain (Marshmallow onwards)
    - **without** Jack Toolchain (Till Nougat)
* Using **Ninja** Build System
    - **with** Jack Toolchain (Nougat onwards)
    - **without** Jack Toolchain (Nougat onwards) - _Reported Non-Working by Developers_

## Setting up Android BuildSystem Environment

There are 3 ways (commands) of Setting up the Build Environment  

`lunch` - Sets the Device Target which is specified by the user  
`breakfast` - Syncs the Device Dependencies + `lunch`  
`brunch` - `breakfast` + Starts the Build  

Device Dependencies are synced by looking for a file named [rom_name].dependencies which specifies the same. It's written in JSON.  
`brunch` starts the build immediately after Setting the Environment  

Usage of each of them  

`lunch rom_device-buildtype`  

`breakfast device buildtype`  

`brunch device`  

`rom` - ROM's codename in source  
`device` - Device's Codename  
`buildtype` - Either of these values -> `user`, `eng`, `userdebug`  

Explanation of Values of `buildtype` is done [HERE](http://source.android.com/source/building.html#choose-a-target)  

Build Type | Use
----------:|:----
user       | limited access; suited for production
userdebug  | like "user" but with root access and debuggability; preferred for debugging
eng        | development configuration with additional debugging tools  

Where `userdebug` is the preferably used for a Public Custom ROM Release. Debugging Tools in this Build are enough for normal debugging.
`eng` is only used for debugging non-working things, and not to be publicly released.
