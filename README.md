#nAOSP 5.1 for Sony Xperia S / Acro S
##GNU/Linux | Android | Convergence

near AOSP ROM 5.1
The purpose of this ROM is to provide support for Xperia S and Acro S

##Build
###Common

```
repo init -u https://github.com/mickybart/android_manifest -b gnulinux-support-nAOSP-5.1
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync --fetch-submodules

cd device/sony/nozomi/patch
./aosp-patch-apply.sh <path to the source code>
cd -
source build/envsetup.sh

export ROM_BUILD_NUM=xx
```

###Android
```
lunch aosp_nozomi-userdebug   (aosp_hikari-userdebug for Acro S)

make otapackage
```

###GNU/Linux
See [the main document](https://github.com/mickybart/gnulinux_support/tree/master/Docs/main.md) for GNU/Linux support.
```
lunch gnulinux_nozomi-userdebug

make otapackage
make hybris
```

##Build update
```
cd device/sony/nozomi/patch
./aosp-patch-unapply.sh <path to the source code>
cd -

repo sync --fetch-submodules

cd device/sony/nozomi/patch
./aosp-patch-apply.sh <path to the source code>   (eventually merge manually in case of conflict)
cd -
```

