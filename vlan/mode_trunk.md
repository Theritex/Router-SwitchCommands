enable
configure terminal
in fa0/1
switchport mode trunk

<!--
Switch#confi t
Switch(config)#in range fa0/2-3
Switch(config-if-range)#switchport mode access 
Switch(config-if-range)#switchport access vlan 20
-->