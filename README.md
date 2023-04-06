# Apptainer-runtime

## 快速开始

1. 下载微信镜像

   ```bash
   wget https://github.com/yswtrue/apptainer-runtime/releases/download/stable/wechat.sif
   wget https://github.com/yswtrue/apptainer-runtime/releases/download/latest/wechat-web-devtools.sif
   ```

2. 安装Apptainer（[详情](https://apptainer.org/docs/admin/main/installation.html#install-from-pre-built-packages)）


   gentoo:

   ```bash
   echo "app-containers/apptainer suid" | sudo tee  /etc/portage/package.use/apptainer
   sudo emerge app-containers/apptainer
   ```

   centos:

   ```bash
   sudo yum install epel-release -y
   sudo yum install apptainer-suid -y
   ```

   ubuntu:

   ```bash
   sudo add-apt-repository -y ppa:apptainer/ppa
   sudo apt update
   sudo apt install apptainer-suid -y
   ```

  1. 运行微信

     ```bash
     apptainer run wechat.sif
     apptainer run wechat-web-devtools.sif
     ```

## 本地构建最新容器镜像

1. 安装 debootstrap 和 singularity

   gentoo:

   ```bash
   echo "app-containers/apptainer suid" | sudo tee  /etc/portage/package.use/apptainer
   sudo emerge dev-util/debootstrap app-containers/apptainer
   ```

   centos:

   ```bash
   sudo yum install epel-release -y
   sudo yum install debootstrap apptainer-suid -y
   ```

   ubuntu:

   ```bash
   sudo add-apt-repository -y ppa:apptainer/ppa
   sudo apt update
   sudo apt install debootstrap apptainer-suid -y
   ```

2. 构建镜像

   ```bash
   git clone https://github.com/yswtrue/apptainer-runtime.git
   cd apptainer-runtime
   apptainer build wechat.sif wechat/deepin-wechat.def
   ```

3. 运行微信

   ```bash
   apptainer run wechat.sif
   ```

## xdg-open-server

宿主机运行xdg-open-server,微信聊天文件和链接可以直接调用宿主机软件打开

```bash
# 编译
gcc -lX11 -lpthread main.c -o xdg-open-server
# 运行
./xdg-open-server
```
> 详情 https://github.com/kitsunyan/xdg-open-server


## 已知问题

- [微信开发者工具也许会遇到内存溢出的问题,有待验证](https://github.com/NixOS/nixpkgs/issues/224828#issuecomment-1499317731)