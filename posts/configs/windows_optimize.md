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