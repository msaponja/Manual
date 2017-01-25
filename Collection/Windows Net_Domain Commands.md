# Windows Net/Domain Commands[[52]]

### Net user - Syntax

    net user [<UserName> {<Password> | *} [<Options>]] [/domain]
    net user [<UserName> {<Password> | *} /add [<Options>] [/domain]]
    net user [<UserName> [/delete] [/domain]]
    
### Net user - Examples

    net view \\production   # To see a list of the resources shared by the \\Production computer
    net view /domain:sales  # To see a list of the computers in the sales domain or workgroup
    
### Net view - Syntax

    net view [\\ComputerName [/CACHE] | [/ALL] | /DOMAIN[:DomainName]]
    
### Net group - Syntax

    net group [<GroupName> [/comment:"<Text>"]] [/domain]
    net group [<GroupName>{/add [/comment:"<Text>"] | /delete} [/domain]]
    net group [<GroupName> <UserName>[ ...] {/add | /delete} [/domain]]
    
### Net group - Examples

    net group                                           # This example lists all the groups on the local server
    net group exec /add                                 # This example adds a group called Exec to the local user accounts database
    net group exec /add /domain                         # This example adds a group called Exec to the domain database
    net group exec estherv ralfr stevent /add           # This example adds the existing user accounts estherv, ralfr, and stevent to the Exec group on the local computer
    net group exec estherv ralfr stevent /add /domain   # This example adds the existing user accounts estherv, ralfr, and stevent to the Exec group in the domain database
    net group exec                                      # This example displays users in the Exec group
    net group exec /comment:"The executive staff"       # This example adds a comment to the Exec group record

[52]: <https://technet.microsoft.com/en-us/library/cc754051(v=ws.11).aspx>
    
    