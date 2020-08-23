# RPI4-Fedora30
Look for the config in https://github.com/jfclere/tomcatPI/blob/master/cloud/bcm2711_defconfig
File for rasbian to use on RPI4 for fedora30
build the kernel
```bash
git clone https://github.com/raspberrypi/linux
cd linux
git checkout rpi-4.19.y
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- Image modules dtbs
```
Install it in /home/jfclere/TMP/mnt/ext4 (or something like /run/media/jfclere/1a17da7a-d604-4e51-983c-e86d06d995e1)
```bash
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- INSTALL_MOD_PATH=/home/jfclere/TMP/mnt/ext4 INSTALL_PATH=/home/jfclere/TMP/mnt/ext4 install modules_install
```
Copy the kernel in the vfat boot partition (something like /run/media/jfclere/8499-9CF0)
```bash
cp arch/arm64/boot/Image /run/media/jfclere/8499-9CF0/kernel8.img
```
# Using rpi-5.4.y
The bcm2711-rpi-4-b.dtb is for bcm2711-rpi-4-b.dtb, use the one you build with the new kernel
```bash
cp ./arch/arm64/boot/dts/broadcom/bcm2711-rpi-4-b.dtb /run/media/jfclere/8499-9CF0/bcm2711-rpi-4-b.dtb
```
*CGROUPS_MEMORY: missing* is fixed by adding "cgroup_enable=memory" in /boot/efi/cmdline.txt
I have:
```
wc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=/dev/mmcblk0p3 elevator=deadline rootfstype=ext4 fsck.repair=yes rootwait cgroup_enable=memory
```
