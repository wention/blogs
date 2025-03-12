---
title: '离线部署 vscode 远程'
date: 2025-03-12
---

```sh
#!/bin/sh

ARCH="arm64"
PLATFORM="linux"
COMMIT_ID="fabdb6a30b49f79a7aba0f2ad9df9b399473380f"
IMAGE="ubuntu:22.04"

EXTENSIONS="vscodevim.vim ms-python.python ms-vscode.cpptools-extension-pack"

if [ "$ARCH" = "arm64" ];then
  IMAGE="arm64v8/ubuntu:20.04"
fi

docker run --rm -i -v `pwd`:/vscode $IMAGE "sh" <<EOF
sed -E -i 's/(archive|security|ports).ubuntu.com/mirrors.ustc.edu.cn/' /etc/apt/sources.list
apt update -y
apt install -y curl
if [ ! -e /vscode/download-vs-code.sh ]; then
  curl -L https://raw.githubusercontent.com/wention/dl-vscode-server/refs/heads/main/download-vs-code.sh -o /vscode/download-vs-code.sh
  chmod +x /vscode/download-vs-code.sh
fi

bash /vscode/download-vs-code.sh "${PLATFORM}" "${ARCH}" --cli --use-commit ${COMMIT_ID}
bash /vscode/download-vs-code.sh "${PLATFORM}" "${ARCH}" --use-commit ${COMMIT_ID} --extensions "${EXTENSIONS}"

rm -rf ~/.vscode-server/data/*
tar -cJf /vscode/vscode_${COMMIT_ID}_${PLATFORM}_${ARCH}.tar.bz2 -C ~/.vscode-server .
exit 0
EOF
```