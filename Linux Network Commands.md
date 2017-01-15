# Linux network commands [[1]]

General networking concepts that will help you in troubleshooting networks on Linux.

    $ watch ss -tp                               # Network connections
    $ netstat -ant                               # Tcp connections -anu=udp
    $ netstat -tulpn                             # Connections with PIDs
    $ lsof -i                                    # Established connections
    $ smb:// ip /share                           # Access windows smb share
    $ share user x.x.x.x c$                      # Mount Windows share
    $ smbclient -0 user\\\\ ip \\ share          # SMB connect
    $ ifconfig eth# ip / cidr                    # Set IP and netmask
    $ ifconfig ethO:l ip / cidr                  # Set virtual interface
    $ route add default gw gw_ip                 # Set GW
    $ ifconfig eth# mtu [size]                   # Change MTU size
    $ export MAC=xx: xx: xx: xx: xx: xx          # Change MAC 
    $ ifconfig int hw ether MAC                  # Change MAC
    $ macchanger -m MAC int                      # Backtrack MAC changer
    $ iwlist int scan                            # Built-in wifi scanner
    $ dig -x ip                                  # Domain lookup for IP
    $ host ip                                    # Domain lookup for IP
    $ host -t SRV _ service _tcp.url.com         # Domain SRV lookup
    $ dig @ ip domain -t AXFR                    # DNS Zone Xfer
    $ host -l domain namesvr                     # DNS Zone Xfer
    $ ip xfrm state list                         # Print existing VPN keys
    $ ip addr add ip / cidr dev ethO             # Adds 'hidden' interface
    $ /var/log/messages | grep DHCP              # List DHCP assignments
    $ tcpkill host ip and port port              # Block ip:port
    $ echo "1" /proc/sys/net/ipv4/ip_forward     # Turn on IP Forwarding
    $ echo "nameserver x.x.x.x" /etc/resolv.conf # Add DNS Server

[1]: <http://linux-training.be/linuxnet.pdf>