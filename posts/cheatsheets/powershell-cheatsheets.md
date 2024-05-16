powershell 常用命令
==================

解决 Windows 与 Linux 双系统的时间冲突
```
# 强制 Windows 使用 UTC
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_QWORD /d 1
```