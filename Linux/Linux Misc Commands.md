# Linux Misc Commands [[4]]

Search commands

    $ find -type f | xargs ls -l | cut -c 33- | sort -n     # Search for files - sort by filesize (add -r for reverse order)
    $ find -atime +32 -exec mv {} /var/archive/logs \;      # Move files that are over 1 month old
RPM commands

    $ rpm -q -a             # List all installed packages
    $ rpm -U -v *.rpm       # Upgrade packages
    $ rpm -Fvh *.rpm        # Freshen packages This is the one you should use when applying the latest fixes
    $ for i in `cat <dir to rpm files>`; do if rpm -qpl $i | grep libX >/dev/null; then echo $i; fi; done      # To find which rpm file (not installed) has the file libX

Debian commands

    $ apt-cache search <searchterm>         # Search for package
    $ sudo apt-get install <packagename>    # Install package from repository
    $ sudo dpkg --install <packagename.deb> # Install package from localfile
    $ sudo apt-get update                   # Update package listsfrom repositories
    $ sudo apt-get -u upgrade               # Upgrade installed packages to latest version

Basic script functions

    $ for filename in * ; do echo > $filename; done     # Basic script to perform something against a number of files

Counting commands

    $ grep -v -e "^$" filename | wc -l      # To count number of none empty lines in a file
    $ find . -name "*.p?" | xargs grep -v -e "^$" - | wc -l     # To count number of source code lines (perl)
    
[4]: <http://www.penguintutor.com/linux/misc-quickreference>
