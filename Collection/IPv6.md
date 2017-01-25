# IPv6

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