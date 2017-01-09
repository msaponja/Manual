# Using the PHP pfSense Shells [[21]]
Using the PHP pfSense shell allows configuration of the config.xml file directly without needing to use the webConfigurator.

### Options
![ii.png](https://www.dropbox.com/s/3mhvnw8v1eiql99/ii.png?dl=0&raw=1)

### pfSense Developer Shell

    print_r($config);                                               # To output a configuration array
    print_r($config['interfaces']);                                 # To output the interfaces configuration portion of config.xml
    print_r($config['dhcpd']);                                      # To output the dhcp server configuration 
    exit                                                            # To exit the  developer shell
    print_r(get_wireless_modes(\"ath0\"));                          # To output supported wireless modes for an interface 
    $config['system']['enablesshd'] = true; # To enable SSH
    $config['interfaces']['optx']['wireless']['standard'] = "11a";  # Change OPTX to the OPT interface name such as BACKHAUL
    $config['interfaces']['optx']['wireless']['mode'] = "hostap";   
    $config['interfaces']['optx']['wireless']['channel'] = "6";
    $config['dhcpd']['optx']['enable'] = true;                      # To enable dhcp server for an optx interface
    $config['dhcpd']['optx']['range']['from'] = "192.168.31.100";
    $config['dhcpd']['optx']['range']['to'] = "192.168.31.150";
    $config['system']['disablefilter'] = true;                      # Disable the firewall filter
    $config['interfaces']['optx']['disabled'] = false;              # Enable an interface and configure it as a DHCP client
    $config['interfaces']['optx']['ipaddr'] = "dhcp";
    $config['interfaces']['wan']['enable'] = true;                  # Enable an interface and set a static IPv4 address
    $config['interfaces']['wan']['ipaddr'] = "192.168.100.1";
    $config['interfaces']['wan']['subnet'] = "24";
    write_config();                                                 # Save out the new configuration (config.xml)
    system_reboot_sync();                                           # Reboot the system after saving

	

[21]:<https://doc.pfsense.org/index.php/Using_the_PHP_pfSense_Shell>

