Comenzando con el proceso de configuración de red VTP:
- Paso1:
Inidicamos los modos de Switch `vlan\vtp\commands.md`
```
en
confi t
vtp mode <modo>
vtp domain <dominio>
vtp password <password>
```
- Paso2:
Nos conectamos por el puerto <puerto> y establecemos l conexión truncada (es truncada cuando es de switch a switch o de switch a router).
Más documentación en `vlan\mode_trunk.md`
```
in <puerto>
switchport mode trunk
```
- Paso3:
Damos el modo acceso a las vlans a los equipos de una vlan.
Más documentación en `vlan\mode_access.md`
```
in <puerto>
switchport mode access
switchport access vlan <numero vlan>
```
