# Windows registry[[56]]    

### Structure of the Windows Registry (hives)

    HKEY_CLASSES_ROOT   # Information stored here ensures that the correct program opens when it is executed in Windows Explorer. 
    HKEY_CURRENT_USER   # Contains configuration information for the user who is currently logged into the system, including user's folders, screen colors, and Control Panel settings
    HKEY_LOCAL_MACHINE  # Contains machine hardware-specific information that the operating system runs on
    HKEY_USERS          # Contains configuration information of all user profiles on the system, which concerns application configurations, and visual settings
    HKEY_CURRENT_CONFIG # Stores information about the systems current configuration. Alias for: HKLM\Config\profile
    
### Autorun locations

    HKLM\Software\Microsoft\Windows\CurrentVersion\Runonce
    HKLM\Software\Microsoft\Windows\CurrentVersion\policies\Explorer\Run
    HKLM\Software\Microsoft\Windows\CurrentVersion\Run
    HKCU\Software\Microsoft\Windows NT\CurrentVersion\Windows\Run
    HKCU\Software\Microsoft\Windows\CurrentVersion\Run
    HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce
    (ProfilePath)\Start Menu\Programs\Startup 
    
### MRU lists

MRU, or 'most recently used' lists contain entries made due to specific actions performed by the user. There are numerous MRU lists located throughout various Registry keys. 
    
    HKCU\Software\Microsoft\Windows\ CurrentVersion\Explorer\RunMRU
    
### UserAssist
The UserAssist key contains two or more subkeys which have long hexadecimal names that appear as globally unique identifiers (GUIDs). Each subkey records values that pertain to specific objects the user has accessed on the system, such as Control Panel applets, shortcut files, programs, etc.
    
    HCU\Software\Microsoft\Windows\CurrentVersion\Explorer\UserAssist

These values however, are encoded using a ROT- 13 encryption algorithm, sometimes known as a Caesar cipher. This particular encryption technique is quite easy to decipher, as each character is substituted with the character 13 spaces away from it in the ASCII table.
With the UserAssist key, a forensic examiner can gain a better understanding of what types of files or applications have been accessed on a particular system.

### Wireless netoworks

    HKLM\SOFTWARE\ Microsoft\WZCSVC\Parameters\Interfaces key        # SSIDs
    HKLM\SYSTEM\ControlSet001\ Services\Tcpip\Parameters\Interfaces\ # flynn-net

### LAN computers

    HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\ComputerDescriptions. # List of devices, including desktop computers, laptops, and printers 
    
### USB Devices
  
    HKLM\SYSTEM\ControlSet00x\Enum\USBSTOR  # Key stores the contents of the product and device ID values of any USB device that has ever been connected to the system
    
### Mounted devices
  
    HKLM\SYSTEM\MountedDevices   # Stores a database of mounted volumes that is used by the NTFS file system
    
### Firefox
Firefox has limited footprints regarding Registry activity. Firefox stores  web history in a history.dat file, which is in ASCII format and plainly visible when opened.

     C:\Documents and Settings\User Profile\Application Data\Mozilla\Firefox\Profiles\x.default\   
    
  
[56]:<http://www.forensicfocus.com/a-forensic-analysis-of-the-windows-registry>