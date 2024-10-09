# 准备系统
下载debian 12网络安装的iso包，debian-12.7.0-amd64-netinst.iso
下载地址：https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.7.0-amd64-netinst.iso

# 注意事项
- 非root用户需要确保有sudo权限，并用sudo执行以下命令 

# 安装依赖
apt-get install -y ifupdown iproute2 openssh-server isc-dhcp-client isc-dhcp-server ethtool libcurl4-openssl-dev libczmq-dev libhyperscan-dev libpcre2-dev libssl-dev libpcap-dev redis redis-server postgresql nginx dnsmasq rsyslog build-essential

apt-get install -y linux-headers-`uname -r`

# 下载、编译、安装dpdk
apt-get install -y python3-pip python3-pyelftools libnuma-dev
pip3 install meson ninja

wget https://fast.dpdk.org/rel/dpdk-23.11.2.tar.xz
unxz dpdk-23.11.2.tar.xz
tar xvf dpdk-23.11.2.tar

cd dpdk-stable-23.11.2
meson setup -Dmachine=default build
cd build
ninja
meson install
/sbin/ldconfig -v

# 拷贝
将安装包拷贝到系统中

# 解压
tar xzvf xsnos-v0.8.0-21-g88dce58-amd64.tar.gz

# 安装
cd xsnos
./scripts/install.sh 

# 登陆
https://{主机的ip}

默认用户名密码: admin/admin12345678

# 上传license


# 配置管理口
点击导航栏 系统-管理接口，配置好系统的管理口

# 绑定网卡
点击导航栏 引擎设置-网卡绑定，绑定要监控的网卡

# 启动引擎
点击导航栏 引擎设置-引擎状态，查看引擎，并启动引擎

# 如何使用被动资产管理功能
点击导航栏 资产发现-设置，将功能开启

# 数据准备
此时可以将绑定的网卡接入流量，或者上传pcap包测试
