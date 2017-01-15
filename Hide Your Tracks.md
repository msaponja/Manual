# Hide Your Tracks [[5]]

### Meterpreter

    $ clearev   # Clear all event logs (Application, System, Security)
### Windows machines

- Download [clearlogs.exe]
- Run: clearlogs.exe -sec
NOTICE: You will need physical access to the victims system

### Linux systems

    $ kwrite /var/log/messages  # Delete all or specific entries
    NOTICE: You can use any other text editor
    
### Erasing the Command History

    $ more ~/.bash_history      # Command history
    $ echo $HISTSIZE            # The size of our history file
    $ export HISTSIZE=0         # Set the histoty file size to zero
    
### Shredding the History File

    $ shred -zu root/.bash_history      # The shred command with the -zu switches will overwrite the history with zeros and delete the file.
    
### The logs[[6]]

    $ WTMP      # Every log on/off, with login/logout time plus tty and host
    $ UTMP      # Who is online at the moment
    $ LASTLOG   # Where did the logins come from 
### Location of logs 

- UTMP : /etc or /var/adm or /usr/adm or /usr/var/adm or /var/log
- WTMP : /etc or /var/adm or /usr/adm or /usr/var/adm or /var/log
- LASTLOG : /usr/var/adm or /usr/adm or /var/adm or /var/log

    NOTICE: The location depends on UNIX distribution

### Shell History
    
    $ mv .logout save.1         
    $ echo rm .history>.logout
    $ echo rm .logout>>.logout
    $ echo mv save.1 .logout>>.logout
    # Delete .history
    
### Log modifier programs

    $ ah-1_0b.tar   # Changes the entries of accounting information
    $ clear.c       # Deletes entries in utmp, wtmp, lastlog and wtmpx
    $ cloak2.c      # Changes the entries in utmp, wtmp and lastlog
    $ invisible.c   # Overwrites utmp, wtmp and lastlog with predefines values
    $ marryv11.c    # Edit utmp, wtmp, lastlog and accounting data
    $ wzap.c        # Deletes entries in wtmp
    $ wtmped.c 	    # Deletes entries in wtmp
    $ zap.c         # Overwrites utmp, wtmp, lastlog - Don't use! Can be detected!
    NOTICE: Never delete the logs

[5]: <http://null-byte.wonderhowto.com/how-to/hack-like-pro-cover-your-tracks-leave-no-trace-behind-target-system-0148123/>
[clearlogs.exe]: <http://ntsecurity.nu/toolbox/clearlogs/>
[6]: <http://www.ouah.org/cover_your_tracks1.html>