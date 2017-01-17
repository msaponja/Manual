# Terminal Services[[47]]
Terminal Services provides the ability to host multiple, simultaneous client sessions on Microsoft Windows Server 2003.

### Terminal Services Arhitecture

![aa.gif](https://www.dropbox.com/s/mon59ohqha3p7g8/aa.gif?dl=0&raw=1)

### Start RDP

    1. Create regfile.reg file with following line in it:
    HKEY LOCAL t1ACHINE\SYSTEH\CurrentControlSet \Control\ TerminalService
    2. "fDe~yTSCo~nections"=dword: 00000000
    3. reg import reg file. reg
    4. net start ''terrnservice''
    5. sc config terrnservice start= auto
    6. net start terrnservice
    
### Disable Network Level Authentification, Add Firewall Excpetion

    reg add "HKEY LOCAL t1ACHINE\SYSTEt1\CurentControlSet\Control \Terminal
    Server\WinStations\RDP-TCP" /v UserAuthentication /t REG_DWORD /d "0" /f
    netsh firewall set service type = remotedesktop mode = enable

[47]: <https://technet.microsoft.com/en-us/library/cc755399(v=ws.10).aspx>