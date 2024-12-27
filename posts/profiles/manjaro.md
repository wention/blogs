Manjaro 环境配置
================

## 更新源
```
#sudo pacman-mirrors -c China -m rank
sudo pacman-mirrors -c China -id
```

## 安装常用包
```
sudo pacman -S gopass
```

## 常用配置

### zsh
```
git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

chsh -s $(which zsh)

zsh

# 安装插件 zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# 安装插件 zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

### tmux
安装
```
sudo pacman -S tmux
```

```
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```

### neovim
安装
```
sudo pacman -S neovim
```

配置
```
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```
> refer: https://nvchad.com/docs/quickstart/install

### 安装中文输入法
安装
```
sudo pacman -S rime-wubi
```

配置
```
mkdir ~/.config/ibus/rime

cat > ~/.config/ibus/rime/default.custom.yaml << EOF
patch:
  schema_list:
    - schema: wubi_pinyin
EOF

# applying
rm ~/.config/ibus/rime/default.yaml && ibus-daemon -drx
```

### gopass
安装
```
sudo pacman -S gopass
```

配置
```
gopass clone git@github.com:wention/pwstore.git

gpg --import /path/to/gpg/key.asc
```
