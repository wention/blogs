---
title: Windows 系统优化/自定义
date: 2025-03-03
---

## 官方文档

* [Windows 应用设置对应注册表修改项](https://learn.microsoft.com/zh-cn/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#bkmk-onedrive)


## Windows 11

任务栏图标对齐方式
* 0: 靠左
* 1: 局中

```
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced /v TaskbarAl /t REG_QWORD /d 0
```

添加 计算机 桌面图标
```
reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\HideDesktopIcons\NewStartPanel /v "{20D04FE0-3AEA-1069-A2D8-08002B30309D}" /t REG_DWORD /d 0
```