# PsExec[[41]]
PsExec is a light-weight telnet-replacement that lets you execute processes on other systems, complete with full interactivity for console applications, without having to manually install client software.

    # The following command launches an interactive command prompt on \\marklap:
    
    psexec \\marklap cmd
    
    # This command executes IpConfig on the remote system with the /all switch, and displays the resulting output locally
    
    psexec \\marklap ipconfig /all
    
    # This command copies the program test.exe to the remote system and executes it interactively
    
    psexec \\marklap -c test.exe
    
    # Specify the full path to a program that is already installed on a remote system if its not on the system's path
    
    psexec \\marklap c:\bin\test.exe
    
    # Run Regedit interactively in the System account to view the contents of the SAM and SECURITY keys
    
    psexec -i -d -s c:\windows\regedit.exe
    
    # To run Internet Explorer as with limited-user privileges use this command
    
    psexec -l -d "c:\program files\internet explorer\iexplore.exe"    

[41]: <https://technet.microsoft.com/en-us/sysinternals/pxexec.aspx>