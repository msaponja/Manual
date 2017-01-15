# Brute Forcing Services [[2]]

### Hydra FTP Brute Force

	hydra -l USERNAME -P /usr/share/wordlistsnmap.lst-f 
	192.168.X.XXX ftp -V

### Hydra POP3 Brute Force

	hydra -l USERNAME -P /usr/sha/wordlistsnmap.lst-f 
     192.168.X.XXX pop3 -V
     
### Hydra SMTP Brute Force

	hydra -P /usr/share/wordlistsnmap.lst 192.168.X.XXX smtp -V
	



[2]: <https://highon.coffee/blog/penetration-testing-tools-cheat-sheet/#brute-forcing-services>