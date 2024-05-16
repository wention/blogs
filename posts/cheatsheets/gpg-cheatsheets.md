gpg 常用命令
==============

```
# 列出公钥
gpg -k
gpg -k --keyid-format=long

# 列出私钥
gpg -K
gpg -K --keyid-format=long
```

## 导入导出

安全导出私钥
```
gpg --armor --export-secret-keys xuyi.828@gmail.com | gpg --armor --symmetric --output wention.gpg.sec.asc
```