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

### Clone & sync source
```bash
mkdir -p ~/OrangeFox_14
cd ~/OrangeFox_14
git clone https://gitlab.com/OrangeFox/sync.git
cd sync
# Modify the script to natively fetch the R12 codebase
sed -i 's/git clone $URL -b $FOX_BRANCH "$dest";/git clone $URL -b fox_14.1-R12-new "$dest";/g' orangefox_sync.sh
./orangefox_sync.sh --branch 14.1 --path ~/fox_14.1
```

### Clone device tree
```bash
cd ~/fox_14.1/device
mkdir -p oneplus
cd oneplus
git clone https://github.com/NullCode1337/android_device_orangefox_ktm ktm
```
### BUILD
```bash
cd ~/fox_14.1
source build/envsetup.sh
lunch twrp_ktm-eng
mka recoveryimage -j$(nproc --all)
```
