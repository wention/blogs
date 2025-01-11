powershell 常用命令
==================

解决 Windows 与 Linux 双系统的时间冲突
```
# 强制 Windows 使用 UTC
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_QWORD /d 1
```

Disable password expiration for user
```
cmd.exe /c wmic useraccount where "name='vagrant'" set PasswordExpires=FALSE
```

Windows 激活命令
```
slmgr -ipk 密钥
slmgr -skms 服务器地址
slmgr -ato 
slmgr -dlv
```
