常用源配置
=========

## 系统源

### ubuntu
```
sudo sed -E -i 's/(archive|security).ubuntu.com/mirrors.ustc.edu.cn/' /etc/apt/sources.list

sudo apt update -y
```

apt 代理:
```
Acquire {
  http::Proxy "http://192.168.214.1:7890";
  https::Proxy "http://192.168.214.1:7890/";
}
```

### Manjaro
```
sudo pacman -c China -m rank
# sudo pacman -c China -id
```

## 软件源

### pip
```
pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple
```

### npm
```
npm config set registry https://registry.npm.taobao.org/
yarn config set registry https://registry.npm.taobao.org/
```