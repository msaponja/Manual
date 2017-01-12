# Powershell[[13]]    

    #	            # Comment / Remark
    $_	            # The current pipeline object
    $variable = "v	# Define a variable  also: ${n!a#me} = "value"
    %	            # Alias for ForEach-Object
    --%	            # Stop parsing input
    & (call)	    # Run a command, script or function
    . (source)	    # Run a command script in the current shell
    ?           	# Alias for Where-Object
    @(...)	        # Force an expression to be evaluated as an array
    #NAME?      	# Format operator
    Active Directo	# Account, Computer, Group and User cmdlets
    Add-Computer	# Add a computer to the domain
    Add-Content	    # ac   Add to the content of the item
    Add-History	    # Add entries to the session history
    Add-Member	    # Add a member to an instance of a PowerShell obje
    Add-PsSnapIn	# asnp   Add snap-ins to the console
    Add-Type    	# Add a .NET Framework type to a PowerShell session
    Add-WindowsFea	# Install roles, role services, and features
    Backup-GPO	    # Backup group policy objects (GPOs)
    Backup-GPO	    # Backup group policy objects (GPOs)
    Begin	        # Function BEGIN block
    BITS	        # Background Intelligent Transfer Service cmdlets
    Break	        # Exit a program loop
    Catch	        # Handle a terminating error within a scriptblock
    Checkpoint-Com	# Create a system restore point (XP)
    Checkpoint-Web	# ationMonitoring Create a checkpoint for an IIS web app
    Clear-Content	# clc   Remove content from a file/item
    Clear-EventLog	# Delete all entries from an event log
    Clear-History	# clhy   Delete entries from the session history
    Clear-Host	    # r/cls  Clear the screen
    Clear-Host	    # cls  Clear the screen
    Clear-Item	    # li   Remove content from a variable or an alias
    Clear-ItemProp	# clp   Remove the property value from a property
    Clear-Variable	# clv   Remove the value from a variable
    Compare-Object	# compare   Compare the properties of objects
    Compare-Object	# compare Compare the properties of objects
    Complete-Trans	# Commit the transaction
    Compress-Archi	# Create a new archive/zipped file [PS 5+]
    Connect-WSMan	# Connect to the WinRM service on a remote computer
    Continue	    # Skip just this iteration of a loop
    ConvertFrom-CSV	# Convert object properties (in CSV format) into C
    ConvertFrom-SecureString	# ring   Convert a secure string into an encrypted standa
    ConvertFrom-St	# Convert a here-string into a hash table
    Convert-Path	# Convert a ps path to a provider path
    ConvertTo-CSV	# Convert .NET Framework objects into CSV variable
    ConvertTo-Html	# Convert the input into an HTML table
    ConvertTo-Secu	#  Convert an encrypted standard string into a secu
    ConvertTo-Xml	# Convert the input into XML
    Copy-Item	    # Copy an item from a namespace location
    Copy-ItemPrope	# Copy a property along with it's value
    Debug-Process	# Attach a debugger to a running process
    Disable-Comput	# ore    Disable System Restore on a drive
    Disable-PSBrea	# dbp   Disable a breakpoint in the current console
    Disable-PSRemo	# Disable remote session configuration on the loc
    Disable-PSSess	# figuration  Disable session configurations on the local
    Disable-WSManC	# Disable Credential Security Service Provider (
    Disconnect-WSM	# Disconnect from the WinRM service on a remote
    Do	            # Loop while a condition is True
    Enable-Compute	# Enable System Restore on a drive
    Enable-PSBreak	# Enable a breakpoint in the current console
    Enable-PSRemot	# Run PowerShell commands on remote computers
    Enable-PSSessi	# Enable session configurations on the local c
    Enable-WSManCr	# Enable Credential SSP authentication
    End	            # Function END block
    Enter-PSSessio	# Start an interactive session with a remote comput
    Exit-PSSession	# Exit  Exit PowerShell (or exit a script)
    Exit-PSSession	# End an interactive session with a remote computer
    Expand-Archive	# Extract files from an archive (zipped) file [PS
    Export-Alias	# Export an alias list to a file
    Export-Clixml	# Produce a clixml representation of PowerShell ob
    Export-Console	# Export console configuration to a file
    Export-Counter	# Export Performance Counter data to log files
    Export-Csv	    # Export to Comma Separated Values (spreadsheet)
    Export-FormatD	# Save formatting data from the current session
    Export-ModuleM	# Export specific module members
    Export-PSSessi	# Import commands and save them in a PowerShell mo
    For	            # Loop through items that match a condition
    ForEach	        # Loop through each item in a collection
    ForEach method	# Loop through each item in a collection
    ForEach-Object	# Reach  Loop through each item in the pipeline ( % )
    Format-Custom	# Format output using a customized view
    Format-List	    # Format output as a list of properties, each on a
    Format-Table	# Format output as a table
    Format-Wide	    # Format output as a table listing one property on
    Get-Acl	        # Get permission settings for a file or registry ke
    Get-Alias	    # Return alias names for Cmdlets
    Get-Authentico	# ature  Get the signature object associated with a file
    Get-ChildItem	# ls/gci Get child items (contents of a folder or registry
    Get-ChildItem	# ls/gci Get child items (contents of a folder or registry
    Get-ChildItem	# ls/gci Get child items (contents of a folder or registry
    Get-Command	    # Get basic information about cmdlets
    Get-Command	    # Retrieve basic information about a command
    Get-ComputerRe	# Get the restore points on the local computer
    Get-Content ca	# Get content from item (specific location)
    Get-Counter	    # Get performance counter data
    Get-Credential	# Get a security credential (username/password)
    Get-Culture	    # Get region information (language and keyboard la
    Get-Date	    # Get current date and time
    Get-DscConfigu	# Get the current config. of a node
    Get-DscLocalCo	# ationManager   Get Local Config Manager settings
    Get-DscResourc	# Get Desired State Config. resources from a compute
    Get-Event	    # Get events in the PowerShell event queue
    Get-Eventlog	# Get event log data (2003)
    Get-EventSubsc	# Get event subscribers
    Get-ExecutionP	# Get the execution policy for the shell
    Get-FormatData	# Get the formatting data in the current session
    Get-Help	    # Open the help file
    Get-History  	# Get a listing of the session history
    Get-Host	    # Get host information (PowerShell Version and Regio
    Get-HotFix	    # Get Installed hotfixes
    Get-Item	    # Get a file/registry object (or any other namespa
    Get-Item	    # Get a file object or get a registry (or other names
    Get-ItemProper	# Retrieve the properties of an object
    Get-Job	        # Get PowerShell background jobs that are running
    Get-Location	# Get and display the current location
    Get-Member	    # Enumerate the properties of an object
    Get-Module	    # Get the modules imported to the session
    Get-Pfxcertifi	# Get pfx certificate information
    Get-Process	    # Get a list of processes on a machine
    Get-PSBreakpoi	# Get the currently set breakpoints
    Get-PSDrive	    # Get drive information (DriveInfo)
    Get-PSProvider	# Get information for the specified provider
    Get-PSSession	# Get the PSSessions in the current session
    Get-PSSessionC	# Get the registered PS session configuration
    Get-PsSnapin	# List PowerShell snap-ins on this computer
    Get-Random	    # Get a random number
    Get-Service	    # Get a list of services
    Get-Tracesourc	# Get components that are instrumented for tracing
    Get-Transactio	# Get information about the active transaction
    Get-Uiculture	# Get the ui culture information
    Get-Unique	    # Get the unique items in a collection
    Get-Variable	# Get a PowerShell variable
    Get-WebApplica	# Get the monitoring status of web apps
    Get-WindowsFea	# Retrieve roles, role services, and features
    Get-WinEvent	# Get event log data (Vista+)
    Get-WmiObject	# Get WMI class information
    Get-WSManCredS	# Get the Credential SSP configuration
    Get-WSManInsta	# Display management information (XML or value)
    Group-Object	# Group objects that contain the same value
    if	            # Conditionally perform a command
    Import-Alias	# ipal   Import an alias list from a file
    Import-Clixml	# Import a clixml file and rebuild the PS object
    Import-Counter	# Import performance counter log files
    Import-Csv	    # Take values from a CSV list and send objects dow
    Import-GPO	    # Import Group Policy settings into a specified GPO
    Import-Module	# Add a module to the session
    Import-PSSessi	# Import commands from another session
    Invoke-Command	# Run commands on local and remote computers
    Invoke-Command	# Run command
    Invoke-Express	# Run a PowerShell expression
    Invoke-History	# Invoke a previously executed Cmdlet
    Invoke-Item	    # Invoke an executable or open a file (START)
    Invoke-WmiMeth	# Call WMI methods
    Invoke-WSManAc	# Invoke an action on a specified object
    Job Trigger cm	# Get/Set Scheduled job triggers
    Join-Path	    # Combine a path and child-path
    Limit-EventLog	# Limit the size of the event log
    Measure-Comman	# Measure running time
    Measure-Object	# Measure the properties of an object
    Move-Item	    # Move an item from one location to another
    Move-ItemPrope	# Move a property from one location to another
    New-Alias	    # Create a new alias.
    New-DSCCheckSu	# Create checksum files for DSC docs/resources
    New-Event	    # Create a new event
    New-Eventlog	# Create a new event log and a new event source
    New-Item   md/	# Create a new item in a namespace
    New-ItemProper	# Set a new property
    New-Module	    # Create a new dynamic module (only in memory)
    New-Object	    # Create a new .Net object
    New-PSDrive	    # Create a mapped network drive
    New-PSSession	# Create a persistent connection to a local or remote
    New-PSSessionO	# Advanced options for a PSSession
    New-Service	    # Create a new service
    New-Timespan	# Create a timespan object
    New-Variable	# Create a new variable
    New-WebService	# Create a Web service proxy object
    New-WSManInsta	# Create a new instance of a management resource
    New-WSManSessi	# Options for WSMan commands
     Out-Default	# Send output to default
    Out-File	    # Send output to a file
    Out-GridView	# Send output to an interactive table
    Out-Host	    # Send output to the host
    Out-Null	    # Send output to null
    Out-Printer	    # Send the output to a printer
    Out-String	    # Send objects to the host as strings
    Param	        # Script Parameters
    Pause	        # Pause and display the message "Press Enter to continue"
    Pop-Location	# Set the current working location from the stack
    Pop-Location	# Set the current working location from the stack
    Powershell	    # Launch a PowerShell session
    Process	        # Function PROCESS block
    Push-Location	# Push a location to the stack
    Push-Location	# Push a location to the stack
    Quest AD cmdle	# Read and write to Active Directory
    Read-Host	    # Read a line of input from the host console
    Read-Host	    # Read a line of input from the host console
    Receive-Job	    # Get PowerShell background job results
    Register-Engin	# Subscribe to PowerShell events
    Register-Objec	# Subscribe to .NET events
    Register-PSSes	# Create and register a new PS session confi
    Register-WmiEv	# Subscribe to a WMI event
    Remove-Compute	# Remove the local computer from a workgroup or doma
    Remove-Event	# Delete events from the event queue
    Remove-EventLo	# Delete an event log
    Remove-Item  D	# se/rd/rm/rmdir   Delete an item
    Remove-Item  r	# erase/rd/ri/rmdir   Remove an item
    Remove-Item  r	# erase/rd/ri/rmdir   Remove an item
    Remove-ItemPro	# Remove a property and its value
    Remove-Job	    # Delete a PowerShell background job
    Remove-Module	# Remove a module from the current session
    Remove-PSBreak	# Delete breakpoints from the current console
    Remove-PSDrive	# Remove a provider/drive from its location
    Remove-PSSessi	# Close PowerShell sessions
    Remove-PSSnapi	# Remove PowerShell snap-ins from the console
    Remove-Variabl	# Remove a variable and its value
    Remove-Windows	# Remove roles, role services, and features
    Remove-WmiObje	# rwmi   Delete an instance of a WMI class
    Remove-WSManIn	# Delete a management resource instance
    Rename-Item	    # Change the name of an existing item
    Rename-ItemPro	# Rename a property of an item
    Rename-ItemPro	# Renames a property at its location
    Reset-Computer	# ePassword Reset the machine account password for the co
    Resolve-Path	# Resolves the wildcards in a path
    Restart-Comput	# Restart the operating system on a computer
    Restart-Servic	# Stop and then restart a service
    Restore-Comput	# Restore the computer to a previous state
    Restore-GPO	    # Restore one or all GPOs from a GPO backup
    Resume-Service	# Resume a suspended service
    Return	        # Exit the current scope, (function, script, or sc
    Run/Call	    # Run a command (call operator)
    Scheduler cmdl	# Get/Set scheduled jobs
    Select-Object	# Select properties of objects
    Select-Object	# Select properties of objects
    Select-String	# Search through strings or files for patterns
    Select-XML	    # Find text in an XML string or document
    Send-MailMessa	# Send an email message
    Send-MailMessa	# Send an email message
    Set-Acl	        # Set permissions
    Set-Alias	    # Create or change an alias
    Set-Authentico	# Place a signature in a .ps1 script or other file
    Set-Content	    # Set content in the item (specific location)
    Set-Date	    # Set system time on the host system
    Set-ExecutionP	# Change the execution policy (user preference)
    Set-Item	    # Change the value of an item
    Set-ItemProper	# Set a property at the specified location to a speci
    Set-Location	# Set the current working location
    Set-Location	# Set the current working location
    Set-PSBreakpoi	# Set a breakpoint on a line, command, or variable
    Set-PSdebug	    # Turn script debugging on or off
    Set-PSSessionC	# Change properties of a registered session confi
    Set-Service	    # Change the start mode/properties of a service
    Set-StrictMode	# Enforce coding rules in expressions & scripts
    Set-Tracesourc	# Trace a PowerShell component
    Set-Variable	# Set a variable and a value
    Set-WmiInstanc	# Create or update an instance of an existing WMI c
    Set-WSManInsta	# Modify the management information related to a r
    Set-WSManQuick	# Configure the local computer for remote manageme
    Show-EventLog	# Display an event log
    Sort-Object	    # Sort objects by property value
    Sort-Object	    # Sort objects by property value
    Split-Path	    # Return part of a path
    Start-DscConfi	# Apply Desired State config to nodes
    Start-Job	    # Start a PowerShell background job
    Start-Process	# Start one or more processes
    Start-Service	# Start a stopped service
    Start-Sleep	    # Suspend shell, script, or runspace activity
    Start-Transact	# Start a new transaction
    Start-Transcri	# Start a transcript of a command shell session
    Stop-Computer	# Stop (shut down) a computer
    Stop-Job	    # Stop a PowerShell background job
    Stop-Process	# Stop a running process
    Stop-Process	# Stop a running process
    Stop-Service	# Stop a running service
    Stop-Transcrip	# Stop the transcription process
    Suspend-Servic	# Suspend a running service
    Switch	        # Multiple if statements
    Tee-Object	    # Send input objects to two places
    Test-ComputerS	# Test and repair the secure channel to the doma
    Test-Connectio	# Ping one or more computers
    Test-Path	    # Return true if the path exists, otherwise return fa
    Test-WSMan	    # Test if a computer is setup to receive remote comman
    Trace-Command	# Trace an expression or command
    Trace-Command	# Trace an expression or command
    Trap	        # Handle a terminating error
    Try ... Catch	# Handle a terminating error within a scriptblock
    Unblock-File	# Unblock files downloaded from the Internet
    Unblock-File	# Unblock files downloaded from the Internet
    Undo-Transacti	# Roll back a transaction
    Unregister-Eve	# Cancel an event subscription
    Unregister-PSS	# Configuration  Delete registered PS session configurati
    Update-Formatd	# Update and append format data files
    Update-Help	    # Download and install help files
    Update-List	    # Add and remove items from a collection
    Update-TypeDat	# Update extended type configuration
    Update-Typedat	# Update the current extended type configuration
    Use-Transactio	# Add a command or expression to the transaction
    Wait-Event	    # Wait until a particular event is raised
    Wait-Job	    # Wait for a background job
    Wait-Process	# Wait for a process to stop
    Where method	# Filter objects from a collection
    Where-Object	# Filter the objects passed along the command pipel
    Where-Object	# Filter input from the pipeline
    While	        # Loop while a condition is True
    Write-Debug	    # Write a debug message to the host display
    Write-Error	    # Write an object to the error pipeline
    Write-EventLog	# Write an event to an event log
    Write-Host  	# Display text on screen
    Write-Host	    # Write customized output to the host/screen
    Write-Output	# Write an object to the pipeline
    Write-Progress	# Display a progress bar
    Write-Verbose	# Write a string to the host's verbose display
    Write-Warning	# Write a string in reverse video to the display
    Zipfile	        # Compress or Extract zip files

[13]:<http://ss64.com/ps/>