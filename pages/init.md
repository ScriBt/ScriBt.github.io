---
layout: wiki
title: "Init | Custom Manifests"
---

This is the First step to start off with.

This Action Initializes the ROM's manifest, which consists of a list of Repositories to be Synced.

**Referencing another ROM Source while syncing another**  

This is a great Bandwidth/Disk Space Saver option provided by `repo`. If you have a ROM Source already synced (.repo folder should be present), then Referencing that ROM's Source location would check for Sources which are already Synced in that Source, and skips syncing those repositories, thus saving both Time and Bandwidth required to download it.

# Custom Manifests :

Custom Manifests (popularly called `local manifests`) act as an Addition to the Repositories mentioned in the ROM's manifest. Users can Add their Device Specific Repositories (and some manifest operations) so that it gets Synced with the ROM's repositories. It is written in XML.

These manifests should be made under .repo/local_manifests folder. Name of the manifest can be user-desired, default is local_manifest.xml

## Can ScriBt do it for me ?

Yes. **Manifest Generator** can generate a custom manifest with the desired actions such as Adding/Removing a repository, Adding a remote, Replacing a repository etc.

![manifest_gen](https://cloud.githubusercontent.com/assets/14874906/26673200/a9c49ab6-46d9-11e7-9a8d-95e066182838.png)  

Nothing of a guide is required to run this module. If you want to know how a manifest works, then there's a guide below this topic to understand it.  

User is asked whether to generate a custom manifest after Initializing a ROM's manifest. Alternatively, one can access **Manifest Generator** by heading on to **Tools -> Generate Custom Manifest**  

**One has to note that Manifest Generator can be used ONLY if a ROM repo is initialized**  

##  Basic Syntax of a Manifest (XML)

```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
...  
Statements  
...
</manifest>
```

**Explanations**

L1 -> Specification of a typical XML file, with `XML version` as `1.0` with Character Encoding as `UTF-8`  
L2 -> `manifest` start tag  
..  
Statements  
..  
L3 -> `manifest` end tag  

## Operations that can be performed with a Custom Manifest

### 1. Adding a Remote

A Remote is any Repository Hosting Website/System. Some of the popular Hosting Systems are...

* GitHub
* GitLab
* BitBucket
And many more...

**GitHub** is the most-used Repository hosting service used by ROM Developers, but you can use the other two too.

To add a Remote, you need to enter this code in the Custom Manifest

```
<remote  name="name_of_your_choice"
         fetch="https://website_url.com" />
```

It can also be used for Creating **Aliases** from Several Repos. For example, to add the CM Repository as a remote...

```
<remote  name="cm"
         fetch="https://github.com/LineageOS"
         revision="cm-14.1" />
```

Where **revision** is the default branch of a Repository in this Organization to be synced if no revision tag is mentioned for projects.

`<project name="android_apps_packages_Snap" remote="cm" revision="cm-14.1" />`

Here, the Remote is 'cm' whose Fetch URL is https://github.com/LineageOS. `repo` searches for this name under this Fetch tag.

This line can interpreted as...

Sync the project which is located at `https://github.com/LineageOS/android_packages_apps_Snap` and whose revision/branch is `cm-14.1` to the path `packages/apps/Snap`

### 2. Adding a Repository

You can add a Repository in this Format...

For eg. https://github.com/LineageOS/android_device_google_marlin (Google Pixel Device Tree) can be added in this way

`<project name="LineageOS/android_device_google_marlin" path="device/google/marlin" remote="github" revision="cm-14.1" />`

#### Tag's Parameters Explained

**No parameters should contain spaces in it.**

`name` -> Name of the Repository

`path` -> Path to which this repository is to be synced

`revision` -> Branch of the Repository

`remote` -> Remote acts an alias to a GitHub Organization / any Repository Hosting Service

### 3. Removing a Repository

A Project can be removed by Specifying its repository name in this format

Ex. https://github.com/LineageOS/android_packages_apps_Trebuchet is present in the ROM Manifest as...

`<project path="packages/apps/Trebuchet" name="LineageOS/android_packages_apps_Trebuchet" />`

It can be removed by specifying its `name` in your Custom Manifest, by this way

`<remove-project name="LineageOS/android_packages_apps_Trebuchet" />`

This Action cancels the syncing of this Project and Removes the checked out Output on Completion of Sync.

### 4. Replacing a Repository

Suppose you don't want a particular repository to be Synced from the ROM's manifest, instead, you want to sync it from another Location/Organization, then you can do this.

> Add a **remove-project** tag to remove the repository from the Main manifest

> Add a **project** tag to add the repository as a replacement

This order has to be followed, because XMLs are interpreted in an up->down manner

If you don't remove the project (or swap the order stated above), and only add the project which syncs to the same path, then 'repo' would throw this error...

`fatal: duplicate path path/to/project in /a_home/a_user/a_folder/.repo/manifest.xml`

Which means that there are more than one projects which are getting synced to the SAME path, you have to remove either of them.

_Both projects are the same if their Checkout Path is the SAME._
