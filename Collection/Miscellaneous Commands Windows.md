# Miscellaneous commands Windows[[37]]

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

[37]: <https://watchthestack.files.wordpress.com/2015/03/rtfm-red-team-field-manual.pdf>