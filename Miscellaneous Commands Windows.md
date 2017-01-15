# Miscellaneous commands Windows[[9]]

### Lock Workstation

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

[9]: <https://www.google.hr/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0ahUKEwjhooiG2rrRAhVqJpoKHV7rBgAQFgggMAE&url=https%3A%2F%2Fwatchthestack.files.wordpress.com%2F2015%2F03%2Frtfm-red-team-field-manual.pdf&usg=AFQjCNGEsophTnPPNguco9UBIh0p92db_A&sig2=qjLZXS2m135kgA3_o3kVLw>