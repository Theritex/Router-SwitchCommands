Denegacion de red externa:

Si se quiere denegar una red hay que hacer lo siguiente:

Irse al router de destino donde no queremos recibir los datos o red de al otra:

en
confi t
access-list 1 deny [ip] [mascara negada]	>> access-list deny 192.168.1.128 0.0.0.63
#Ahora hay que permitir el resto de redes porque sino se ha denegado todo, para coger todas las redes:
access-list 1 permit any
in fa0/0
#Inidcamos que lo que haya en la lista 1, será quitado/eliminado y no habra contacto
ip access-group 1 out
#Permitir lo que haya en la lista 1
ip access-group 1 in
#Borrar lista de acceso
no access-list 1

#Mostrar tipos de listas que queremos agregar
ip access-list ?
#Lista de acceso creada con nombre de texto y no con numero
#Ahora creamos informatica y denegamos una ip permitiendo el resto
ip access-list standard informatica
deny 192.168.1.128 0.0.0.63
permit any
exit
in fa0/0
#Quitamos la lista, permitiendo el acceso a la gente de dentor de la red
ip access-group informatica out

#Mostrar listas de acceso:
show access-lists

#Denegar una cosa especifica (protocolos, ftp, ssh, arp ...)
#Estructura
access-list 101-199 [permit/deny] [protocolo] [origen] [destino]
#Denegacion de ssh por ftp, de la ip 128 a la 202 por el puerto 22
Router(config)#access-list 101 deny tcp 192.168.1.128 0.0.0.69 192.168.1.208 0.0.0.15 eq 22