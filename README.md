[![Build Status](https://travis-ci.com/hanwckf/rt-n56u.svg?branch=master)](https://travis-ci.com/hanwckf/rt-n56u)
![GitHub All Releases](https://img.shields.io/github/downloads/hanwckf/rt-n56u/total)
[![release](https://img.shields.io/github/release/hanwckf/rt-n56u.svg)](https://github.com/hanwckf/rt-n56u/releases)

```shell
# Debian/Ubuntu
sudo apt update
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
	fakeroot kmod cpio git python-docutils gettext automake autopoint \
	texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
	libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

# Archlinux/Manjaro
sudo pacman -Syu --needed git base-devel cmake gperf ncurses libmpc \
        gmp python-docutils vim rpcsvc-proto fakeroot cpio help2man

# Alpine
sudo apk add make gcc g++ cpio curl wget nano xxd kmod \
	pkgconfig rpcgen fakeroot ncurses bash patch \
	bsd-compat-headers python2 python3 zlib-dev \
	automake gettext gettext-dev autoconf bison \
	flex coreutils cmake git libtool gawk sudo

# CentOS 7
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* texinfo gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* python-docutils nano help2man fakeroot

# CentOS 8
sudo yum update
sudo yum groupinstall "Development Tools"
sudo yum install ncurses-* flex byacc bison zlib-* gmp-* mpfr-* gettext \
	libtool* libmpc-* gettext-* nano fakeroot

# CentOS 8不能直接通过yum安装texinfo，help2man，python-docutils。请去官网下载发行的安装包编译安装
# 以texinfo为例
# cd /usr/local/src
# sudo wget http://ftp.gnu.org/gnu/texinfo/texinfo-6.7.tar.gz
# sudo tar zxvf texinfo-6.7.tar.gz
# cd texinfo-6.7
# sudo ./configure
# sudo make
# sudo make install

```

* 克隆源码

```shell
git clone --depth=1 https://e.coding.net/hanwckf/rt-n56u/padavan.git /opt/rt-n56u
#git clone --depth=1 https://github.com/hanwckf/rt-n56u.git /opt/rt-n56u
```

* 准备工具链

```shell
cd /opt/rt-n56u/toolchain-mipsel

# （推荐）使用脚本下载预编译的工具链：
sh dl_toolchain.sh

# 或者，也可以从源码编译工具链，这需要一些时间：
./clean_toolchain
./build_toolchain

```

* (可选) 修改机型配置文件

```shell
nano /opt/rt-n56u/trunk/configs/templates/PSG1218.config
```

* 清理代码树并开始编译

```shell
cd /opt/rt-n56u/trunk
./clear_tree
fakeroot ./build_firmware_modify PSG1218
# 脚本第一个参数为路由型号，在trunk/configs/templates/中
# 编译好的固件在trunk/images里
```

***

### 请参阅 ###
- https://www.jianshu.com/p/cb51fb0fb2ac
- https://www.jianshu.com/p/6b8403cdea46

