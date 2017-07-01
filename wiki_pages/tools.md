---
permalink: wiki/tools.html
title: "Tools"
---

Tools. Setting up the Build Environment and making the System ready to build Android.  

![Tools](https://github.com/ScriBt/images/raw/master/Tools.png)

This function helps the user to make his/her System ready for building Android. Tools provided by ScriBt are...  

### Install Build Dependencies  

This action installs the required packages which are required by the Android Build-System to function properly. Specific to Distro's Year of Release.  

### Install Java  

#### a. Installation:

This action Installs Java 1.6/1.7/1.8. It is the User's choice on which version of Java to install based on the Android version of the ROM he/she desires to build  
Java 1.6 –> Kitkat
Java 1.7 –> Lollipop & Marshmallow
Java 1.8 –> Marshmallow (Experimental support) & Nougat

#### b. Switch between different Java Versions
In case you have multiple versions of Java Installed, you can switch between these versions by this Option. Doing this will chose the Default Version of Java which will be used by Android for building.

Just in case if the user couldn't Install Java because of it's unavailability, The Java Installation Menu has two other options which are...
Ubuntu 14.04~ and want to Install Java 8
Ubuntu 16.04~ and want to Install Java 7

[ ~ - Also applies for Distros based on these Releases such as Linux Mint ]
which installs Java from a recognized PPA – openjdk-r

<b>NOTICE</b>: openjdk-r hasn't been updated for Ubuntu 17.04 (Zesty Zapus) yet, so Installing Java 7 from ScriBt isn't possible at this moment

ScriBt installs Java by OpenJDK (not the Oracle JDK) which is used for building

### Install / Update ADB udev rules  

This action Installs / Updates the udev rules, which allows the detection of any Android Device by the ADB

### Set-Up CCache  

### Add/Update Git Credentials  

Create a GitHub account if you don't have one, Enter your Username and Email ID in their respective prompts to successfully configure Default Git Credentials.
This is asked when you start your First Ever Sync.

### Install _make_

make (or GNU make) is a binary which is used to build any module from it's Source on any Linux Distro.

This action installs the `make' binary in the system.

### Install _ninja_, _ccache_, _repo_ ^^

### Add ScriBt to PATH

This is more of a Feature (aka ScriBtofy), which is explained [here]({{ "/wiki/features.html" | relative_url }}#scribtofy)  

### Create a ScriBt Update [ScriBt-Devs ONLY]

An update creator for ScriBt, for us.

### Generate a Custom Manifest

[Featured "Manifest Generator", description about it is in here]({{ "/wiki/init.html" | relative_url }}#can-scribt-do-it-for-me-)
