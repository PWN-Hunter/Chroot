# NetHunter vanilla-chroot builder

Build a basic NetHunter chroot

## What have i added?
### minimal will have these packages automatically when compiling
* kali-linux-nethunter (Get kex and other stuff)
* sudo (Just in case, if things mess up)
* kali-linux-core (Because why not?)
* exploitdb (for nethunter app)
* msfpc (for nethunter app)
### Full will have same stuff as minimal but heres a new things for it
#### Also i dont provide full as it will be too much to upload/work on.
* kali-linux-large (For more tools)
* And some things more that builder adds
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

To create a full NetHunter system:
```bash
./build.sh -f -a arm64
```
To create a minimal NetHunter filesystem:
```bash
./build.sh -m -a arm64
```
