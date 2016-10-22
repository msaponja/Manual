Linux anti-forensics
====================

#### Bash History

watch ss -tp                                Network Connections
netstat -ant                                Tcp-connections -anu=udp
netstat -tulpn
lsof -i
smb:// ip /share
share user x.x.x.x c$
smbclient -0 user\\\\ ip \\ share
ifconfig eth# ip I cidr
ifconfig ethO:l ip I cidr
route add default gw gw lp
ifconfig eth# mtu [size]
export l1AC=xx: XX: XX: XX: XX: XX
ifconfig int hw ether t~AC
macchanger -m l1AC int
iwlist int scan
dig -x ip
host ip
host -t SRV service tcp.url.com
dig @ ip domain -t AXrR
host -1 domain namesvr
ip xfrm state list
ip addr add ip I cidr aev ethO
/var/log/messages I grep DHCP
tcpkill host ip and port port
echo "1" /proc/sys/net/ipv4/ip forward
echo ''nameserver x.x.x.x'' /etc7resolv.conf


