Las listas de acceso pueden ser identificadas por números o por nombres.
Cada vez que se crea una lista de acceso, por defecto se te deniega a todas las redes, es por eso que es necesario indicarle posteriormente el permiso al resto de redes excluyendo la lista creada, permitiendo al resto de redes la conexion exceptuando a la de la lista de acceso denegada.
```
Lista de acceso estandar (1-99 / nombre):
    Permitir / Denegar todo el trafico
Lista de acceso extendida (101-199 / nombre):
    Permitir / Denegar todo el trafico con conexiones http, https, ssh, telnet
    Permitir / Denegar todo el trafico entre dos equipos
```
Denegación de redes:
Para denegar una red, es necesario tener acceso al router del destino donde no se quiere recibir señal de la red a bloquear, crear una lista con un rango de hosts o redes bloqueadas y aplicar la lista permitiendo al resto el acceso a la red destino.

```
#Habilitamos el router
enable
#Accedemos al modo configuracion
configure terminal
#Creamos una lista de acceso con un ID numerico compuesto de la siguiente manera:
#access-list 1 deny [ip] [mascara negada]
access-list 1 deny 192.168.1.128 0.0.0.63
#Permitimos el resto de redes excluyendo la de la lista 1
access-list 1 permit any
#Seleccionamos el puerto por donde no queremos recibir la red bloqueada
in fa0/0
#Indicamos que lo que haya en la lista 1, sea excluido y no habra contacto
ip access-group 1 out
```

Permitir Redes:
Para permitir una red, es necesario tener acceso al router del destino donde se quiere recibir señal de la red a dar acceso, crear una lista con un rango de hosts o redes permitidas y aplicar la lista bloqueando al resto el acceso a la red destino.
```
#Habilitamos el router
enable
#Accedemos al modo configuracion
configure terminal
#Creamos una lista de acceso con un ID numerico compuesto de la siguiente manera:
#access-list 1 permit [ip] [mascara negada]
access-list 1 permit 192.168.1.128 0.0.0.63
#Seleccionamos el puerto por donde queremos recibir la red
in fa0/0
#Indicamos que lo que haya en la lista 1, sea permitido
ip access-group 1 in
```

Eliminar Lista de Acceso:
Para eliminar una lista de acceso, hay que tener el numero de identificacion de la lista de acceso, posteriormente habrá que ejecutar el siguiente comando en modo configuracion:
```
no access-list 1
```

Mostrar Lista de Acceso:
Para mostrar una lista de acceso, es necesario tener el numero de identificacion de la lista de acceso, posteriormente habrá que ejecutar el siguiente comando en modo configuracion:
```
show access-list 1
```

Mostrar Tipos de Listas:
Para mostrar el tipo de lista de acceso que se puede establecer, es necesario acceder al router en modo configuracion y escribir el siguiente comando:
```
ip access-list ?
```

Mostrar Listas de Acceso Creadas:
Para mostrar el numero y cantidad de listas de acceso creadas, es requerido estar en el router que almacena las listas de acceso y ejecutar el siguiente comando:
```
show access-lists
```

Permitir / Denegar Acceso de Protocolos:
Para permitir o denegar protocolos con listas de acceso hay que seguir la siguiente estructura en modo de configuracion:
`access-list 101-199 [permit/deny] [protocolo] [origen] [destino]`

Un ejemplo de la denegación de rango de IPs, desde la IP `192.168.1.128` hasta la red `192.168.1.208`, bloqueando el protocolo ssh por ftp en el puerto 22:
```
access-list 101 deny tcp 192.168.1.128 0.0.0.69 192.168.1.208 0.0.0.15 eq 22
```