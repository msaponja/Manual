# WMIC[[12]]
WMIC extends WMI for operation from several command-line interfaces and through batch scripts. Before WMIC, you used WMI-based applications (such as SMS), the WMI Scripting API, or tools such as CIM Studio to manage WMI-enabled computers. Without a firm grasp on a programming language such as C++ or a scripting language such as VBScript and a basic understanding of the WMI namespace, do-it-yourself systems management with WMI was difficult. WMIC changes this situation by giving you a powerful, user-friendly interface to the WMI namespace.

### Listing 1: Code to Display

    Results at the
    Console from a WMIC Batch File
    wmic /node:SERVER1, SERVER4
        cpu get name, caption,
        maxclockspeed, systemname
        /format:textvaluelist.xsl
        
### Listing 2: Code to Use Variables in a WMIC Batch File

    @echo off
    if "%1"=="" goto msg
    if "%2"=="" goto single
    wmic /node:%1, %2 cpu get name,
     caption, maxclockspeed,
     systemname
     /format:textvaluelist.xsl
    goto end
    :single
    wmic /node:%1 cpu get name,
        caption, maxclockspeed,
        systemname
        /format:textvaluelist.xsl
    goto end
    :msg
    echo you must specify at least
        one computer name.
    :end

### Listing 3: Code to Direct WMIC Output to an HTML File
    wmic /node:SERVER4
      /output:e:\file1.htm cpu get
      description, maxclockspeed,
      extclock, manufacturer,
      revision /format:hform.xsl
### Listing 4: Code to Direct Class
    Command Output to an HTML File
wmic /output:e:\se_class.htm
      class WIN32_SOFTWAREELEMENT
      get
### Listing 5: Code to Generate XML Output from a WMIC Command
     wmic cpu get maxclockspeed
       /translate:basicxml
      /format:rawxml.xsl
[12]: <https://msdn.microsoft.com/en-us/library/bb742610.aspx>