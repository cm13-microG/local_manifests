# local_manifests

To build my specific LOS 13.0 version for the Osprey and SM-T815 device,
follow the steps below:

## Setup build tree
Create the directory, which should hold your build tree, 'cd' into it
and run the following commands:
```Shell session
repo init -u https://github.com/LineageOS/android.git -b cm-13.0 --groups=all,-notdefault,-darwin,-x86,-mips
cd .repo
git clone https://github.com/cm13-microG/local_manifests
cd local_manifests
git checkout cm-13.0
cd ../..
repo sync --no-tags
```
Note: If you build on a MAC, omit the `-darwin` in above `repo init` statement.

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
5. Synchonize further repositories due to 'cm-13.0-microG' branch (no impact on 'cm-13.0' branch)
6. **z_patches** directory contains 'microG patch' (applied, if patch script is executed)
