Linux 主机配置为网关
==================

> 目前仅在未安装 docker、libvirtd 的环境中测试ok!

```shell
sudo sysctl -w net.ipv4.ip_forward=1

# 你可以验证是否生效
cat /proc/sys/net/ipv4/ip_forward
```

配置 NAT（通过 iptables）
假设你的外网网卡是 eth0，内网网卡是 eth1，运行以下命令：
```shell
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

然后允许转发流量
```shell
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
```