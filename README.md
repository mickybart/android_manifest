#AOSP 5.1.1
##GNU/Linux | Android | Convergence

Pure AOSP 5.1.1

##Build
###Common

```
repo init -u https://github.com/mickybart/android_manifest -b gnulinux-support-5.1
mkdir .repo/local_manifests/
ln -s ../manifests/local_manifest.xml .repo/local_manifests/local_manifest.xml
repo sync --fetch-submodules

source build/envsetup.sh
```

###Android
```
lunch

make otapackage
```

###GNU/Linux
See [the main document](https://github.com/mickybart/gnulinux_support/tree/master/Docs/main.md) for GNU/Linux support.
```
lunch #select gnulinux_<device>-userdebug

make otapackage

make hybris
```

