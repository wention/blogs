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

```
## Export all public keys
gpg -a --export > mypubkeys.asc

## Export all encrypted private keys (which will also include corresponding public keys)
gpg -a --export-secret-keys > myprivatekeys.asc

## Export gpg's trustdb to a text file
gpg --export-ownertrust > ownertrust.txt

## Restore the public and secret keyrings and trust database
gpg --import myprivatekeys.asc
gpg --import mypubkeys.asc
gpg -K
gpg -k
gpg --import-ownertrust otrust.txt
```

安全导出私钥
```
gpg --armor --export-secret-keys xuyi.828@gmail.com | gpg --armor --symmetric --output wention.gpg.sec.asc
```
