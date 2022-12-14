Universidad San Carlos de Guatemala <br>
Facultad de Ingeniería <br>
Escuela de Ciencias y Sistemas <br>
Redes de computadoras 1 sección Q <br>
Ing. Allan Alberto Morataya Gómez <br>
Aux. Jorge David Ambrosio Ventura <br>
<br>
<br>
### <center>Manual de configuración proyecto 2 </center>
<br>
<br>
  

| Nombre | Carnet |
|--|--|
| Pablo José Oliva Bonilla | 201700898 |
| Henry Gabriel Peralta Martinez | 201712289 |
| Josseline Suseth Godinez Garcia | 201503841|

# Manual de configuración

### Herramientas necesarias
- 4 PC/Laptop con sistema operativo libre.
### Software
- GNS3 instalados en los hosts fisicos.
- OpenVPN.
- Cloud Platform.
- VMware

### Topología Completa
![enter image description here](https://i.ibb.co/rtH7dpb/Whats-App-Image-2022-11-02-at-10-22-44-AM.jpg)

### Topología 1 (Red Wan)
![enter image description here](https://i.ibb.co/54gwGNv/topologia1.png)

En la topología 1 tenemos la Red Wan, la cual servira como interconexion de centro de datos y oficina central.
La Red Wan  que se utilizo fue la 10.4.0.0/16.

Para las configuraciones de los routers se utilizaron 2 protocolos: 

 - El protocolo de redundancia GLBP donde el router 2 (R2) sera Activo y el router 3 (R3) sera Pasivo.
 - El protocolo de redundancia HSRP donde el router 5 (R5) sera Activo y el router 4 (R4) sera Pasivo.

### Topología 2
![enter image description here](https://i.ibb.co/djnzKVL/topologia2.png)

### Topología 2 (Oficina Central)
En la oficina central se crearon 4 departamentos, el departamento de recursos humanos, contabilidad, ventas y bases de datos.
distribuciones de los departamentos:

 - Recursos humanos: 1 gerente, 15 reclutadores, y 5 analistas de recursos humanos
 - Contabilidad: 1 gerente, 5 asistentes de contabilidad, 1 contador y 1 auditor.
 - Ventas: 76 operadores, 4 encargados de cuentas, 12 managers, 1 gerente y un crecimiento de 32%.
 - Informática: 15 programadores, 5 gestores de proyectos, 1 administrador de la base de datos, 3 analistas de infraestructura, 6 testers, 1 gerente y un crecimiento de 18%.

La red red para la oficina central es la 192.168.44.0/24 
tambien se configuraron los modos de acceso y troncales, tambien se crearon las vlan 10 para recursos humanos, 20 para contabilidad, 30 para ventas y 40 para informática.

### Topología 3 (Centro de datos)
![enter image description here](https://i.ibb.co/5k1V5gH/topologia3.png)

La red que se utilizo en el centro de datos es 192,168.45.0/24 
Se configuraron las vlans y los modos de acceso a las vpcs y se configuro el router 6 para establecer la comunicación entre centro de datos y oficina central.

### Resultado de subnetting
#### Red Wan
![enter image description here](https://i.ibb.co/hMzhXpb/RedWan.png)

#### Oficina Central
![enter image description here](https://i.ibb.co/DLNjrwp/Oficinacentral.png)

#### Centro de datos
![enter image description here](https://i.ibb.co/17X4T7k/Centodedatos.png)

### Comandos utilizados
#### Comando HSRP
Configuración router activo <br>
Conf t • <br>
Interface [tipo]#/# <br>
No shutdown <br>
Standby # ip [ip-virtual] • <br>
Standby # priority [num] • <br>
Standby # preempt • <br>
Exit <br>

Configuración router en espera <br>
Conf t <br>
Interface [tipo]#/# <br>
No shutdown <br>
Standby # ip [ip-virtual] <br>
Standby # priority [num] <br>
exit <br>

ver la configuración <br>
Show running-config <br>
Show standby brief <br>

#### Comando GLBP

Esquema <br>
Conf t <br>
Int s#/# <br>
Ip address <br>
No shutdown <br>
End <br>
Write <br>

#### Configuracion routing estatico

Conf t <br>
iP route [dirección de red] [máscara subred] [dirección ip de la interfaz destino o de salida] <br>
exit <br>

Ver la configuración del enrutamiento <br>
show ip route <br>
show ip int brief <br>

#### Routing RIP
Conf t <br>
router rip <br>
version 2 <br>
network [dirección de red a la que se conecta] <br>
exit <br>

#### Configurar routing EIGRP

Conf t <br>
router eigrp [número entre 1 y 65535] <br>
network [dirección de subred] [bits restantes de la máscara de red] <br>
exit <br>
Conf t <br>
router eigrp 10 <br>
network 192.168.12.0 0.0.0.255 <br>
exit <br>

#### Modo Acceso
Conf t <br>
Int f#/# <br>
Switchport mode Access <br>
Switchport Access vlan # <br>
Do wri <br>
End <br>

#### Modo Troncal
Conf t <br>
Int f#/# <br>
Switchport mode trunk <br>
Switchport trunk allowed vlan 1,#,#,1002-1005 <br>
Do wri <br>
End <br>

#### Configuracion VTP
Conf t <br>
Vtp domain nombredeldominio <br>
Vtp password contraseñadeldominio <br>
Vtp mode server|client|transparent <br>
Do wri <br>
End <br>

#### Port Channel
Conf t <br>
Interfaces range f#/#-# <br>
Channel-group # mode on <br>
Do wri <br>
End <br>

#### Configuracion vlan
Conf t <br>
Vlan numerodevlan <br>
Name nombredevlan <br>
Do wri <br>
End <br>
