# IPv4    

### CLASSFULL IP RANGES [[3]]

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
    - H indicates a bit used for the host ID
    - X indicates a bit without a specified purpose
  
### Reserved ranges [[4]]

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
    
### Subnetting [[5]]

![class_a_subnets.jpg](https://www.dropbox.com/s/i7k6anrqrew7q8h/class_a_subnets.jpg?dl=0&raw=1)

### Calculating subnet range [[6]]

    Address:   192.168.0.1           11000000.10101000.00000000 .00000001
    Netmask:   255.255.255.0 = 24    11111111.11111111.11111111 .00000000
    Wildcard:  0.0.0.255             00000000.00000000.00000000 .11111111
    =>
    Network:   192.168.0.0/24        11000000.10101000.00000000 .00000000       (Class C)
    Broadcast: 192.168.0.255         11000000.10101000.00000000 .11111111
    HostMin:   192.168.0.1           11000000.10101000.00000000 .00000001
    HostMax:   192.168.0.254         11000000.10101000.00000000 .11111110
    Hosts/Net: 254                   (Private Internet)
    
[3]:<https://en.wikipedia.org/wiki/Classful_network>
[4]:<https://en.wikipedia.org/wiki/Reserved_IP_addresses>
[5]:<https://www.tutorialspoint.com/ipv4/ipv4_subnetting.htm>
[6]:<http://jodies.de/ipcalc?host=192.168.0.1&mask1=24&mask2=>