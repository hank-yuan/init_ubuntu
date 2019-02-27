# 重装系统初始化

## 1.更改ubuntu源

查看当前系统版本`lsb_release -a`

使用清华源

备份原文件 `cp /etc/apt/sources.list /etc/apt/sources.list.bak `

修改源 `vi /etc/apt/sources.list`

```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ cosmic-proposed main restricted universe multiverse
```

更新 `apt update`

更新软件`apt upgrade`

## 2.typora

添加公钥`wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -`

设置源

```bash
add-apt-repository 'deb https://typora.io/linux ./'
apt-get update
```

安装 `apt-get install typora`

## 3.oh-my-fish,使用eclm 主题

安装**fish**`apt install fish`

安装**oh-my-fish**`curl -L https://get.oh-my.fish | fish`

设置fish主题 `omf install eclm`

查看 fish shell 的安装位置：

```
$ which fish
/usr/bin/fish
```

修改默认 shell 为 fish shell

```
chsh -s /usr/bin/fish
```

## 4. dock 使用plank/docky

## 5.launcher

1. rofi
2. ulauncher
3. albert

## 6.spacevim, neovim

`apt install vim`

### neovim

### spacevim

## 7.界面美化

### gnome-tweak

终端键入命令：`sudo add-apt-repository universe`

回车再次键入命令：`sudo apt install gnome-tweak-tool`

### arch-theme

### arch-icon

## 8.开发相关

### 利用`proxychains`终端使用socks5代理安装node/node包

1. proxychains安装

```bash
git clone https://github.com/rofl0r/proxychains-ng.git
cd proxychains-ng
./configure
make && make install
cp ./src/proxychains.conf /etc/proxychains.conf
cd .. && rm -rf proxychains-ng
```

也可以用`brew install proxychains-ng`安装。

2. 编辑proxychains配置

```bash
vim /etc/proxychains.conf
```

3. 将`socks4 127.0.0.1 9095`改为

```conf
socks5 127.0.0.1 1080
```

4. 使用方法

**在需要代理的命令前加上 proxychains4 ，如：**

```bash
proxychains4 wget http://xxx.com/xxx.zip
```

### vscode

### nvm

**`note:`** fish 终端不支持nvm,安装omf插件来支持nvm `omf install nvm`

1. 使用官方安装脚本`curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash`

2. 重启终端 ，`nvm --version`查看是否安装成功

### yarn

添加安装源

```bash
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
```

安装

```bash
apt update
apt install yarn
```

**`note:`**如果有被墙的包使用`proxychains4 yarn install XXX`

## 9.下载工具

curl , wget, aria2, axel, amule, webtorrent, bitTorrent, utorrent, rtorrent

## 10. 定时任务

### 1. 检查 crontab 服务是否安装

`crontab -l`

如果显示 ‘no crontab for root’ 或者 显示当前的任务列表 或者 不报错 那说明已经安装，

如果没有安装 cron 服务
Contos
`yum -y install vixie-cron crontab`

ubuntu

`apt-get install cron`

### 2. 编辑任务

`crontab -e `选择编辑器后进入

增加一行如：

`0 0 * * 4 /root/go.sh`

