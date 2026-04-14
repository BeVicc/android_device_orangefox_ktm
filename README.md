# Ace 6 (PLQ110) Android device tree

## Status

- [X] Display
- [X] MTP/OTG Storage
- [X] ADB/Fastbootd
- [X] Vibrator
- [X] Display Settings
- [X] Flashing 
- [X] Backup & Restore 
- [X] Factory Reset
- [X] Touch
- [X] Decryption

# Building (OrangeFox R12)

### Setup build environment
```bash
mkdir -p ~/OrangeFox_14
cd ~/OrangeFox_14

# Sync TWRP base and patch for OrangeFox
repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-14
repo sync -c --no-clone-bundle --no-tags --optimized-fetch --prune --force-sync -j$(nproc --all)
git clone https://gitlab.com/OrangeFox/sync.git sync_scripts/sync
cd build/make && patch -p1 < ../../sync_scripts/sync/patches/patch-manifest-fox_14.1.diff && cd ../../

# Download latest OrangeFox R12 Code
git clone https://gitlab.com/OrangeFox/vendor/recovery.git -b fox_14.1-R12-new vendor/recovery
```

### Clone device tree
```bash
cd ~/OrangeFox_14/device
mkdir -p oneplus
cd oneplus
git clone https://github.com/NullCode1337/android_device_orangefox_ktm ktm
```
### BUILD
```bash
cd ~/OrangeFox_14
source build/envsetup.sh
lunch twrp_ktm-eng
mka recoveryimage -j$(nproc --all)
```
