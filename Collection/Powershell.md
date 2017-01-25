# Powershell[[40]]    

    #	                                # Comment / Remark
    $_	                                # The current pipeline object
    $variable = "value"	                # Define a variable  also: ${n!a#me} = "value"
    %	                                # Alias for ForEach-Object
    --%	                                # Stop parsing input
    & (call)	                        # Run a command, script or function
    . (source)	                        # Run a command script in the current shell
    ?           	                    # Alias for Where-Object
    @(...)	                            # Force an expression to be evaluated as an array
    #NAME?      	                    # Format operator
    Active Directory	                # Account, Computer, Group and User cmdlets
    Add-Computer	                    # Add a computer to the domain
    Add-Content	                        # Add to the content of the item
    Add-History	                        # Add entries to the session history
    Add-Member	                        # Add a member to an instance of a PowerShell object
    Add-PsSnapIn	                    # Add snap-ins to the console
    Add-Type    	                    # Add a .NET Framework type to a PowerShell session
    Add-WindowsFeature	                # Install roles, role services, and features
    Backup-GPO	                        # Backup group policy objects (GPOs)
    Backup-GPO	                        # Backup group policy objects (GPOs)
    Begin	                            # Function BEGIN block
    BITS	                            # Background Intelligent Transfer Service cmdlets
    Break	                            # Exit a program loop
    Catch	                            # Handle a terminating error within a scriptblock
    Checkpoint-Computer	                # Create a system restore point (XP)
    Checkpoint-Web	                    # Create a checkpoint for an IIS web app
    Clear-Content	                    # Remove content from a file/item
    Clear-EventLog	                    # Delete all entries from an event log
    Clear-History	                    # Delete entries from the session history
    Clear-Host	                        # Clear the screen
    Clear-Host	                        # Clear the screen
    Clear-Item	                        # Remove content from a variable or an alias
    Clear-ItemProperty	                # Remove the property value from a property
    Clear-Variable	                    # Remove the value from a variable
    Compare-Object	                    # Compare the properties of objects
    Compare-Object	                    # Compare the properties of objects
    Complete-Transaction                # Commit the transaction
    Compress-Archive                    # Create a new archive/zipped file [PS 5+]
    Connect-WSMan	                    # Connect to the WinRM service on a remote computer
    Continue	                        # Skip just this iteration of a loop
    ConvertFrom-CSV	                    # Convert object properties (in CSV format) into CSV objects
    ConvertFrom-SecureString	        # Convert a secure string into an encrypted standard string
    ConvertFrom-StringData	            # Convert a here-string into a hash table
    Convert-Path	                    # Convert a ps path to a provider path
    ConvertTo-CSV	                    # Convert .NET Framework objects into CSV variable
    ConvertTo-Html	                    # Convert the input into an HTML table
    ConvertTo-SecureString	            # Convert an encrypted standard string into a secure string
    ConvertTo-Xml	                    # Convert the input into XML
    Copy-Item	                        # Copy an item from a namespace location
    Copy-ItemProperty	                # Copy a property along with it's value
    Debug-Process	                    # Attach a debugger to a running process
    Disable-ComputerRestore	            # Disable System Restore on a drive
    Disable-PSBreakpoint	            # Disable a breakpoint in the current console
    Disable-PSRemoting	                # Disable remote session configuration on the local computer
    Disable-PSSessionConfiguration  	#  Disable session configurations on the local computer
    Disable-WSMAnCredSSP 	            # Disable Credential Security Service Provider (SSP) authentication
    Disconnect-WSMan	                # Disconnect from the WinRM service on a remote
    Do	                                # Loop while a condition is True
    Enable-ComputerRestore	            # Enable System Restore on a drive
    Enable-PSBreakpoint	                # Enable a breakpoint in the current console
    Enable-PSRemotRemoting	            # Run PowerShell commands on remote computers
    Enable-PSSessionConfiguration	    # Enable session configurations on the local computer
    Enable-WSManCredSSP 	            # Enable Credential SSP authentication
    End	                                # Function END block
    Enter-PSSessio	                    # Start an interactive session with a remote computer
    Exit-PSSession	                    # Exit PowerShell (or exit a script)
    Exit-PSSession	                    # End an interactive session with a remote computer
    Expand-Archive	                    # Extract files from an archive (zipped) file [PS
    Export-Alias	                    # Export an alias list to a file
    Export-Clixml	                    # Produce a clixml representation of PowerShell ob
    Export-Console	                    # Export console configuration to a file
    Export-Counter	                    # Export Performance Counter data to log files
    Export-Csv	                        # Export to Comma Separated Values (spreadsheet)
    Export-FormatData	                # Save formatting data from the current session
    Export-ModuleMember	                # Export specific module members
    Export-PSSession	                # Import commands and save them in a PowerShell mo
    For	                                # Loop through items that match a condition
    ForEach	                            # Loop through each item in a collection
    ForEach method	                    # Loop through each item in a collection
    ForEach-Object	                    # Reach  Loop through each item in the pipeline ( % )
    Format-Custom	                    # Format output using a customized view
    Format-List	                        # Format output as a list of properties, each on a
    Format-Table	                    # Format output as a table
    Format-Wide	                        # Format output as a table listing one property on
    Get-Acl	                            # Get permission settings for a file or registry ke
    Get-Alias	                        # Return alias names for Cmdlets
    Get-AuthenticonSignature	        # Get the signature object associated with a file
    Get-ChildItem	                    # Get child items (contents of a folder or registry)
    Get-Command	                        # Get basic information about cmdlets
    Get-Command	                        # Retrieve basic information about a command
    Get-ComputerRestorePoint	        # Get the restore points on the local computer
    Get-Content 	                    # Get content from item (specific location)
    Get-Counter	                        # Get performance counter data
    Get-Credential	                    # Get a security credential (username/password)
    Get-Culture	                        # Get region information (language and keyboard la
    Get-Date	                        # Get current date and time
    Get-DscConfiguration	            # Get the current config. of a node
    Get-DscLocalConfigurationManager	# Get Local Config Manager settings
    Get-DscResource	                    # Get Desired State Config. resources from a compute
    Get-Event	                        # Get events in the PowerShell event queue
    Get-Eventlog	                    # Get event log data (2003)
    Get-EventSubscriber	                # Get event subscribers
    Get-ExecutionPolicy	                # Get the execution policy for the shell
    Get-FormatData	                    # Get the formatting data in the current session
    Get-Help	                        # Open the help file
    Get-History  	                    # Get a listing of the session history
    Get-Host	                        # Get host information (PowerShell Version and Region)
    Get-HotFix	                        # Get Installed hotfixes
    Get-Item	                        # Get a file/registry object (or any other namespa
    Get-Item	                        # Get a file object or get a registry (or other names)
    Get-ItemProperty	                # Retrieve the properties of an object
    Get-Job	                            # Get PowerShell background jobs that are running
    Get-Location	                    # Get and display the current location
    Get-Member	                        # Enumerate the properties of an object
    Get-Module	                        # Get the modules imported to the session
    Get-Pfxcertificate	                # Get pfx certificate information
    Get-Process	                        # Get a list of processes on a machine
    Get-PSBreakpoint	                # Get the currently set breakpoints
    Get-PSDrive	                        # Get drive information (DriveInfo)
    Get-PSProvider	                    # Get information for the specified provider
    Get-PSSession	                    # Get the PSSessions in the current session
    Get-PSSessionConfiguration	        # Get the registered PS session configuration
    Get-PsSnapin	                    # List PowerShell snap-ins on this computer
    Get-Random	                        # Get a random number
    Get-Service	                        # Get a list of services
    Get-Tracesource	                    # Get components that are instrumented for tracing
    Get-Transaction	                    # Get information about the active transaction
    Get-Uiculture	                    # Get the ui culture information
    Get-Unique	                        # Get the unique items in a collection
    Get-Variable	                    # Get a PowerShell variable
    Get-WebApplicationMonitoringStatus	# Get the monitoring status of web apps
    Get-WindowsFeature	                # Retrieve roles, role services, and features
    Get-WinEvent	                    # Get event log data (Vista+)
    Get-WmiObject	                    # Get WMI class information
    Get-WSManCredSSP  	                # Get the Credential SSP configuration
    Get-WSManInstance 	                # Display management information (XML or value)
    Group-Object	                    # Group objects that contain the same value
    if	                                # Conditionally perform a command
    Import-Alias	                    # Import an alias list from a file
    Import-Clixml	                    # Import a clixml file and rebuild the PS object
    Import-Counter	                    # Import performance counter log files
    Import-Csv	                        # Take values from a CSV list and send objects dow
    Import-GPO	                        # Import Group Policy settings into a specified GPO
    Import-Module	                    # Add a module to the session
    Import-PSSession	                # Import commands from another session
    Invoke-Command	                    # Run commands on local and remote computers
    Invoke-Command	                    # Run command
    Invoke-Express	                    # Run a PowerShell expression
    Invoke-History	                    # Invoke a previously executed Cmdlet
    Invoke-Item	                        # Invoke an executable or open a file (START)
    Invoke-WmiMethod	                # Call WMI methods
    Invoke-WSManAction	                # Invoke an action on a specified object
    Job Trigger cmdlets	                # Get/Set Scheduled job triggers
    Join-Path	                        # Combine a path and child-path
    Limit-EventLog	                    # Limit the size of the event log
    Measure-Command	                    # Measure running time
    Measure-Object	                    # Measure the properties of an object
    Move-Item	                        # Move an item from one location to another
    Move-ItemProperty	                # Move a property from one location to another
    New-Alias	                        # Create a new alias.
    New-DSCCheckSum	                    # Create checksum files for DSC docs/resources
    New-Event	                        # Create a new event
    New-Eventlog	                    # Create a new event log and a new event source
    New-Item   	                        # Create a new item in a namespace
    New-ItemProperty	                # Set a new property
    New-Module	                        # Create a new dynamic module (only in memory)
    New-Object	                        # Create a new .Net object
    New-PSDrive	                        # Create a mapped network drive
    New-PSSession	                    # Create a persistent connection to a local or remote
    New-PSSessionOption	                # Advanced options for a PSSession
    New-Service	                        # Create a new service
    New-Timespan	                    # Create a timespan object
    New-Variable	                    # Create a new variable
    New-WebServiceProxy	                # Create a Web service proxy object
    New-WSManInstance 	                # Create a new instance of a management resource
    New-WSManSessionOption 	            # Options for WSMan commands
    Out-Default	                        # Send output to default
    Out-File	                        # Send output to a file
    Out-GridView	                    # Send output to an interactive table
    Out-Host	                        # Send output to the host
    Out-Null	                        # Send output to null
    Out-Printer	                        # Send the output to a printer
    Out-String	                        # Send objects to the host as strings
    Param	                            # Script Parameters
    Pause	                            # Pause and display the message "Press Enter to continue"
    Pop-Location	                    # Set the current working location from the stack
    Pop-Location	                    # Set the current working location from the stack
    Powershell	                        # Launch a PowerShell session
    Process	                            # Function PROCESS block
    Push-Location	                    # Push a location to the stack
    Push-Location	                    # Push a location to the stack
    Quest AD 	                        # Read and write to Active Directory
    Read-Host	                        # Read a line of input from the host console
    Read-Host	                        # Read a line of input from the host console
    Receive-Job	                        # Get PowerShell background job results
    Register-EngineEvent 	            # Subscribe to PowerShell events
    Register-ObjectEvent   	            # Subscribe to .NET events
    Register-PSSessionConfiguration 	# Create and register a new PS session confi
    Register-WmiEvent	                # Subscribe to a WMI event
    Remove-Computer	                    # Remove the local computer from a workgroup or doma
    Remove-Event	                    # Delete events from the event queue
    Remove-EventLog	                    # Delete an event log
    Remove-Item  D	                    # se/rd/rm/rmdir   Delete an item
    Remove-Item  r	                    # erase/rd/ri/rmdir   Remove an item
    Remove-Item  r	                    # erase/rd/ri/rmdir   Remove an item
    Remove-ItemProperty	                # Remove a property and its value
    Remove-Job	                        # Delete a PowerShell background job
    Remove-Module	                    # Remove a module from the current session
    Remove-PSBreakpoint 	            # Delete breakpoints from the current console
    Remove-PSDrive	                    # Remove a provider/drive from its location
    Remove-PSSession	                # Close PowerShell sessions
    Remove-PSSnapin	                    # Remove PowerShell snap-ins from the console
    Remove-Variable	                    # Remove a variable and its value
    Remove-Windows	                    # Remove roles, role services, and features
    Remove-WmiObject	                # Delete an instance of a WMI class
    Remove-WSManInstance    	        # Delete a management resource instance
    Rename-Item	                        # Change the name of an existing item
    Rename-ItemProperty	                # Rename a property of an item
    Rename-ItemProperty	                # Renames a property at its location
    Reset-Computer	                    # Password Reset the machine account password for the computer
    Resolve-Path	                    # Resolves the wildcards in a path
    Restart-Computer	                # Restart the operating system on a computer
    Restart-Service	                    # Stop and then restart a service
    Restore-Computer	                # Restore the computer to a previous state
    Restore-GPO	                        # Restore one or all GPOs from a GPO backup
    Resume-Service	                    # Resume a suspended service
    Return	                            # Exit the current scope, (function, script, or script block)
    Run/Call	                        # Run a command (call operator)
    Scheduler 	                        # Get/Set scheduled jobs
    Select-Object	                    # Select properties of objects
    Select-Object	                    # Select properties of objects
    Select-String	                    # Search through strings or files for patterns
    Select-XML	                        # Find text in an XML string or document
    Send-MailMessage	                # Send an email message
    Send-MailMessage	                # Send an email message
    Set-Acl	                            # Set permissions
    Set-Alias	                        # Create or change an alias
    Set-AuthenticodeSignature	        # Place a signature in a .ps1 script or other file
    Set-Content	                        # Set content in the item (specific location)
    Set-Date	                        # Set system time on the host system
    Set-ExecutionPolicy	                # Change the execution policy (user preference)
    Set-Item	                        # Change the value of an item
    Set-ItemProperty	                # Set a property at the specified location to a specified value
    Set-Location	                    # Set the current working location
    Set-Location	                    # Set the current working location
    Set-PSBreakpoint	                # Set a breakpoint on a line, command, or variable
    Set-PSdebug	                        # Turn script debugging on or off
    Set-PSSessionConfiguration	        # Change properties of a registered session config
    Set-Service	                        # Change the start mode/properties of a service
    Set-StrictMode	                    # Enforce coding rules in expressions & scripts
    Set-Tracesource	                    # Trace a PowerShell component
    Set-Variable	                    # Set a variable and a value
    Set-WmiInstance	                    # Create or update an instance of an existing WMI class
    Set-WSManInstance	                # Modify the management information related to a resource
    Set-WSManQuickConfig	            # Configure the local computer for remote management
    Show-EventLog	                    # Display an event log
    Sort-Object	                        # Sort objects by property value
    Sort-Object	                        # Sort objects by property value
    Split-Path	                        # Return part of a path
    Start-DscConfiguration	            # Apply Desired State config to nodes
    Start-Job	                        # Start a PowerShell background job
    Start-Process	                    # Start one or more processes
    Start-Service	                    # Start a stopped service
    Start-Sleep	                        # Suspend shell, script, or runspace activity
    Start-Transaction	                # Start a new transaction
    Start-Transcript	                # Start a transcript of a command shell session
    Stop-Computer	                    # Stop (shut down) a computer
    Stop-Job	                        # Stop a PowerShell background job
    Stop-Process	                    # Stop a running process
    Stop-Process	                    # Stop a running process
    Stop-Service	                    # Stop a running service
    Stop-Transcript	                    # Stop the transcription process
    Suspend-Service	                    # Suspend a running service
    Switch	                            # Multiple if statements
    Tee-Object	                        # Send input objects to two places
    Test-ComputerSecureChannel 	        # Test and repair the secure channel to the domain
    Test-Connection	                    # Ping one or more computers
    Test-Path	                        # Return true if the path exists, otherwise return false
    Test-WSMan	                        # Test if a computer is setup to receive remote command
    Trace-Command	                    # Trace an expression or command
    Trap	                            # Handle a terminating error
    Try ... Catch	                    # Handle a terminating error within a scriptblock
    Unblock-File	                    # Unblock files downloaded from the Internet
    Undo-Transaction	                # Roll back a transaction
    Unregister-Event	                # Cancel an event subscription
    Unregister-PSSessionConfiguration	# Configuration  Delete registered PS session configuration
    Update-Formatdata	                # Update and append format data files
    Update-Help	                        # Download and install help files
    Update-List	                        # Add and remove items from a collection
    Update-TypeData	                    # Update extended type configuration
    Update-Typedata	                    # Update the current extended type configuration
    Use-Transaction	                    # Add a command or expression to the transaction
    Wait-Event	                        # Wait until a particular event is raised
    Wait-Job	                        # Wait for a background job
    Wait-Process	                    # Wait for a process to stop
    Where method	                    # Filter objects from a collection
    Where-Object	                    # Filter the objects passed along the command pipeline
    Where-Object	                    # Filter input from the pipeline
    While	                            # Loop while a condition is True
    Write-Debug	                        # Write a debug message to the host display
    Write-Error	                        # Write an object to the error pipeline
    Write-EventLog	                    # Write an event to an event log
    Write-Host  	                    # Display text on screen
    Write-Host	                        # Write customized output to the host/screen
    Write-Output	                    # Write an object to the pipeline
    Write-Progress	                    # Display a progress bar
    Write-Verbose	                    # Write a string to the host's verbose display
    Write-Warning	                    # Write a string in reverse video to the display
    Zipfile	                            # Compress or Extract zip files

[40]:<http://ss64.com/ps/>
