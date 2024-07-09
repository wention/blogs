银河麒麟桌面版 环境配置
================

## 安装常用包
```
# Qt 开发环境
sudo apt update
sudo aptitude upgrade
sudo aptitude install --with-recommends build-essential cmake
sudo aptitude install --with-recommends qtcreator
sudo aptitude install --with-recommends qt5-default qt5-doc
sudo aptitude install --with-recommends librabbitmq-dev libzmqpp-dev
sudo aptitude install --with-recommends qtbase5-dev qtdeclarative5-dev qtquickcontrols2-5-dev qtmultimedia5-dev qtwebengine5-dev libqt5svg5-dev libqt5charts5-dev libqt5websockets5-dev

sudo aptitude install --with-recommends python3-sqlalchemy
sudo aptitude install --with-recommends pyqt5-dev-tools python3-pyqt5 python3-pyqtgraph python3-pyqt5.qtmultimedia python3-pyqt5.qtchart python3-pyqt5.qtopengl python3-pyqt5.qtquick python3-pyqt5.qtsvg python3-pyqt5.qtsql python3-pyqt5.qtserialport python3-pyqt5.qtwebsockets

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
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```


### docker
> refer: https://docs.docker.com/engine/install/ubuntu/

安装
```
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
  focal stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
``

卸载
```
sudo apt-get purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd
```