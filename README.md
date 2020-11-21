# Práctica 5

**Universidad de San Carlos de Guatemala**

**Facultad de Ingeniería**

**Escuela de Ciencias y Sistemas**

**Redes de Computadoras 1**

**Ing. Pedro Pablo Hernandez Ramirez**

**Aux. Andrés Alejandro Montufar Cordero**

**Angel Manuel Miranda Asturias 201807394**

**Julian Isaac Maldonado Lopez 201806839**

**Kelvin Vásquez Gómez 201212490**

# Manual de Configuración

Esta practica del curso de REDES 1, contiene 2 topologias, que consiste en crear y configurar distintas topologías de red según los requermientos y
conectarlas de manera remota por medio de una VPN

La primera topolomia contiene:
  - 4 Host [Tiny-core](http://tinycorelinux.net/downloads.html), que se ejecuta en VMWARE(v15)
  - 1 router modelo c3725
  - 1 ethernetswitch 
  - 2 switch 
  
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/topo1.png)]()

La segunda topologia contiene:
  - 1 cliente windows xp
  - 1 cliente linux
  - 3 router modelo c3725
  - 1 ethernetswitch 
  - 2 switch 
  
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/topo2.png)]()

Cantidad de host requeridos por demartamento en la infraestructura:
  - Departamento de profesores 34 host
  - Departamento de estudiantes 64
  - Departamento de invitados 14
  
Vlan que se deben crear:
  - VLAN 20 para los profesores
  - VLAN 50 para los estudiantes
  - VLAN 70 para los invitados
  
### Calculo de busredes utilizando la direccion de red 192.168.0.0/24

[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/calculo_subredes.jpeg)]()

### Configurando el protocolo EIGRP  router2
comandos a utilizar:

    - conf t
    - router eigrp 10
    - network 10.10.0.0 0.0.0.255
    - network 20.10.0.0 0.0.0.255
    - network 192.168.15.0 0.0.0.255
    - end
    
  [![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/show_eigrp_router1.png)]()
    
 ### Configurando el protocolo EIGRP  router3
 
    - conf t 
    - router eigrp 10
    - network 10.10.0.0 0.0.0.255
    - network 20.10.0.0 0.0.0.255
    - network 192.168.15.0 0.0.0.255
    - end
    
 [![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/show_eigrp_router2.png)]()
### Configurando el protocolo EIGRP  router4 

    - conf t
    - router eigrp 10
    - network 10.10.0.0 0.0.0.255
    - network 20.10.0.0 0.0.0.255
    - network 192.168.15.0 0.0.0.255
    - end

[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/show_eigrp_router2.png)]()

### Configurando el protocolo VRRP en el router 3

    -conf t
    -vrrp 10
    -vrrp 10 ip 192.168.15.3
    -vrrp 10 priority 120
    -vrrp 10 preempt
    -end
    
### Configurando el protocolo VRRP en el router 4
    -conf t
    -vrrp 10
    -vrrp 10 ip 192.168.15.3
    -vrrp 10 priority 100
    -end

## Configuracion de VLANS en el Etherswitch de la topologia 1 y 2
 Se utilizo los siguientes comandos para configurar las vlans:
 
    - conf term
    - vlan 20
    - name PROFESORES
     vlan 50
    - name ESTUDIANTES
     vlan 70
    - name INVITADOS
 
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/conf_vlan_topo1.png)]()

### Configurar los puertos en el Etherswitch en modo truncal en ambas topologias
      - conf term
      - int range fa 1/0 - 15
      - speed 100
      - duplex full
      - switchport mode trunk
      - end
      - wr
  
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/conf_puertos_trunk_topo1.png)]()
 
### Configurar los puertos en modo acceso y truncal para la comunicacion entre vlans

[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/conf_puertos_switch.png)]()

### Configuracion del protocolo EIGRP
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/eigrp2-10.jpeg)]()

 
 ### Configuracion de VLAN en SWT2
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/show-vlan.jpeg)]()


 ### Configuracion interfaces router 3 con protocolo vrrp
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/vrrp.jpeg)]()

 ### Configuracion interfaces router 4 con protocolo vrrp
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/sh-runn.jpeg)]()


 ### Configuracion EIGRP del router 3
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/eigrp.jpeg)]()

 ### Topologia Final
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/topo2.jpeg)]()


 ### Configuracion interface router 1
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/sh-int-brief.jpeg)]()


 ### Configuracion interface router 2
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/sh-int-brin2.jpeg)]()


 ### Configuracion ruteo estatico
[![Image from Gyazo](https://github.com/kevgoz/img_p5_redes/blob/master/ip-fow3.jpeg)]()





  
  
