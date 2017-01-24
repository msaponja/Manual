Manual
======

Table of contents
-----------------

 **Linux**
  
- [Linux Network Commands](#linux-network-commands)
- [Linux System Info]
- [Manipulating files]
- [Linux Misc Commands]
- [Hide Your Tracks]
- [Linux Scripting]
- [IP Tables]
- [Automatically run commands over SSH on many servers]
- [CHKCONFIG]
- [Kali Linux Commands]
- [Solaris]
  
**Windows**

- 	[Windows Versions]
- 	[Startup Directories]
- 	[Useful Run Commands]
- 	[Windows System Info Commands]
- 	[Windows Net_Domain Commands]
-	[Running Remote Commands]
- 	[Windows Network Commands]
- 	[Hidden tools in Command Line]
- 	[Miscellaneous Commands Windows]
- 	[PsExec]
- 	[Terminal Services]
- 	[WMIC]
- 	[Powershell]
- 	[Windows Registry]

**Networking**

- 	[Common ports]
- 	[IPv4]
-	[IPv6]
-	[Cisco commands]
-	[SNMP]
-	[Packet Capturing]
-	[DNS]
-	[VPN]

**PenTesting**

-	[Brute Forcing Services]
-	[Exploit Research]
-	[Metasploit]
-	[Password Cracking]

**Slike/Tablice**

-	[Figure: Driver.csv]
-	[Figure: IPtables Packet Flow Diagram]
-	[Figure: Subnetting]
- 	[Figure: SNMP Concept]
- 	[Figure: Terminal Services Arhitecture]
-	[Table: Common ports]

**Literatura**

-	[Literatura]

Linux Network Commands
----------------------

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

[26]: <http://linux-training.be/linuxnet.pdf>


# Linux system info [[34]]
--------------------------

Most common commands used to check information and configuration details about various hardware peripherals and devices.

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

# Linux Misc Commands [[25]]
----------------------------

Search commands

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

# Manipulating files [[35]]
---------------------------

Most frequently used Linux Commands for manipulating files.

    $ cp file1 file         # Copies the contents of file1 into file2. If file2 does not exist, it is created
    $ cp -i file1 file2     # If file2 exists, the user is prompted before it is overwritten with the contents of file1
    $ mv file1 file2        # If file2 does not exist, then file1 is renamed file2. If file2 exists, its contents are replaced with the contents of file1
    $ rm file1 file2        # Deletes file1 and file2
    $ mkdir directory       # Create directories
[35]: <http://linuxcommand.org/lts0050.php>

 # Linux Misc Commands [[25]]
 ----------------------------

Search commands

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

# Hide Your Tracks [[11]]
-------------------------

### Meterpreter

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
    
### The logs[[12]]

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

# Linux scripting
-----------------

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

# IP Tables[[13]]
-----------------

### Create a set named geoset

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
    
### Connection States[[14]]

    #iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT
    #iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
    
### Accept connections by default

    iptables --policy INPUT ACCEPT
    iptables --policy OUTPUT ACCEPT
    iptables --policy FORWARD ACCEPT
   
### Red Hat Linux firewall[[15]] 

### IPtables Packet Flow Diagram[[16]]

![Iptables.gif](https://www.dropbox.com/s/5gwp8tk1q9hhnr4/Iptables.gif?dl=0&raw=1)

[13]: <http://www.dghost.com/techno/internet/banning-an-entire-country-with-iptablesipset>
[14]: <http://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/>
[15]: <http://oceanpark.com/notes/firewall_example.html>
[16]: <http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#.WG_4SNRACdJ>

# Example [[1]]
---------------

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

# CHKCONFIG[[3]]
----------------

The chkconfig utility is a command-line tool that allows you to specify in which runlevel to start a selected service, as well as to list all available services along with their current setting.

    $ chkconfig --list                              # Listing the Services
    $ chkconfig --list service_name                 # Display the current settings for a selected service only
    $ chkconfig service_name on                     # Enabling a Service
    $ chkconfig service_name on --level runlevels   # To enable a service in certain runlevels only
    $ chkconfig service_name off                    # Disabling a Service
    
[3]: <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-services-chkconfig.html>

# Kali Linux Commands[[24]]
---------------------------

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

# Using the PHP pfSense Shells [[49]]
-------------------------------------

Using the PHP pfSense shell allows configuration of the config.xml file directly without needing to use the webConfigurator.

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

# Solaris [[45]]
----------------

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






