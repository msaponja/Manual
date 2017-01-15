# Packet Capturing[[14]]

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
    
[14]: <http://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/>




