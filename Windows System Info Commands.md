# Systeminfo[[54]]

### Syntax

    systeminfo [/s <Computer> [/u <Domain>\<UserName> [/p <Password>]]] [/fo {TABLE | LIST | CSV}] [/nh]
    
    /s  # Specifies the name or IP address of a remote computer
    /u  # Runs the command with the account permissions of the specified user account
    /p  # Specifies the password of the user account that is specified in the /u parameter
    /fo # Specifies the output format
    /nh # Suppresses column headers in the output.
    /?  # Displays help at the command prompt.
    
# Tasklist

### Syntax

    tasklist[.exe] [/s computer] [/u domain\user [/p password]] [/fo {TABLE|LIST|CSV}] [/nh] [/fi FilterName [/fi FilterName2 [ ... ]]] [/m [ModuleName] | /svc | /v]
# Reg query

### Syntax
    reg query <KeyName> [{/v <ValueName> | /ve}] [/s] [/se <Separator>] [/f <Data>] [{/k | /d}] [/c] [/e] [/t <Type>] [/z]
    
    /ve         # Runs a query for value names that are empty
    /s          # Specifies to query all subkeys and value names recursively
    /se         # Specifies the single value separator to search for in the value name type REG_MULTI_SZ
    /f          # Specifies the data or pattern to search for
    /k          # Specifies to search in key names only
    /d          # Specifies to search in data only
    /c          # Specifies that the query is case sensitive
    /e          # Specifies to return only exact matches
    /t <Type>   # Specifies registry types to search
    /z          # Specifies to include the numeric equivalent for the registry type in search results
    

[54]:<https://technet.microsoft.com/en-us/library/cc771190(v=ws.11).aspx>