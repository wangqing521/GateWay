固件特点及说明:

1.所有源码来自lean的源码仓库:https://github.com/coolsnowwolf/lede

2.固件默认eth0地址:192.168.120.1

3.无WEB服务，默认开启SSH服务，管理需用SSH或TTL

4.固件带x819无线驱动，默认开启，可在命令行下运行 "wlan 你的SSID 你的密码" 配置无线

5.固件集成PPTP,VXLAN,N2N,GRE等服务，专为异地组网定制

6.spiflash版需要硬改16M spiflash（型号仅测试w25q128，需要的自行测试，2M的spiflash无法运行本固件），SD卡版Uboot中集成了SPIflash的驱动，可以在Uboot中烧写SPIflash（需要在电脑上搭建tftp服务器，用于上传文件）

7.uboot用tftp需要设置客户端和服务器ip，然后在上传文件到内存，例如:

setenv ipaddr 192.168.1.101

setenv serverip 192.168.1.100

tftp 42000000 gateway-spi.bin

spiflash烧写前需要先输入：sf probe

然后烧录：sf update 42000000 0 1000000

8.spiflash版首次运行时要在终端输入：firstboot

然后再输入：mount -t jffs2 /dev/mtdblock5 /mnt
