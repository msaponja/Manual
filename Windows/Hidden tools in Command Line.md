# Hidden tools in Command Line[[8]]
NOTICE: You need to run CMD with administrator privileges

### System file checker

    $ sfc /scannow      # This performs an immediate scan of your system and will replace files as necessary. You may need to restart Windows when it's done if it finds problems
    $ sfc /scanonce     # This performs a scan the next time you restart your system
    $ sfc /scanboot     # This schedules a scan to be performed every time you restart your system
    $ sfc Revert        # This returns the System File Checker to its default settings. You can use it to turn off the /scanboot option, for example
    
### Check disk

    $ chkdsk Volume     # If you want to check a whole drive, just type the drive letter
    $ chkdsk Filename   # You can also use chkdsk to check a single file or group of files
    $ chkdsk /F         # Run it with this option to have chkdsk go ahead and fix those errors
    $ chkdsk /R         # This option forces chkdsk to locate bad sectors and recover information from them. If chkdsk cannot lock the disk (which it usually can't since you're actually using Windows), it will prompt you run the command the next time you restart Windows

### Cipher
    
    $ cipher /W:pathname    # The /W option removes data on unused portions of a volume, effectively erasing data that may be hanging around on your hard drive after deletion. You can point cipher at an entire volume (like C:) or a specific folder
    
    NOTICE: This applies to traditional hard drives and not SSDs
    
### Driverquery

    $ driverquery /s        # This option lets you specify the name or IP address of a remote computer so that you investigate the drivers it has installed
    $ driverquery /si       # This option shows you the digital signature information for drivers
    $ driverquery /fo       # This is really the key option you'll use with driverquery. It lets you specify the format in which information is displayed so that you can more effectively save it as a report.
    
    Example: driverquery /fo CSV > drivers.csv
    
![g91lech9vvrplpbh0qnd.png](https://www.dropbox.com/s/mfgbhgugjic88vq/g91lech9vvrplpbh0qnd.png?dl=0&raw=1)
    
[8]: <http://lifehacker.com/the-best-tools-hidden-in-windows-command-line-1553193077>
    
    