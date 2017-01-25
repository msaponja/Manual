# Linux scripting

### Understanding bash scripting[[27]]

### Ping sweep without NMAP [[28]]

    $ for i in `seq 1 255`; do ping -c 1 10.10.10.$i | tr \\n ' ' | awk '/1 received/ {print $2}'; done
    $ for i in {1..254}; do ping -c 1 -W 1 10.1.1.$i | grep 'from'; done

### Fork bomb[[29]]

    $ :(){ :|:& };:     # forkbomb(){ forkbomb | forkbomb & }; forkbomb
    
### Monitor DNS[[30]]
-It takes the IP address or hostname of the DNS server to check. Checks the records defined in the array.

    //Define defaults
    if($_SERVER[argv][1])
    {
    $ns_server = $_SERVER[argv][1];
    } else {
    echo "You need to supply a DNS server to check. Quitting.\n";
    exit;
    }
    $hosts = array("zabbix.com" => "85.113.250.92",
    "php.net" => "69.147.83.197");
    // Do query
    foreach($hosts as $host => $ip)
    {
    $result = shell_exec("dig +time=1 +tries=1 +short @".$ns_server." ".$host);
    if(!preg_match('/'.$ip.'/', $result))
    {
    $failed = TRUE;
    }
    }
    if($failed)
    {
    echo "0\n";
    } else {
    echo "1\n";
    }
    ?>

### Monitoring NTP[[31]]

    #!/usr/local/bin/bash
    #ntptest
    #NTP test scripts for Zabbix monitor. Conditional return
    # of 1=success | 0= for failed response
    HOST_QUERY=$1
    if [`ntpq -pn $HOST_QUERY | grep -E -c '^\*'` -eq 1 ]; then
    #Sync responded, OK
    echo "1"
    else
    echo "0"
    fi
    
    NOTICE: Works with *nix Zabbix Server

### Special shell variables to be aware [[32]]

    $ $*    # Passes in all of the arguments. This is useful for FOR loops
    $ $?    # Gets the error code (exit()) status) of the last program executed
    $ $$    # Gets the PID of the current shell.
    $ $!    # Gets the PID of the last background process
    $ $EUID # Gets the effective UID number of the scripts execution

### Linux Iptables Firewall Shell Script For Standalone Server[[33]]

    #!/bin/bash
    # A Linux Shell Script with common rules for IPTABLES Firewall.
    # By default this script only open port 80, 22, 53 (input)
    # All outgoing traffic is allowed (default - output)
    # -------------------------------------------------------------------------
    # Copyright (c) 2004 nixCraft project <http://cyberciti.biz/fb/>
    # This script is licensed under GNU GPL version 2.0 or above
    # -------------------------------------------------------------------------
    # This script is part of nixCraft shell script collection (NSSC)
    # Visit http://bash.cyberciti.biz/ for more information.
    # -------------------------------------------------------------------------
    IPT="/sbin/iptables"
    SPAMLIST="blockedip"
    SPAMDROPMSG="BLOCKED IP DROP"
    echo "Starting IPv4 Wall..."
    $IPT -F
    $IPT -X
    $IPT -t nat -F
    $IPT -t nat -X
    $IPT -t mangle -F
    $IPT -t mangle -X
    modprobe ip_conntrack
    [ -f /root/scripts/blocked.ips.txt ] && BADIPS=$(egrep -v -E "^#|^$" /root/scripts/blocked.ips.txt)
    PUB_IF="eth0"
    #unlimited
    $IPT -A INPUT -i lo -j ACCEPT
    $IPT -A OUTPUT -o lo -j ACCEPT
    # DROP all incomming traffic
    $IPT -P INPUT DROP
    $IPT -P OUTPUT DROP
    $IPT -P FORWARD DROP
    if [ -f /root/scripts/blocked.ips.txt ];
    then
    # create a new iptables list
    $IPT -N $SPAMLIST
    for ipblock in $BADIPS
    do
       $IPT -A $SPAMLIST -s $ipblock -j LOG --log-prefix "$SPAMDROPMSG"
       $IPT -A $SPAMLIST -s $ipblock -j DROP
    done
    $IPT -I INPUT -j $SPAMLIST
    $IPT -I OUTPUT -j $SPAMLIST
    $IPT -I FORWARD -j $SPAMLIST
    fi
    # Block sync
    $IPT -A INPUT -i ${PUB_IF} -p tcp ! --syn -m state --state NEW  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Drop Sync"
    $IPT -A INPUT -i ${PUB_IF} -p tcp ! --syn -m state --state NEW -j DROP
    # Block Fragments
    $IPT -A INPUT -i ${PUB_IF} -f  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fragments Packets"
    $IPT -A INPUT -i ${PUB_IF} -f -j DROP
    # Block bad stuff
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL ALL -j DROP
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL NONE -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "NULL Packets"
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL NONE -j DROP # NULL packets
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,FIN SYN,FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "XMAS Packets"
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP #XMAS
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags FIN,ACK FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fin Packets Scan"
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags FIN,ACK FIN -j DROP # FIN packet scans
    $IPT  -A INPUT -i ${PUB_IF} -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
    # Allow full outgoing connection but no incomming stuff
    $IPT -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -A OUTPUT -o eth0 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    # Allow ssh
    $IPT -A INPUT -p tcp --destination-port 22 -j ACCEPT
    # allow incomming ICMP ping pong stuff
    $IPT -A INPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    $IPT -A OUTPUT -p icmp --icmp-type 0 -m state --state ESTABLISHED,RELATED -j ACCEPT
    # Allow port 53 tcp/udp (DNS Server)
    $IPT -A INPUT -p udp --dport 53 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
    $IPT -A OUTPUT -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
    $IPT -A INPUT -p tcp --destination-port 53 -m state --state NEW,ESTABLISHED,RELATED  -j ACCEPT
    $IPT -A OUTPUT -p tcp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
    # Open port 80
    $IPT -A INPUT -p tcp --destination-port 80 -j ACCEPT
    ##### Add your rules below ######
    ##### END your rules ############
    # Do not log smb/windows sharing packets - too much logging
    $IPT -A INPUT -p tcp -i eth0 --dport 137:139 -j REJECT
    $IPT -A INPUT -p udp -i eth0 --dport 137:139 -j REJECT
    # log everything else and drop
    $IPT -A INPUT -j LOG
    $IPT -A FORWARD -j LOG
    $IPT -A INPUT -j DROP
    exit 0
[27]: <https://linuxconfig.org/bash-scripting-tutorial>
[28]: <http://www.commandlinefu.com/commands/view/3144/ping-sweep-without-nmap>
[29]: <https://linuxconfig.org/how-to-crash-your-linux-system-with-fork-bomb>
[30]: <https://www.zabbix.com/forum/showpost.php?p=31561&postcount=2>
[31]: <https://www.zabbix.com/forum/showpost.php?p=31549&postcount=1>
[32]: <http://wiki.jaxhax.org/images/9/94/Shell_Scripting_Crash_Course.pdf>
[33]: <https://bash.cyberciti.biz/firewall/linux-iptables-firewall-shell-script-for-standalone-server/>