# Cisco Switch IOS commands

### Cisco IOS command hierarchy  
|Mode|Explanation|Example|
|-----------|--------------|-----------------------|
|Router>|User EXEC mode||
|Router#|Privileged EXEC mode|configure terminal|enable|
|Router(config)#|Configuration mode (accessible only at privileged EXEC mode)|configure terminal|
|Router(config-if)#|Interface level within configuration mode|interface vlan xx|
|Router(config-router)#|Routing engine level within configuration mode||
|Router(config-line)#|Line level (vty, tty, async) within configuration mode|line vty 0 15|

----------------------------------------------------------------------------------------------------------------------------

|Command|Explanation|mode|
|-----------------------------|--------------------------------------------|--------------------------------------------|
|enable||
|Configure terminal|Enter global configuration mode|switch>
|Interface vlan xx|Creates an SVI for specified Vlan|Interface vlan 20
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||
||||

### SVI (Switch Virtual Interface)
An SVI is normally found on switches (Layer 3 and Layer 2). If I have understood correctly, each Vlan has it's own SVI. An SVI cannot be activated unless the VLAN itself is created and at least one physical port is associated and active in that VLAN. SVI allows traffic to be routed between VLANs.

### Information About the Management Interface

The management interface is the default interface for in-band management of the controller and connectivity to enterprise services such as AAA servers. It is also used for communications between the controller and access points. The management interface has the only consistently “pingable” in-band interface IP address on the controller. You can access the GUI of the controller by entering the management interface IP address of the controller in the address field of your browser.

### Sources  
- https://www.cisco.com/c/en/us/td/docs/wireless/controller/7-4/configuration/guides/consolidated/b_cg74_CONSOLIDATED/b_cg74_CONSOLIDATED_chapter_010011011.html
- https://learningnetwork.cisco.com/thread/62241
- https://www.cisco.com/E-Learning/bulk/public/tac/cim/cib/using_cisco_ios_software/02_cisco_ios_hierarchy.htm
