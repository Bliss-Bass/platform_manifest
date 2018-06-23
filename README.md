<img src="https://i.imgur.com/7V995n7.png">

Bliss-Bass for Treble
-----------------------
Download the Bliss-Bass for Treble source code, based on [phhusson](https://github.com/phhusson/treble_manifest), [skunkworx](https://github.com/skunkworkx/platform_manifest), & [BlissRoms](https://github.com/BlissRoms/platform_manifest)

---------------------------------------------------

Please read the [AOSP building instructions](http://source.android.com/source/index.html) before proceeding.

-----------------------
What you need to build [Bliss-Bass](ssh://git@git.floydco.net:Bliss-Bass/platform_manifest)
-----------------------

    Latest Ubuntu LTS Releases https://www.ubuntu.com/download/server
    Decent CPU (Dual Core or better for a faster performance)
    8GB RAM (16GB for Virtual Machine)
    250GB Hard Drive (about 170GB for the Repo and then building space needed)
  
-----------------------

Installing Java 8

    sudo add-apt-repository ppa:openjdk/ppa
    sudo apt-get update && upgrade
    sudo apt-get install openjdk-8-jdk
    update-alternatives --config java  (make sure Java 8 is selected)
    update-alternatives --config javac (make sure Java 8 is selected)
    reboot
    
-----------------------

Grabbing Dependencies
-----------------------

    $ sudo apt-get install git-core gnupg flex bison gperf build-essential zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386  lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache libgl1-mesa-dev libxml2-utils xsltproc unzip squashfs-tools python-mako libssl-dev ninja-build lunzip syslinux syslinux-utils gettext genisoimage gettext bc xorriso

Initializing Repository
-----------------------

Repo initialization :

    $ repo init -u https://github.com/Bliss-Bass/platform_manifest -b o8.1-tb

sync repo :

    $ repo sync --no-tags --no-clone-bundle
    
problems syncing? :

    $ repo sync --no-tags --no-clone-bundle --force-sync

Building
--------
treble build options explained:

    treble_arm64_afN-userdebug - ARM64, A-only with FDroid and no superuser
    treble_arm64_afS-userdebug - ARM64, A-only with FDroid rooted with phh-su
    treble_arm64_agN-userdebug - ARM64, A-only with OpenGapps and no superuser
    treble_arm64_agS-userdebug - ARM64, A-only with OpenGapps rooted with phh-su
    treble_arm64_avN-userdebug - ARM64, A-only with and no superuser
    treble_arm64_avS-userdebug - ARM64, A-only with rooted with phh-su
    treble_arm64_bfN-userdebug - ARM64, A/B with FDroid and no superuser
    treble_arm64_bfS-userdebug - ARM64, A/B with FDroid rooted with phh-su
    treble_arm64_bgN-userdebug - ARM64, A/B with OpenGapps and no superuser
    treble_arm64_bgS-userdebug - ARM64, A/B with OpenGapps rooted with phh-su
    treble_arm64_bvN-userdebug - ARM64, A/B vanilla with no superuser
    treble_arm64_bvS-userdebug - ARM64, A/B vanilla, and rooted with phh-su
    treble_arm_afN-userdebug - ARM, A-only with FDroid and no superuser
    treble_arm_afS-userdebug - ARM, A-only with FDroid rooted with phh-su
    treble_arm_agN-userdebug - ARM, A-only with OpenGapps and no superuser
    treble_arm_agS-userdebug - ARM, A-only with OpenGapps rooted with phh-su
    treble_arm_avN-userdebug - ARM, A-only with vanilla and no superuser
    treble_arm_avS-userdebug - ARM, A-only with vanilla, rooted with phh-su
    treble_arm_bfN-userdebug - ARM, A/B with FDroid and no superuser
    treble_arm_bfS-userdebug - ARM, A/B with FDroid rooted with phh-su
    treble_arm_bgN-userdebug - ARM, A/B with OpenGapps and no superuser
    treble_arm_bgS-userdebug - ARM, A/B with OpenGapps rooted with phh-su
    treble_arm_bvN-userdebug - ARM, A/B and vanilla no superuser
    treble_arm_bvS-userdebug - ARM, A/B and vanilla, rooted with phh-su

After the sync is finished

    $ bash build.sh (to build armA 64bit with su and gapps built in)

Or...

    $ . build/envsetup.sh
    $ lunch treble_arm64_agS-userdebug bliss (or any other treble device combo)
    $ mka systemimage
