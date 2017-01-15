# Solaris [[22]]

    ifconfig -a                                 # List of interfaces
    netstat -in                                 # List of interface
    ifconfig -r                                 # Route listing
    ifconfig ethO dhcp                          # Start DHCP client
    ifconfig ethO plumb up ip netmask nmask     # SET IP
    route add default ip                        # Set gateway
    logins -p                                   # List users w/out passwords
    svcs -a                                     # List all services w/ status
    prstat -a                                   # Process listing (top)
    svcadm start ssh                            # Start SSH service
    inetadm -e telnet (-d for disable)          # Enable telnet
    prtconf I grep Memory                       # Total physical memory
    iostat -En                                  # Hard disk size
    showrev -c /usr/bin/bash                    # Information on a binary
    shutdown -i6 -gO -y                         # Restart system
    dfmounts                                    # List clients connected NFS
    smc
    snoop -d int -c pkt # -o results.pcap       # Packet capture
    /etc/vfstab                                 # File system mount table
    /var/adm/logging                            # Login attempt log
    /etc/default/'                              # Default settings
    /etc/system                                 # Kernel modules & config
    /var/adm/messages                           # Syslog location
    /etc/auto_'                                 # Automounter config files
    /etc/inet/ipnodes                           # IPv4/IPv6 host file
    
[22]:<https://www.google.hr/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwiE1be92LDRAhUHkRQKHXnZAx8QFgggMAE&url=https%3A%2F%2Fwatchthestack.files.wordpress.com%2F2015%2F03%2Frtfm-red-team-field-manual.pdf&usg=AFQjCNGEsophTnPPNguco9UBIh0p92db_A&sig2=lEFteRB9djm24jYJoV5iTg>




