常用源配置
=========

## 系统源

### ubuntu
```
sudo sed -E -i 's/(archive|security).ubuntu.com/mirrors.ustc.edu.cn/' /etc/apt/sources.list

sudo apt update -y
```

### Manjaro
```
sudo pacman -c China -m rank
# sudo pacman -c China -id
```
