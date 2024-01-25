VTP  (Vlan Trunking Protocol):

Administración de fomra centralizada

Para crear un VTP, hay que crear una contraseña y un dominio

Inidcar cual es el servidor (primero):
```
en
confi t
vtp mode server
#En la creacion del nombre del domonio distingue mayusculas con minusculas
vtp domain smr2
vtp password smr2 
```

Indicar VTP transparente:
```
en
confi t
vtp mode trnasparent
vtp domain smr2
vtp password smr2 
```

Indicar VTP cliente:
```
en
confi t
vtp mode client
vtp password smr2
vpt domain smr2
vtp password smr2 
```