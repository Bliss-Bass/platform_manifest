<img src="https://i.ibb.co/61Tk8Wy/Bliss-New-Beginning-hide.png">
<p align="center">
<a href="https://https://blissos.org">Website</a> |
<a href="https://sourceforge.net/projects/blissos-dev">Download</a> |
<a href="https://www.paypal.com/donate/?hosted_button_id=J5SLZ7MQNCT24">Donate</a> |
<a href="https://docs.blissos.org/">Documentation</a> |
<a href="https://t.me/blissx86">Telegram</a>

## Bliss Bass

Download the source code for (android-x86|Bliss-Bass|Bliss OS|Bliss OS Go|Bliss ROM), based on [AOSP](https://android.googlesource.com) / [Android-x86](http://android-x86.org/) / [Bliss ROM](http://blissroms.org/)

<div align="center">
<strong><i>Modified for PC build using Android-Generic Project v2023</i></strong>
<br>
<img src="https://i.ibb.co/rf2rv3M/Yep1l4L.png">
<br>
</div>

---------------------------------------------------

Please read the [AOSP building instructions](http://source.android.com/source/index.html) before proceeding.

-----------------------
## What you need to build [android-x86|Bliss-Bass|Bliss OS|Bliss OS Go|Bliss ROM](https://github.com/Bliss-Bass/platform_manifest)


    Latest Ubuntu LTS Releases https://www.ubuntu.com/download/server
    Decent CPU (Dual Core or better for a faster performance)
    8GB RAM (16GB for Virtual Machine)
    250GB Hard Drive (about 170GB for the Repo and then building space needed)
  
-----------------------

## Grabbing Dependencies

    sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386  lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip squashfs-tools python3-mako libssl-dev ninja-build lunzip syslinux syslinux-utils gettext genisoimage gettext bc xorriso xmlstarlet meson glslang-tools git-lfs libncurses5 libncurses5:i386 libelf-dev aapt

## Initializing Target Repository

**Target Repo nitialization**

##### android-x86 #####
   
    repo init -u https://github.com/Bliss-Bass/platform_manifest.git -b a12.1 -m android-x86.xml


##### Bliss-Bass #####
   
    repo init -u https://github.com/Bliss-Bass/platform_manifest.git -b a12.1 -m bliss-bass.xml


##### Bliss OS #####
   
    repo init -u https://github.com/Bliss-Bass/platform_manifest.git -b a12.1 -m bliss-os.xml


##### Bliss Os Go #####
   
    repo init -u https://github.com/Bliss-Bass/platform_manifest.git -b a12.1 -m bliss-os-go.xml


##### Bliss ROM #####
   
    repo init -u https://github.com/Bliss-Bass/platform_manifest.git -b a12.1 -m bliss-rom.xml


**Sync repo**

    repo sync -c --force-sync --no-tags --no-clone-bundle -j$(nproc --all) --optimized-fetch --prune

## Options

	BLISS_BUILD_VARIANT - (vanilla, gapps, foss) - We currently use this to specify what type of extra apps and services to include in the build. 
***Note: Default BLISS_BUILD_VARIANT is VANILLA.***

   BLISS_SPECIAL_VARIANT - This can be custom set if you wanna build a version for a specific device 
    for example `-jupiter` for Steam Deck or `-surface` for Microsoft Surface series

## Setup FOSS apps (if you choose to build FOSS)
----------------------------

- If you want to build with FOSS (this will include microG Services & some extra apps), go to vendor/foss and then type
```
    ./update.sh
```
And then choose 1 (x86/x86_64) to fetch all the apps. If you want to include Bromite Webview in, type this instead
```
    ./update.sh "" bromite
```

## Building (android-x86) (AG Patches needed)
```
    . build/envsetup.sh
    bash vendor/ag/ag-menu-new.sh
```
Apply the base patchset for "android-x86-base"
```
    lunch android_x86_64-userdebug
    make iso_img
```
## Building (Bliss Bass) (AG Patches needed)
```
    . build/envsetup.sh
    bash vendor/ag/ag-menu-new.sh
```
Apply the base patchset for "bliss-os-base"
```
    lunch bliss_x86_64-userdebug
    make iso_img
```
## Building (Bliss OS)
```
    . build/envsetup.sh
    lunch bliss_x86_64-userdebug 
    make iso_img
```
## Building (Bliss OS GO)
```
    . build/envsetup.sh
    export IS_GO_VERSION=true && lunch bliss_x86_64-userdebug 
    make iso_img
```
## Building (Bliss ROM)
```
    . build/envsetup.sh
    blissify options deviceCodename
```  
     
***Adding build options***

Before running `lunch`, you can add variables into the build to integrate more stuff into the image.
Note that you can put different variables into the build.

- **To build with FOSS**
```
    export BLISS_BUILD_VARIANT=foss && export USE_FOSSAPPS=true
```

- **To build with [MindTheGapps](https://gitlab.com/MindTheGapps/vendor_gapps)**
```
    export BLISS_BUILD_VARIANT=gapps
```

- **To build with SmartDock**
```
    export USE_SMARTDOCK=true
```

- **To add a custom label into a device-specific build**
```
    export BLISS_SPECIAL_VARIANT := jupiter
```

**More build options will be in Extras part including proprietary native-bridge/widevine libraries**

Extras
-------

We do offer some extra libraries that can be compiled into the build. These include :

***Prebuilt Widevine from Windows Subsystem for Android***

https://github.com/supremegamers/vendor_google_proprietary_widevine-prebuilt

Clone to `vendor/google/proprietary/widevine-prebuilt`, The variable to activate this is `USE_WIDEVINE=true`

***Windows Subsystem for Android's libhoudini*** 

https://github.com/supremegamers/vendor_intel_proprietary_houdini

Clone to `vendor/intel/proprietary/houdini`, The variable to activate this is `ANDROID_USE_INTEL_HOUDINI=true`
## Report build issues
- You can reach us via [Telegram (Android™-Generic (x86 PC) Community Development)](https://t.me/androidgenericpc)
