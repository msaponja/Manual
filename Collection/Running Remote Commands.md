# Running remote commands[[42]]
Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers. They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.

Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter. To find these cmdlets in your session, type:

    Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}

### Start an Interactive Session

To start an interactive session with a single remote computer, we use the Enter-PSSession cmdlet.

    Enter-PSSession Server01
    
### Exit Session

    Exit-PSSession
    
### Running a remote command

To run any command on one or many remote computers, use the Invoke-Command cmdlet. For example, to run a Get-UICulture command on the Server01 and Server02 remote computers, type:

    Invoke-Command -ComputerName Server01, Server02 {Get-UICulture}

### Output example

![Untitled.png](https://www.dropbox.com/s/k545zhqu94vn33c/Untitled.png?dl=0&raw=1)

### Run a script

    Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
    
### Establish a Persistent Connection
Following command creates a remote session on the Server01 computer and another remote session on the Server02 computer. It saves the session objects in the $s variable.

    $s = New-PSSession -ComputerName Server01, Server02
    
following command creates a remote session on the Server01 computer and another remote session on the Server02 computer. It saves the session objects in the $s variable.

    Invoke-Command -Session $s {$h = Get-HotFix}
    
Now you can use the data in the $h variable in subsequent commands, such as the following one. The results are displayed on the local computer.

    Invoke-Command -Session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"}}
    
[42]: <https://msdn.microsoft.com/en-us/powershell/scripting/core-powershell/running-remote-commands>
    
    