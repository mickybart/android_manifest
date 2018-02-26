# nAOSP 7.1.2 for Sony Xperia S and Acro S

near AOSP ROM 7.1.2
The purpose of this ROM is to provide support for Xperia S / Acro S

## Build

```
# repo
repo init -u https://github.com/mickybart/android_manifest -b nAOSP-7.1.2_r36
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

# build
source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch aosp_nozomi-userdebug (aosp_hikari-userdebug for Acro S)

make otapackage
```

## Build (Gapps alternative built-in)

```
# repo
repo init -u https://github.com/mickybart/android_manifest -b nAOSP-7.1.2_r36
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

# patch
cd device/sony/nozomi/patch
./aosp-patch-apply.sh ../../../../
cd -

# build
source build/envsetup.sh

export ROM_BUILD_NUM=xx

# => needed for Gapps alternative (adapt for your environment; Use Android Studio to download Sdk 27 and 25)
export ANDROID_HOME=/home/aosp/Android/Sdk/
export ANDROID_SDK_HOME=/home/aosp/Android/Sdk/
export TERM=xterm-color
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk/
export ANDROID_JAVA_TOOLCHAIN=/usr/lib/jvm/java-8-openjdk/

lunch microg_nozomi-userdebug

make otapackage
```

## Rebase issue for manifest

```
cd .repo/manifests
git rebase --abort
git reset --hard origin/nAOSP-7.1.2
cd -
```

## Jack Xmx issue

```
out/host/linux-x86/bin/jack-admin stop-server
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"
out/host/linux-x86/bin/jack-admin start-server

make otapackage
```
