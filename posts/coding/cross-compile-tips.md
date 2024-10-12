交叉编译
=======

```
sudo apt install cmake git crossbuild-essential-arm64
```

# 跨 ARCH 交叉编译
## ubuntu arm64
```
sudo debootstrap --arch arm64 --variant=minbase --components=main,restricted,universe,multiverse --foreign focal rootfs https://mirrors.ustc.edu.cn/ubuntu-ports
sudo chroot rootfs /debootstrap/debootstrap --second-stage

# 安装依赖
apt install build-essential cmake git
```

## 银河麒麟V10 SP1 Arm64 交叉编译

```
# 银河麒麟 Arm64 交叉编译
sudo ln -s /usr/share/debootstrap/scripts/focal /usr/share/debootstrap/scripts/10.1
sudo debootstrap --no-check-gpg --arch arm64 --components=main,restricted,universe,multiverse --foreign 10.1 rootfs http://archive.kylinos.cn/kylin/KYLIN-ALL

sudo chroot rootfs /debootstrap/debootstrap --second-stage
```