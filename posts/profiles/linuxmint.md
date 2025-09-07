Mint 环境配置
================

## 更新源
```
sudo sed -E -i 's/(ports|archive|security).ubuntu.com/mirrors.ustc.edu.cn/' /etc/apt/sources.list.d/official-package-repositories.list
sudo sed -E -i 's/packages.linuxmint.com/mirrors.ustc.edu.cn\/linuxmint/' /etc/apt/sources.list.d/official-package-repositories.list

sudo apt update -y
```

## 安装常用包
```
openssh-server

tmux zsh

neofetch
gdu ranger


# 开发
git cmake build-essential
cloc

# 交叉统译
qemu-user-static qemu-user-binfmt

# 虚机
virt-manager virt-viewer qemu-system-arm

# 图像处理
gimp inkscape blender

# 视频
ffmpeg mpv
```

#### Qt 开发
```
# QWidgets
qtbase5-dev qtchooser qttools5-dev-tools qttools5-dev
qtbase5-examples qttools5-doc qt5-doc qt5-doc-html

# QML
qtdeclarative5-dev qtdeclarative5-dev-tools qtquickcontrols2-5-dev
qtdeclarative5-doc qtdeclarative5-examples qtquickcontrols2-5-doc qtquickcontrols2-5-examples

# WebEngine
qtwebengine5-dev qtwebengine5-dev-tools
qtwebengine5-doc qtwebengine5-examples

# DB
libqt5sql5-odbc
odbcinst unixodbc-dev odbc-postgresql

qtcreator
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
sudo apt install tmux
```

```
git clone https://github.com/gpakosz/.tmux.git ~/.tmux
ln -s -f ~/.tmux/.tmux.conf ~/.tmux.conf
cp ~/.tmux/.tmux.conf.local ~/.tmux.conf.local
```

### neovim
安装
```
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt update
sudo apt install neovim ripgrep xclip
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
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
  $(. /etc/os-release && echo "$UBUNTU_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get purge docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# use Docker without root privileges
sudo usermod -aG docker $USER
```


卸载
```
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```

### 安装中文输入法
安装
```
sudo apt install ibus-rime rime-data-wubi
```

配置
```
mkdir -p ~/.config/ibus/rime

cat > ~/.config/ibus/rime/default.custom.yaml << EOF
patch:
  schema_list:
    - schema: wubi_pinyin
EOF

# applying
rm ~/.config/ibus/rime/default.yaml && ibus-daemon -drx
```

> 
