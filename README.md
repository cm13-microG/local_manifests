# local_manifests

To build my specific LOS 13.0 'microG & sec.enhanced' version for the 
Osprey and SM-T815 device, follow the steps below:

## Setup build tree
Create the directory, which should hold your build tree, 'cd' into it
and run the following commands:
```Shell session
repo init -u https://github.com/LineageOS/android.git -b cm-13.0
cd .repo
git clone https://github.com/MSe1969/local_manifests
cd local_manifests
git checkout cm-13.0-microG
cd ../..
repo sync
```

## Prepare build / apply patches
cd into directory **z_patches** and execute the script `./patches_apply.sh`

Create a build script in the root dir of your build tree, take the
sample scripts in directory z_patches as reference and adapt them according
to your needs.

## Differences to 'vanilla' LineageOS 13.0
1. Removed below packages from the build:
   - **CMUpdater** (obsolete, as cm-13.0 does not receive any updates any longer)
   - **AOSP Browser** and **Gello** (obsolete, outdated and insecure)
2. Included LineageOS **Jelly** browser (prebuilt)
3. Include most current **CA-Certificates** from AOSP master branch
4. Osprey-device only: Use **Squid Kernel** (oreo branch)
5. Take AOSP System Webview and other Chromium components from 'cm-14.1' branch
6. 'microG build' having the following features:
   - Prebuilt 'microG' apps included
   - Enhanced SELinux policies (restrict /proc timers and /proc/net)
   - Additional AppOps (Sensor, Storage) in Privacy Guard
   - SQLite Secure delete feature
