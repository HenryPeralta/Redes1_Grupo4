#### Universidad San Carlos de Guatemala 
#### Facultad de Ingeniería 
#### Escuela de Ciencias y Sistemas 
#### Redes de computadoras 1 sección Q 
#### Ing. Allan Alberto Morataya Gómez 
#### Aux. Jorge David Ambrosio Ventura 
<br>
<br>

### Manual de configuración practica 1

<br>
<br>
  

| Nombre | Carnet |
|--|--|
| Pablo José Oliva Bonilla | 201700898 |
| Henry Gabriel Peralta Martinez | 201712289 |
| Josseline Suseth Godinez Garcia | 201503841|
| Aybson Diddiere Mercado Grijalva | 201700312|

<br>
<br>  
<br>

# Manual de configuración

### Herramientas necesarias
- 4 PC/Laptop con sistema operativo libre.
### Software
- GNS3 instalados en los hosts fisicos.
- OpenVPN.
- Cloud Platform.

### Primer paso
Antes de empezar, todas las PC/Laptop deben estar conectadas con su VPN y verificar que haya ping entre sus maquinas nativas.

### Dispositivos nativos de GNS3 
![enter image description here](https://i.ibb.co/qgnpGwC/1.png)

### Segundo paso
Hay que configurar el UDP Tunnel en el dispositivo cloud
![enter image description here](https://i.ibb.co/3vd339M/2.png)

![enter image description here](https://i.ibb.co/60TjRJ7/3.png)

En esta parte los Local Port y Remote Port pueden ser cualquier puerto y el de su compañero tiene que ser el inverso para que se puedan conectar de manera correcta y en la parte de Remote Host debe ir la ipv4 del compañero que fue dada por la conexión vpn.

### Tercer paso

Configurar la VPC
![enter image description here](https://i.ibb.co/nkTq4FB/4.png)

Una vez en la consola usaremos el formato de subred de tipo C con sub mascara de red 24.

- Usaremos el comando ip para configurar la ip de la vpc, para la PC/Laptop del coordinador se utilizara la ip: 192.168.14.10 y para los demás del equipo cambiaran el .10 por el .20, .30 y .40
- La mascara de sub red 255.255.255.0 para todos al igual que la Geteway 192.168.14.1
- Con el comando sh podremos ver los cambios y con el comando save guardaremos los cambios.

![enter image description here](https://i.ibb.co/yQmmK1W/6.png)


![enter image description here](https://i.ibb.co/8jcbBsn/5.png)

Conectar la VPC con el switch

![enter image description here](https://i.ibb.co/G3grLCc/7.png)

![enter image description here](https://i.ibb.co/Ksf5WMs/8.png)

Para que la comunicación no tenga ningún problema hay que configurar el switch en modo troncal.
![enter image description here](https://i.ibb.co/dJG7DYQ/9.png)

![enter image description here](https://i.ibb.co/z5tdMz2/Final.png)

Esta topología la deben de hacer cada uno de los integrantes repitiendo los pasos.
