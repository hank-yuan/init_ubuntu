# linux 个人云

## 安装caddy

`curl https://getcaddy.com | bash -s personal http.filebrowser`

## 创建配置文件

`mkdir /etc/caddy`

`vim Caddyfile`

```
:80 {
 timeouts none
 gzip
 filebrowser / /mnt/sda1 {
  database /usr/local/caddy/filebrowser.db
 }
}

```

## 挂载硬盘

### 1、建一个目录（挂载磁盘分区）
mkdir /mnt/sda1
#通过mkdir命令创建文件夹



### 2、挂载/dev/sda1分区
mount /dev/sda1 /mnt/sda1
#挂载/dev/sda1到/mnt/sda1目录下



### 3、然后进入挂载分区目录即可
cd /mnt/sda1

cd 命令进入该目录，就可以看到分区存放的文件了

## 后台运行，并管理

