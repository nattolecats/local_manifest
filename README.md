# local_manifests
Manifest for Pixel 6a on my unofficial Evolution X build.

### Sync ###

```bash
# Initialize local repository
repo init -u https://github.com/Evolution-X/manifest -b tiramisu

# Clone my custom manifest
git clone -b tiramisu https://github.com/nattolecats/local_manifests_bluejay .repo/local_manifests

# Sync
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

```

### Build ###

```bash

# Set up environment
. build/envsetup.sh

# Choose a target
lunch evolution_bluejay-userdebug

# Build the code
m evolution
```

If you got something went wrong, try replace this repos below:

```bash

# Go to root of your source
croot

# Avoid hardware source code error
rm -rf hardware/google/pixel && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_pixel hardware/google/pixel
rm -rf hardware/google/gchips && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_gchips hardware/google/gchips
rm -rf hardware/google/graphics/common && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_graphics_common hardware/google/graphics/common

# Avoid neuralnetworks bug
rm -rf external/armnn && git clone -b topaz https://github.com/AOSPA/android_external_armnn external/armnn
rm -rf external/android-nn-driver && git clone -b topaz https://github.com/AOSPA/android_external_android-nn-driver external/android-nn-driver

```
