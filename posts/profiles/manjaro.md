Manjaro 环境配置
================

## 更新源
```
#sudo pacman-mirrors -c China -m rank
sudo pacman-mirrors -c China -id
```

## 安装常用包
```
sudo pacman -S zsh tmux neovim
sudo pacman -S --asdeps python-pynvim xclip wl-clipboard
sudo pacman -S noto-fonts-cjk ttf-jetbrains-mono-nerd
sudo pacman -S gnome-shell-extension-caffeine
sudo pacman -S neofetch

sudo pacman -S gopass

sudo pacman -S docker
sudo pacman -S --asdeps docker-buildx docker-compose

sudo pacman -S timeshift
sudo pacman -S virt-manager
sudo pacman -S qemu-emulators-full

sudo pacman -S qemu-user-static
sudo pacman -S qemu-user-static-binfmt

sudo pacman -S base-devel 
sudo pacman -S yay
yay -S visual-studio-code-bin
yay -S wechat-bin


# Desgin
sudo pacman -S gimp inkscape blender


# Office
yay -S wps-office-cn


# Games
sudo pacman -S retroarch
sudo pacman -S --asdeps libretro-shaders retroarch-assets-ozone retroarch-assets-xmb
```

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
sudo pacman -S tmux
```

```
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```

### neovim
安装
```
sudo pacman -S neovim
```

配置
```
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```
> refer: https://nvchad.com/docs/quickstart/install

### 安装中文输入法
安装
```
sudo pacman -S ibus-rime rime-wubi
```

配置
```
mkdir ~/.config/ibus/rime

cat > ~/.config/ibus/rime/default.custom.yaml << EOF
patch:
  schema_list:
    - schema: wubi_pinyin
EOF

# applying
rm ~/.config/ibus/rime/default.yaml && ibus-daemon -drx
```

### gopass
安装
```
sudo pacman -S gopass
```

配置
```
gopass clone git@github.com:wention/pwstore.git

gpg --import /path/to/gpg/key.asc
```


### Docker

```
sudo pacman -S docker
sudo pacman -S --asdeps docker-buildx docker-compose

sudo pacman -S nvidia-container-toolkit
sudo nvidia-ctk runtime configure --runtime=docker

sudo systemctl enable --now docker
sudo usermod -aG docker $USER
```


### OpenVPN

```
sudo pacman -S networkmanager-openvpn
sudo pacman -S --asdeps libnma

nmcli connection import type openvpn file /path/to/config.ovpn
```
