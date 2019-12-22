# RPI4-Fedora30
File for rasbian to use on RPI4 for fedora30
build the kernel
```bash
git clone https://github.com/raspberrypi/linux
cd linux
git checkout rpi-4.19.y
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- Image modules dtbs
```
Install it in /home/jfclere/TMP/mnt/ext4
```bash
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- INSTALL_MOD_PATH=/home/jfclere/TMP/mnt/ext4 INSTALL_PATH=/home/jfclere/TMP/mnt/ext4 install modules_install
```
