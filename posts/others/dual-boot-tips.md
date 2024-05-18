---
title: 'Kylin 发行版源'
date: 2024-05-17
---

## 修复 Windows 与 Linux 时间冲突
```
# 强制 Windows 使用 UTC
Reg add HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation /v RealTimeIsUniversal /t REG_QWORD /d 1
```

## 引导冲突
重建 Linux 引导
```
# UEFI
grub-install --target=x86_64_efi --efi-directory=/boot/efi --bootloader-id=Manjaro --force

# grub-mkconfig -o /boot/grub/grub.cfg

# 写入 nvram
# efibootmgr -c -d /dev/sda -p 1 -L Manjaro -l \EFI\Manjaro\grubx64.efi
# efibootmgr -b <bootnum> -B
```