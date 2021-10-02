NAT    Network Address Translation
软路由设置端口转发比较简单
 旁路由模式用旁路由分配IP比较好，总之不能和光猫同时分配ip
 拨号设备和负责端口转发和DHCP
 整个内网最好只有一层NAT,只有一台设备负责DHCP

 #### 路由器的两种工作模式
 ac模式：路由器负责拨号
 ap模式：只负责发射无限信号

 软路由网口功能：
 lan口：连接内网设备，分配IP地址(dhcp)
 wan口：连接外网(nat转换),PPPOE拨号

 DDNS    Dynamic Domain Name System

 传输层：(tcp/udp)

会话层，表示层，应用层对于TCP/IP协议来说，可以认为是一层。
