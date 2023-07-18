### Device specific configuration to build Automotive AOSP Android 13 with RSO 2 powered VHAL for Raspberry Pi 4.

***

### How to build:

1. Establish [Android build environment](https://source.android.com/setup/initializing) and install [repo](https://source.android.com/docs/setup/develop#installing-repo).

2. Install additional packages:

```
sudo apt-get install bc coreutils dosfstools e2fsprogs fdisk kpartx mtools ninja-build pkg-config python3-pip
sudo pip3 install meson mako jinja2 ply pyyaml dataclasses
```

3. Initialize repo:

```
repo init -u https://android.googlesource.com/platform/manifest -b android-13.0.0_r61 --depth=1
git clone https://github.com/SpyroSoft-Synergy/roscar_local_manifest.git .repo/local_manifests
```

4. Sync source code:

```
repo sync
```

5. Compile:

```
. build/envsetup.sh
lunch aosp_rpi4-userdebug
make bootimage systemimage vendorimage
```

6. Make flashable image:

```
./rpi4-mkimg.sh
```

Also look into [Linux kernel build instructions](https://github.com/raspberry-vanilla/android_kernel_manifest/tree/android-13.0).

***

### Issues:

- [roscar_local_manifest](https://github.com/SpyroSoft-Synergy/roscar_local_manifest/issues)

