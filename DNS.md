# DNS

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



