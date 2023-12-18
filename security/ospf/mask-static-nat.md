<!--Enmascaramiento - NAT Estatica-->
```prolog
#---------------------------------------------------------------------------#---------------------------------------------------------------------------------------------------#
|   COMANDO                                                                 |       DESCRIPCION                                                                                 |
#---------------------------------------------------------------------------#---------------------------------------------------------------------------------------------------#
enable                                                                      §;Inicio del router
confi t                                                                     §;Acceso al modo configuracion
in gi0/0                                                                    §;Indicar que puerto se modifica
ip nat insisde                                                              §;Indicar que el puerto es el interno (router donde salen los datos)
in gi0/1                                                                    §;Indicar que puerto se modifica
ip nat outside                                                              §;Indicar que el puerto es el externo (router donde llegan los datos)
exit                                                                        §;Salir del actual modo
ip nat inside source static 10.0.0.2 20.0.0.3                               §;Indicar que el puerto interno que recibe las IP 10.0.0.2, la muestra al siguiente equipo como IP 20.0.0.3
ip nat inside source static 10.0.0.3 20.0.0.4                               §;Indicar que el puerto interno que recibe las IP 10.0.0.3, la muestra al siguiente equipo como IP 20.0.0.4
```