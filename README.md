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
