# Cisco Switch IOS commands

### Cisco IOS command hierarchy  
|Mode|Explanation|Example|
|-----------|--------------|-----------------------|
|Router>|User EXEC mode||
|Router#|Privileged EXEC mode|enable|
|Router(config)#|Configuration mode (accessible only at privileged EXEC mode)|configure terminal|
|Router(config-if)#|Interface level within configuration mode|interface vlan xx|
|Router(config-router)#|Routing engine level within configuration mode||
|Router(config-line)#|Line level (vty, tty, async) within configuration mode|line vty 0 15|

<p align="center">
  <img width="500" height="540" src="https://github.com/nauskis/Kisko/blob/master/Kuvia/hierarchy.PNG?raw=true">
</p>
----------------------------------------------------------------------------------------------------------------------------

### Basic commands
|Command|Explanation|mode|
|-----------------------------|--------------------------------------------|--------------------------------------------|
|enable|Enter privileged EXEC mode|EXEC|
|Configure terminal|Enter global configuration mode|Privileged EXEC|
|Interface XX|Enter interface configuration mode|Configuration mode|
|ip address xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy|Configure the interface IP address|Interface-level within configuration mode|
|no shutdown|Enable the specified interface|Interface-level within configuration mode|
|end|Return to privileged EXEC mode|interface-level within configuration mode|
|show ip interface brief|Determine the status of physical and virtual interfaces|Privileged EXEC mode|
|copy running-config startup-config|Save the running config to the startup config|Privileged EXEC mode|

----------------------------------------------------------------------------------------------------------------------------

### Basic device configuration
|Command|Explanation|
|--------------------------------------|---------------------------------------|
|enable|enter privileged EXEC mode|
|configure terminal|enter configuration mode with privileged EXEC mode|
|hostname s1|configure the device with a hostname|
|enable secret karamba|Secure privileged EXEC access with a password|
|line console 0|Enter console port configuration mode|
|password kiskokisko|Enter password for console port|
|login|Enable login to console port|
|exit||
|line vty 0 15|Enable VTY (remote access lines) for the first 16 ports|
|password pillimehu|Set password for VTY lines|
|login|Enable login from VTY lines|
|exit||
|service password-encryption|Encrypt all passwords shown in configuration files|
|interface vlan 1|Enter configuration mode for interface vlan 1|
|ip address ip-address subnet-mask|Configure the interface with IP address and subnet mask|
|no shutdown|Turn the port on|
|exit|Exit the interface configuration|
|exit|Exit global configuration mode|
|show running-config|Shows the currently running configuration|
|save running-config startup-config|Save the currently running configuration to the start-up configuration|
|exit||


- The most important password to configure is access to the privileged EXEC mode (enable). To secure privileged EXEC access, use the `enable secret password` global config command.
- To secure EXEC access, the console port must be configured by entering line console configuration mode by using `line console 0` global configuration command. The zero is used to represent the first and most likely only console interface.
- Virtual terminal (VTY) lines enable remote access to the device. To secure VTY lines used for SSH and Telnet, enter line VTY mode using the command `line vty 0 15`. Next specify the VTY password using the `Password password` command. Lastly, enavle VTY access using the `login` command.
- The only IP address  the switch needs for remote connection is that of the vlan 1 interface. By default, every port is connected to vlan 1, thus when a computer is connected to the switch by e.g Ethernet connection, the switch can be remotely configured.

----------------------------------------------------------------------------------------------------------------------------

### Configure Switch Management Interface (SVI)
|Command|Explanation|
|------------------------------|--------------------------------------------|
|enable|enter privileged mode|
|configure terminal|Enter configuration mode|
|interface vlan 99|Enter interface configuration mode for the SVI|
|ip address xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy|Configure SVI IP address|
|no shutdown|Enable the management interface|
|end|Return to privileged EXEC mode|
|copy running-config startup-config|Save the running configuration to the startup configuration|

![SVI](https://raw.githubusercontent.com/nauskis/Kisko/master/Kuvia/SVI.PNG)

----------------------------------------------------------------------------------------------------------------------------

### Configure Switch Default Gateway
|Command|Explanation|
|----------------------------|---------------------------------------------|
|Enable|Enter privileged EXEC mode|
|conf t|Enter configuration mode|
|ip default-gateway xxx.xxx.xxx.xxx|Configure the default gateway for the switch|
|end|Return to privileged EXEC mode|
|copy running-config startup-config|Save the running configuration to the startup configuration|

The default gateway is the router to which the switch is connected. The switch will forward its IP packets with destination IP addresses outside the local network to the default gateway. The switch should be configured with a default gateway if it will be managed remotely from networks that are not directly connected.
![default-gateway](https://github.com/nauskis/Kisko/blob/master/Kuvia/default-gateway2.PNG?raw=true)  
The default gateway of the **S1** is the router port to which it is connected to.

-------------------------------------------------------------------------------------------------------------------------

### SVI (Switch Virtual Interface)
An SVI is normally found on switches (Layer 3 and Layer 2). If I have understood correctly, each Vlan has it's own SVI. An SVI cannot be activated unless the VLAN itself is created and at least one physical port is associated and active in that VLAN. SVI allows traffic to be routed between VLANs.

### Information About the Management Interface

The management interface is the default interface for in-band management of the controller and connectivity to enterprise services such as AAA servers. It is also used for communications between the controller and access points. The management interface has the only consistently “pingable” in-band interface IP address on the controller. You can access the GUI of the controller by entering the management interface IP address of the controller in the address field of your browser.

### Sources  
- https://www.cisco.com/c/en/us/td/docs/wireless/controller/7-4/configuration/guides/consolidated/b_cg74_CONSOLIDATED/b_cg74_CONSOLIDATED_chapter_010011011.html
- https://learningnetwork.cisco.com/thread/62241
- https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/02_cisco_ios_hierarchy.htm
- https://study-ccna.com/ios-basic-commands/
