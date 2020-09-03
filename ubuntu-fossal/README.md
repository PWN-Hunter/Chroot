# NetHunter custom-chroot builder

* Build a older NetHunter chroot (Supports more tools that are deprecated/obselete in kali-rolling)
* This chroot is based on Ubuntu fossal (AKA focal, 20.04.1 LTS) build as it supports arm64.
* Also sources.list has " [trusted=yes] " to get updates, upgrades, install from http://ports.ubuntu.com/ubuntu-ports/.
* deb [trusted=yes] http://ports.ubuntu.com/ubuntu-ports/ focal main contrib non-free
## What have i added?
### minimal will have these packages automatically when compiling
* Nothing really yet

## Docker support
```bash
docker build -t nethunter .
docker run --privileged --name nethunter_build -i -t nethunter 2>&1 | tee output.log
docker cp nethunter_build:/root/nethunter-fs/output .
```

## Dependencies

This could be built on any debian based system but I recommend building on Kali.

```bash
apt-get install -y git-core gnupg flex bison gperf libesd0-dev build-essential zip curl libncurses5-dev zlib1g-dev libncurses5-dev gcc-multilib g++-multilib parted kpartx debootstrap pixz qemu-user-static abootimg cgpt vboot-kernel-utils vboot-utils bc lzma lzop xz-utils automake autoconf m4 dosfstools rsync u-boot-tools schedtool git e2fsprogs device-tree-compiler ccache dos2unix debootstrap
```

## Running by itself

To create a ubuntu system (default arch is arm64 now and -u stands for ubuntu):
```bash
./build.sh -u
```
