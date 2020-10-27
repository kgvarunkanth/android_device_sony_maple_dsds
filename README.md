Device configuration for Sony Xperia XZ Premium Dual sim variant (maple_dsds)
========================================================

Description
-----------

This repository is for LineageOS 18.0 on Sony Xperia XZ Premium Dual sim variant (maple_dsds).

How to build LineageOS
----------------------

* Make a workspace:

        mkdir -p ~/lineageos
        cd ~/lineageos

* Initialize the repo:

        repo init -u git://github.com/LineageOS/android.git -b lineage-18.0

* Create a local manifest:

        vim .repo/local_manifests/roomservice.xml

        <?xml version="1.0" encoding="UTF-8"?>
        <manifest>
            <!-- SONY -->
            <project name="whatawurst/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-18.0" />
            <project name="kgvarunkanth/android_device_sony_yoshino-common1" path="device/sony/yoshino-common" remote="github" revision="lineage-18.0" />
            <project name="kgvarunkanth/android_device_sony_maple_dsds" path="device/sony/maple_dsds" remote="github" revision="lineage-18.0" />

            <!-- Pinned blobs for maple_dsds -->
            <project name="kgvarunkanth/android_vendor_sony_maple_dsds" path="vendor/sony/maple_dsds" remote="github" revision="lineage-18.0" />
        </manifest>

* Sync the repo:

        repo sync

* Extract vendor blobs

        cd device/sony/maple_dsds
        ./extract-files.sh

* Setup the environment

        source build/envsetup.sh
        lunch lineage_maple_dsds-userdebug

* Build LineageOS

        m bacon
