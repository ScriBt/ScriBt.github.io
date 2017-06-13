---
layout: wiki
title: "Syncing Sources"
---

Size of the Downloadable Source is around 20GB (Size of the .repo folder)

Size of the Source after Checking out would be around 35-40GB (Size of the Checked out source)

# Options available for `repo sync`

### Number of Threads

No. of threads to be used for Syncing sources. If you have a weak Internet Connection OR you want to take a look at the Output, set the Number of Jobs to 1, else set it according to your wish (No of threads <= No of CPU cores - Recommended)

### Silent Sync

If Enabled, Sync output won't be shown. But, file-checkout progress is shown irrespective of it.

### Sync current Branch

If Enabled, It syncs only the branch which is specified in the manifest. A Data/Bandwidth Saving Attempt.

### Clone Depth

If Depth Value is set, It'd Sync the Repository with a limited amount of Commit History (dependent on Depth Value). Another B/W saving attempt, but it is recommended not to use this flag if you don't know the effects.

### Force Syncing

If Enabled, Local Sources having changes would be overwritten by Remote, thus ensuring a cleaner attempt for Building the ROM.

If User doesn't specify one of these Prompts by ScriBt, the Default Responses are

No. Of Jobs           -> **1**

Silent Sync           -> **Disabled**

Sync Current Branch   -> **Enabled**

Force Sync            -> **Disabled**

Clone Depth           -> **not used**

**Sync can be resumed from one point.**
User can **cancel the Sync** by performing the command `killall python` in another TAB.

# Common Sync Errors

**WiP**
