# bbr2.0

--------------------

# CentOS
```
wget https://github.com/2444989513/bbr2.0/raw/master/CentOS/kernel-5.4.0_rc6-1.x86_64.rpm
wget https://github.com/2444989513/bbr2.0/raw/master/CentOS/kernel-headers-5.4.0_rc6-1.x86_64.rpm
yum install -y kernel-5.4.0_rc6-1.x86_64.rpm
yum install -y kernel-headers-5.4.0_rc6-1.x86_64.rpm

sudo cat /boot/grub2/grub.cfg | grep menuentry
sudo grub2-set-default 'CentOS Linux (5.4.0-rc6) 7 (Core)'
sudo grub2-editenv list

reboot
uname -r
grub2-mkconfig -o /boot/grub2/grub.cfg

sed -i '/net.core.default_qdisc/d' /etc/sysctl.conf
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
sed -i '/net.ipv4.tcp_congestion_control/d' /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr2" >> /etc/sysctl.conf
sed -i '/net.ipv4.tcp_ecn/d' /etc/sysctl.conf
echo "net.ipv4.tcp_ecn=1" >> /etc/sysctl.conf

reboot

lsmod | grep bbr

```

--------------------

