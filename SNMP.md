# SNMP

### Concept [[12]]

![snmp.png](https://www.dropbox.com/s/srwfkxgbqyep6yo/snmp.png?dl=0&raw=1)

### Command Examples [[13]]
This command returns an administratively assigned name for this managed node.

    % snmpget -mALL -v1 -cpublic snmp_agent_Ip_address sysName.0
The snmpwalk command performs a sequence of chained GETNEXT requests automatically. It is a work saving command.

    % snmpwalk -mALL -v1 -cpublic snmp_agent_Ip_address system
    
The snmpbulkwalk command uses the GETBULK SNMP protocol feature to query for an entire tree of information about a network entity

    % snmpbulkwalk -mALL -v2c -cprivate snmp_agent_Ip_address entPhysicalTable>time7

    
    
[12]: <http://www.cert.hr/sites/default/files/NCERT-PUBDOC-2010-09-313.pdfl>
[13]: <https://docs.oracle.com/cd/E19201-01/820-6413-13/SNMP_commands_reference_appendix.html>



