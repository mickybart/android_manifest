build AOSP ROM (bAOSP) for Sony Xperia S (nozomi)

This branch is used to have a vanilla AOSP build for Xperia S.
We have some "minor" AOSP code fix to support full features of this device (eg: FMradio)

1. initialize the repo:

    repo init -u https://github.com/mickybart/android_manifest -b bAOSP-5.0

2. sync repo:

    repo sync

3. build:

    - source build/envsetup.sh
    - lunch aosp_nozomi-userdebug
    - export USE_CCACHE=1
    - export CCACHE_DIR=.ccache
    - prebuilts/misc/linux-x86/ccache/ccache -M 50G
    - make

    (see: http://source.android.com/source/building.html)
