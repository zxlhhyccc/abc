# abc

CentOS6和CentOS7 一键更换内核，一键安装锐速[lotServer]
````
#wget --no-check-certificate https://www.zhangfangzhou.cn/sh/ruisu.sh
wget --no-check-certificate https://raw.githubusercontent.com/zxlhhyccc/abc/master/ruisu.sh
bash ruisu.sh
`````
手动更换内核
CentOS6更换内核
`````
#rpm -ivh http://file.asuhu.com/kernel/kernel-firmware-2.6.32-504.3.3.el6.noarch.rpm
rpm -ivh https://github.com/zxlhhyccc/abc/raw/master/centos6-7/kernel-firmware-2.6.32-504.3.3.el6.noarch.rpm
#rpm -ivh http://file.asuhu.com/kernel/kernel-2.6.32-504.3.3.el6.x86_64.rpm --force
rpm -ivh https://github.com/zxlhhyccc/abc/raw/master/centos6-7/kernel-2.6.32-504.3.3.el6.x86_64.rpm --force
`````
查看内核版本
````
cat /boot/grub/grub.conf | awk '$1=="title" {print i++ " : " $NF}'
0 : (2.6.32-504.3.3.el6.x86_64)
1 : (2.6.32-642.13.1.el6.x86_64)
`````
确认内核版本
`````
cat /boot/grub/grub.conf | awk '$1=="title" {print i++ " : " $NF}'|grep '2.6.32-504'|awk '{print $1}'
`````
设置启动的内核
````
vi /boot/grub/grub.conf
default=0
````
重启
````
reboot
`````
确认内核版本
`````
uname -r
2.6.32-504.3.3.el6.x86_64
`````
CentOS7更换内核
````
#rpm -ivh http://file.asuhu.com/kernel/kernel-3.10.0-229.1.2.el7.x86_64.rpm --force
rpm -ivh https://github.com/zxlhhyccc/abc/raw/master/centos6-7/kernel-3.10.0-229.1.2.el7.x86_64.rpm --force
`````
查看内核
`````
awk -F\' '$1=="menuentry " {print i++ " : " $2}' /etc/grub2.cfg
0 : CentOS Linux 7 Rescue 1f0eb10f866e4eeea5ec2c016d383869 (3.10.0-229.1.2.el7.x86_64)
1 : CentOS Linux (3.10.0-229.1.2.el7.x86_64) 7 (Core)
2 : CentOS Linux (3.10.0-514.2.2.el7.x86_64) 7 (Core)
3 : CentOS Linux (0-rescue-98f15324ee1542fdaf9b60c933ff0e2c) 7 (Core)
``````
设置启动的内核
`````
grub2-set-default `awk -F\' '$1=="menuentry " {print i++ " : " $2}' /etc/grub2.cfg | grep '(3.10.0-229.1.2.el7.x86_64) 7 (Core)'|awk '{print $1}'`
grub2-editenv list #查看确认
reboot 重启
``````
CentOS6和7 更换内核完成一键安装锐速[lotServer]
`````
wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && chmod +x appex.sh && bash appex.sh install
`````
安装完成后检测是否启用
`````
lsmod |grep appex
````````
卸载
`````
wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && chmod +x appex.sh && bash appex.sh uninstall
`````
使用此脚本安装时如遇许可证错误，可尝试使用此命令更新许可证
````
bash /appex/bin/serverSpeeder.sh renewLic
``````
