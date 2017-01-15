# IP Tables[[15]]

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
    
### Connection States[[16]]

    #iptables -A INPUT -p tcp --dport ssh -s 10.10.10.10 -m state --state NEW,ESTABLISHED -j ACCEPT
    #iptables -A OUTPUT -p tcp --sport 22 -d 10.10.10.10 -m state --state ESTABLISHED -j ACCEPT
    
### Accept connections by default

    iptables --policy INPUT ACCEPT
    iptables --policy OUTPUT ACCEPT
    iptables --policy FORWARD ACCEPT
   
### Red Hat Linux firewall[[17]] 

### IPtables Packet Flow Diagram[[18]]

![Iptables.gif](https://www.dropbox.com/s/5gwp8tk1q9hhnr4/Iptables.gif?dl=0&raw=1)

[15]: <http://www.dghost.com/techno/internet/banning-an-entire-country-with-iptablesipset>
[16]: <http://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/>
[17]: <http://oceanpark.com/notes/firewall_example.html>
[18]: <http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#.WG_4SNRACdJ>