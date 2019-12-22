# RPI4-Fedora30
File for rasbian to use on RPI4 for fedora30
build the kernel
```bash
git clone https://github.com/raspberrypi/linux
cd linux
git checkout rpi-4.19.y
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- bcm2711_defconfig
make ARCH=arm64 CROSS_COMPILE=aarch64-linux-gnu- zImage modules dtbs
```
