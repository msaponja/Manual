# Cisco commands

### Exec commands [[4]]

    <1-99>           # Session number to resume
    connect          # Open a terminal connection
    disconnect       # Disconnect an existing telnet session
    enable           # Turn on privileged commands
    exit             # Exit from Exec mode
    help             # Description of the interactive help system
    lat              # Open a lat connection
    lock             # Lock the terminal
    login            # Log in as a particular user
    logout           # Exit from Exec mode and log out
    menu             # Start a menu-based user interface
    mbranch          # Trace multicast route for branch of tree
    mrbranch         # Trace reverse multicast route to branch of tree
    mtrace           # Trace multicast route to group
    name-connection  # Name an existing telnet connection
    pad              # Open a X.29 PAD connection
    ping             # Send echo messages
    resume           # Resume an active telnet connection
    show             # Show running system information
    systat           # Display information about terminal lines
    telnet           # Open a telnet connection
    terminal         # Set terminal line parameters
    tn3270           # Open a tn3270 connection
    trace            # Trace route to destination
    where            # List active telnet connections
    x3               # Set X.3 parameters on PAD
    
### Common commands [[5]]

    ?                                                   # Help
    show running-configuration                          # Shows the router, switch, or firewall's current configuration
    copy running-configuration startup-configuration    # Save the configuration that is currently being modified (in RAM), also known as the running-configuration, to the nonvolatile RAM (NVRAM)   
    show interface                                      # Displays the status of the router's interfaces
    show ip interface                                   # Provides information about the configuration and status of the IP protocol and its services, on all interfaces.
    config terminal, enable, interface, and router      # Change modes
    no shutdown                                         # Enables an interface (brings it up)
    show ip route                                       # Show the router's routing table
    show version                                        # Gives you the router's configuration register
    debug                                               # It provides detailed debugging output on a certain application, protocol, or service
    
[4]: <http://www.cisco.com/c/en/us/td/docs/ios/12_2/configfun/configuration/guide/ffun_c/fcf001.html>
[5]:<http://www.techrepublic.com/blog/data-center/10-commands-you-should-master-when-working-with-the-cisco-ios-104071/>


