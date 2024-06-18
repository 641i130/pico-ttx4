# pico-ttx4

### Hardware Emulated TTX4 IO

This currently will look exactly like the TTX4 USB input device I reversed [here](https://github.com/641i130/ttx4-usbio). At least, according to the linux tool `lsusb`.

## Build instructions

1. Install CMake (at least version 3.13), and GCC cross compiler
   **Debian:**

```
sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi
```

**Arch:**

```
sudo pacman -S --noconfirm arm-none-eabi-gcc arm-none-eabi-newlib arm-none-eabi-binutils cmake gcc
```

2. Download the pico-sdk and set the `PICO_SDK_PATH` environment variable. Also set the variable in your `.bashrc`, `.zshenv`, or even `/etc/environment` for future use.

```
git clone https://github.com/raspberrypi/pico-sdk
cd pico-sdk
git submodule update --init
export PICO_SDK_PATH=$PWD
cd ..
```

3. Clone and build this repository

```
git clone https://github.com/Drewol/rp2040-gamecon
cd rp2040-gamecon
mkdir build
cd build
cmake ..
make
```

4. Upload the `pico-ttx4.uf2` that was created in your build directory to the pico device by mounting the partition (see script below):

5. Find the disk to mount:

   ```bash
   sudo mkdir /mnt/pico
   sudo mount `sudo fdisk -l | grep 'W95 FAT16' | awk '{print $1}'` /mnt/pico
   sudo cp pico-ttx4.uf2 /mnt/pico
   ```

   

