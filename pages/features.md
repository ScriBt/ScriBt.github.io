---
layout: wiki
title: "Features"
---

# What do the colors mean ?

![Colors](https://cloud.githubusercontent.com/assets/14874906/22984750/60463530-f3cc-11e6-9178-c543db2f999a.png)  

This method of coloring is **Relevant_Coloring** and is inspired from [a scene in Person of Interest](https://goo.gl/photos/s8YpQL1eBxSYwCWS7) and ADB Logs on a phone (Log types like E for Error, F for Fatal etc.)

# Command Explanations

ScriBt explains any relevant command possible to the user in a easily understandable representation.

Each command is explained, parameter by parameter

**Preview:**

![cmdprex](https://cloud.githubusercontent.com/assets/14874906/25778882/e1828b44-3328-11e7-9ae8-38acf71cfa2b.png)

This feature fulfils the aspect _"Easy and Understandable"_ :smile:  

# Automation Notes

Users can add their own commands in the default sequence ( I do it )

For Automating ScriBt

1. Create a config file of any name, in .rc format (eg. aosp_huashan.rc)

Enter this code in that file

`AUTOMATOR="true_dat";`

ScriBt can detect it's AutoConfig file by this line  
Now, fill the Information with reference to this File  

[variable_list.rc](https://github.com/ScriBt/ScriBt-examples/blob/master/variable_list.rc)  

Everything you think would be used by ScriBt should be filled.

**There's an example Automation Config to make things simple**

[lineage_huashan.rc](https://github.com/ScriBt/ScriBt-Examples/blob/master/lineage_huashan.rc)

_Want some more ? Head over to [ScriBt-Examples](https://github.com/ScriBt/ScriBt-Examples) repo for more Automation Configs_

2. Enter this on Terminal to Start with Automation

```
bash ./ROM.sh automate
```

ScriBt would display the available automation config files, select the one you want to execute, It'd do it for you. It's pretty much similar to a lunch menu on Android

![Automation menu](https://cloud.githubusercontent.com/assets/14874906/21285113/9e940f2a-c455-11e6-99ab-f33bfd3094d3.png)  

##### Functions that can be automated

* sync
* pre_build **^**
* build
* the_cherries

**^** - The Device Tree must be Compatible with the ROM you're building (Extra Toolchain Configs, Overlays etc. **ROMNIS-fying is taken care of in Point 3b** ) Else, Issues :) :P

# ScriBtofy

This feature (available under 'tools') allows ScriBt to be executed under any directory by adding it's working directory under PATH  

![ScriBtofy](https://cloud.githubusercontent.com/assets/14874906/22964656/bbc012d4-f37f-11e6-9813-599d2c29dbb8.png)

What it does ?  
1. Creates a file '.scribt' under ${HOME} directory  
2. Adds this code: ```export PATH=/wherever/is/ScriBt:$PATH```  
3. Adds code to execute '.scribt' under .bashrc:  
```# ScriBtofy```  
```. ~/.scribt;```  
Done!  

You can do this procedure as many times as you want, just in case if you've Shifted ScriBt somewhere else.  

ScriBt can be executed normally (after ScriBtofication) ```bash ROM.sh```

However, if you want to test another version of ScriBt (which is not in PATH) , then execute this command under that particular directory  

```bash ./ROM.sh```

This command executes ROM.sh which is present at the current directory instead of the one in PATH.  
This command also applies if you want to sync the source to the same location where ScriBt has been cloned.   
ScriBt gives preference to local ROM.rc to be executed (instead of the ROM.rc in PATH), if it is PRESENT.

# Updates

ScriBt is updated on the basis of the HEAD's SHA ID  
HEAD is the latest commit (SHA ID) of any Repository's commit list  
If the HEAD of Local Clone and HEAD of Remote Clone is different, then ScriBt notifies the user to update itself.  

```upScriBt``` does the Updating work.  

**ROM.sh** force-downloads upScriBt.sh from 'master' branch.
**upScriBt.sh then checks updates** on the basis of the above Procedure

**Based on Git Tag/Releases System - for messages to appear on ScriBt as well as in Github**

upScriBt works only for `master` branch. If Branch name is different, then it won't update.

# Automated Cherry-Picking

The title says everything. In Automated Mode, this function picks the commits which are mentioned in the Config.
Information needed by this function are...

`URL` -> Link of the GitHub repo in which you want to pick a commit.

URL should be in the format `https://github.com/[user_org]/[repo_name]/tree/[branch_name]`  
To get this format, open the repository, and choose the branch you want, It'd reload with the specified format, use it.

**Example** : https://github.com/a7r3/ScriBt/tree/master

`DIR` -> Directory under which the commit has to be picked

`CID` -> The SHA ID of the commit. It should be either Forty or Seven Character String

In a config file, to cherrypick a commit, enter these lines

```
DIR="foo";
URL="bar";
CID="lol";
cherrypick "$DIR" "$URL" "$CID"
```

# Patch Manager

**Every ROM compilation aren't bound to be Successful** :rofl:. Changes in the
source occur time to time, and eventually are merged as commits to the respective Repository.

ScriBt removes the hassle of "**What changes did I make for Previous Successful build ? :thinking:**"
by the Patch Manager Feature

![Patch Manager](https://cloud.githubusercontent.com/assets/14874906/23702774/b76963c6-0422-11e7-817e-7e38318bda0e.png)

## How does it work ?

* After making the changes in the source, as well as getting a Successfully compiled build, the
user can make use of this feature to generate a *Combined Patch file* which consists of all the changes the
user has made.  

> Patch is generated by the `git diff` command

* One thing to note is that this Patch can be re-applied by ScriBt, by Using the Patch Manager  

* Patch Destination can be under user-desired directory, with a user-desired name for the patch
make sure the directory exists.

* If the user wants to make use of the Patch in ScriBt's Patch Manager, he/she has to place the
Patch File inside these directories inside Working Directory.

`device/[VENDOR]/[CODENAME]/patch`  

OR  

`patch`  

### Indications shown by Patch Manager

![Indications](https://cloud.githubusercontent.com/assets/14874906/25778985/387a676c-332b-11e7-9fe4-5c26b2550ccc.png)

### Notes

* The patch files would be detected **ONLY** if it is present inside above specified directories
* The repositories which are synced with `repo` are considered as "Search for Changes" directories for Patch Creator. This means that Patches are not generated for repositories which were not synced by `repo` (`git clone`, `ZIP Download` sources are not considered).
