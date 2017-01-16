# CHKCONFIG[[3]]
The chkconfig utility is a command-line tool that allows you to specify in which runlevel to start a selected service, as well as to list all available services along with their current setting.

    $ chkconfig --list                              # Listing the Services
    $ chkconfig --list service_name                 # Display the current settings for a selected service only
    $ chkconfig service_name on                     # Enabling a Service
    $ chkconfig service_name on --level runlevels   # To enable a service in certain runlevels only
    $ chkconfig service_name off                    # Disabling a Service
    
[3]: <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-services-chkconfig.html>
