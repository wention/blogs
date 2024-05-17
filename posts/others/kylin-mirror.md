---
title: 'Kylin 发行版源'
date: 2024-05-17
---

## 银河麒麟桌面操作系统V10 (SP1)

/etc/os-release
```
NAME="Kylin"
VERSION="银河麒麟桌面操作系统V10 (SP1)"
VERSION_US="Kylin Linux Desktop V10 (SP1)"
ID=kylin
ID_LIKE=debian
PRETTY_NAME="Kylin V10 SP1"
VERSION_ID="v10"
HOME_URL="http://www.kylinos.cn/"
SUPPORT_URL="http://www.kylinos.cn/support/technology.html"
BUG_REPORT_URL="http://www.kylinos.cn/"
PRIVACY_POLICY_URL="http://www.kylinos.cn"
VERSION_CODENAME=kylin
UBUNTU_CODENAME=kylin
PROJECT_CODENAME=V10SP1
KYLIN_RELEASE_ID="2303"
```

/etc/apt/source.list
```
# 本文件由源管理器管理，会定期检测与修复，请勿修改本文件
deb http://archive.kylinos.cn/kylin/KYLIN-ALL 10.1-2303-hwe-updates main universe multiverse restricted
deb http://archive.kylinos.cn/kylin/KYLIN-ALL 10.1-2303-updates main universe multiverse restricted
deb http://archive.kylinos.cn/kylin/KYLIN-ALL 10.1 main restricted universe multiverse
deb http://archive2.kylinos.cn/deb/kylin/production/PART-V10-SP1/custom/partner/V10-SP1 default all
```

