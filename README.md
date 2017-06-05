# local_manifests

To build my specific LOS 13.0 version for the Osprey and SM-T815 device,
follow the steps below:

## Setup build tree
Create the directory, which should hold your build tree, 'cd' into it
and run the following commands:
```
repo init -u https://github.com/LineageOS/android.git -b cm-13.0
cd .repo
git clone https://github.com/MSe1969/local_manifests
cd local_manifests
git checkout cm-13.0
cd ../..
repo sync
```

## Prepare build / apply patches
cd into directory **z_patches** and execute the script ./patches_apply.sh

Create a build script in the root dir of your build tree, take the
sample scripts in directory z_patches as reference and adapt them according
to your needs.
