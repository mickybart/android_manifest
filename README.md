# nAOSP 8 for Sony Xperia S and Acro S

near AOSP ROM 8
The purpose of this ROM is to provide support for Xperia S / Acro S

## Build

```
repo init -u https://github.com/mickybart/android_manifest -b nAOSP-8
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch aosp_nozomi-userdebug (aosp_hikari-userdebug for Acro S)

make otapackage
```

## Rebase issue for manifest

```
cd .repo/manifests
git rebase --abort
git reset --hard origin/nAOSP-8
cd -
```

## Jack Xmx issue

```
out/host/linux-x86/bin/jack-admin stop-server
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"
out/host/linux-x86/bin/jack-admin start-server

make otapackage
```
