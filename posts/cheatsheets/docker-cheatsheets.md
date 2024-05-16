docker 常用命令
==============


```
# 删除所有 Untaged 镜像
docker rmi $(docker images -f 'dangling=true' -q)
```
