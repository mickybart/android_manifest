#nAOSP 7.1.1 for Sony Xperia S and Acro S

near AOSP ROM 7.1.1
The purpose of this ROM is to provide support for Xperia S / Acro S

##Build

```
repo init -u https://github.com/mickybart/android_manifest -b nAOSP-7.1.1
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync

source build/envsetup.sh

export ROM_BUILD_NUM=xx

lunch aosp_nozomi-userdebug (aosp_hikari-userdebug for Acro S)

make otapackage
```

##Jack Xmx issue

```
out/host/linux-x86/bin/jack-admin stop-server
export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4096m"
out/host/linux-x86/bin/jack-admin start-server

make otapackage
```
