---
title: 'Windows 环境配置'
type: post
tags:
  - 环境配置
  - windows
categories: []
keywords:
  - windows
  - scoop
  - winget
---

## 安装常用包
### scoop
```
# 基础
scoop install git scoop-search

# 系统
scoop install everything trafficmonitor
scoop install k-lite-codec-pack-basic-np

# 开发 - 编辑器
scoop install vscode neovim
scoop install neovim ripgrep
scoop install typora

# 开发 - 语言
scoop install nodejs-lts python rustup go

# 开发 - 字体编辑
scoop install fontcreator

# 开发 - 调试
scoop install wireshark 
scoop install dependencies

# 开发 - 实用工具
scoop install cloc

# 网络
scoop install openvpn

# 远程
scoop install vncviewer

# 终端
scoop install alacritty

# 实用工具
scoop install imagemagick powertoys speedtest iperf3 wakemeonlan
scoop install winscp
scoop install localsend
scoop install syncthingtray
scoop install sd-card-formatter
scoop install qbittorrent

# 字体
scoop install JetBrainsMono-NF
```

### winget
```
# 日常
winget install Tencent.WeChat
winget install Tencent.TencentMeeting
```

## 常用配置

### scoop
> refer: https://scoop.sh/

安装
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

使用代理安装
```
[net.webrequest]::defaultwebproxy = new-object net.webproxy "http://127.0.0.1:7890"
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
```


配置
```
# 代理
#scoop config proxy [username:password@]host:port
#scoop config rm proxy
scoop config proxy 127.0.0.1:7890

# 常用 buckets
scoop bucket add extras
scoop bucket add nerd-fonts
```


卸载
```
scoop uninstall scoop

del .\scoop -Force
```


### alacritty

```$env:APPDATA/alacritty/alacritty.toml
live_config_reload = true

[font]
size = 14.0

[font.normal]
family = "JetBrainsMono Nerd Font"
```

### msys2
安装
```
scoop install msys2
```

### WSL2
安装
```
wsl --install
wsl --update

# 列出所有发行版: wsl -l -o
wsl --install --distribution Ubuntu

# 列出当前安装: wsl -l -v

# 设置默认WSL版本
wsl --set-version Ubuntu 2
# 设置默认发行版
wsl -s Ubuntu
```