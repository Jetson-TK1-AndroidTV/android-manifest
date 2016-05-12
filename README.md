Welcome to the Jetson TK1 Android L Open Source + Binary Driver Release.

In this README, you will find sync, build, and flashing instructions.

---------
HowTo Sync:
---------

Syncing this release requires git and the repo tool from Google:
http://source.android.com/source/downloading.html#installing-repo

	mkdir ~/jtk1-android-l-open-source
	cd ~/jtk1-android-l-open-source
	COMING SOON!


---------
HowTo Build:
---------

Building this release requires a Linux build environment configured to
build Android: http://source.android.com/source/initializing.html

As to u-boot compiling, you should have device-tree-compiler upgraded to dtc
1.4 or newer

Additionally, you will be required to agree to license terms when extracting
the binary drivers.

	cd ~/jtk1-android-l-open-source
	export TOP=`pwd`
	cd vendor/nvidia/licensed-binaries
	./extract-nv-bins.sh "I ACCEPT"
	cd $TOP
	source build/envsetup.sh
	setpaths
	export SECURE_OS_BUILD=n
	lunch wx_na_wf-eng
	mp dev


---------
HowTo Flash:
---------

Before flashing, you should put your Jetson TK1 into RCM(forced-recovery mode)

	hw method
		Hold FORCE_RECOVERY key and press RESET, then release FORCE_RECOVERY key
	sw method
		`adb reboot forced-recovery` if you have android installed already

Now it only supports flashing product in Linux enviromment.

	cd $OUT
	sudo ./nvflash --bct flash_pm358_792.cfg --setbct --configfile jetson_flash.cfg --dtbfile tegra124-jetson_tk1-pm375-000-c00-00.dtb --create --bl fastboot.bin --odmdata 0x6009C000 --go
