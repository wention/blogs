APT 配置
========

## 代理
```
cat > /etc/apt/apt.conf.d/99proxy <<EOF
Acquire::http::Proxy "http://10.1.1.89:7890";
Acquire::https::Proxy "https://10.1.1.89:7890";
EOF
```