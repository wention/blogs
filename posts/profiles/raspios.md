RaspiOS bookworm 环境配置
================

## 更新源
```
sudo sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list

sudo sed \
  -e 's|http://archive.raspberrypi.org|http://mirrors.ustc.edu.cn/raspberrypi|g' \
  -e 's|http://archive.raspberrypi.com|http://mirrors.ustc.edu.cn/raspberrypi|g' \
  -i.bak \
  /etc/apt/sources.list.d/raspi.list

sudo apt update -y
```

## 安装常用包

sudo apt install git tmux zsh
sudo aptitude install vgabios qemu-system-arm qemu-user-static libguestfs-tools libvirt-daemon virt-manager

sudo aptitude install neofech ncdu ranger ripgrep fzf wl-clipboard xclip

## 常用配置

### zsh
```
git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

chsh -s $(which zsh)

zsh

# 安装插件 zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# 安装插件 zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### tmux
安装
```
sudo apt install tmux
```

```
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```

### neovim
安装
```
sudo apt install neovim
```

配置
```
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

> refer: https://nvchad.com/docs/quickstart/install

### docker
> refer: https://docs.docker.com/engine/install/ubuntu/

安装
```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

curl -fsSL https://get.docker.com -o get-docker.sh
sudo DOWNLOAD_URL=https://mirrors.ustc.edu.cn/docker-ce sh get-docker.sh

sudo usermod -aG docker $USER
```


卸载
```
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```
