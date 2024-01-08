<!--Enmascaramiento - NAT Dinamica-->
```prolog
#---------------------------------------------------------------------------#---------------------------------------------------------------------------------------------------#
|   COMANDO                                                                 |       DESCRIPCION                                                                                 |
#---------------------------------------------------------------------------#---------------------------------------------------------------------------------------------------#
enable                                                                      §;
confi t                                                                     §;
in gi0/0                                                                    §;
ip nat inside                                                               §;
in gi0/1                                                                    §;
ip nat outside                                                              §;
exit                                                                        §;
access-list 1 permit 10.0.0.0 0.255.255.255                                 §;  # Lista de acceso aprs que las ips de esa red tengan acceso || lista de acceso "1"
ip nat pool natdinamica 20.0.0.3 20.0.0.6 netmask 255.0.0.0                 §;  # natdinamica = nombre de la lista  || rango agregado = 20.0.0.3 20.0.0.6 || mascara normal (no negada)
ip nat inside source list 1 pool natdinamica                                §;

```

<!--
Router>EN
Router#confi t
Enter configuration commands, one per line.  End with CNTL/Z.
Router(config)#router ospf 1
Router(config-router)#network 3.0.0.0 0.255.255.255 area 0
Router(config-router)#network 40.0.0.0 0.255.255.255 area 0
Router(config-router)#exit
Router(config)#access-l
Router(config)#access-list 1 permit 40.0.0.0 0.255.255.255
Router(config)#ip nat pool dinamica 3.0.0.50 3.0.0.100 netmask 255.0.0.0
Router(config)#ip nat inside source list 1 pool dinamica
-->