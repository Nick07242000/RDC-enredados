# Trabajo Practico N°1

**Nombres**

- Constanza Medran  
- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Córdoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Teoria de Redes** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**15/03/2026**

---

### Información de los autores

* **Información de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - constanza.medran@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

El presente trabajo práctico tiene como objetivo analizar el funcionamiento básico de la transmisión de datos en redes de computadoras mediante una simulación del envío de paquetes entre hosts y routers. 

Para ello, cada participante representa un dispositivo de red con una identidad compuesta por dirección IP, dirección MAC, máscara de subred y gateway por defecto. A partir de esta configuración se construyen manualmente frames Ethernet que encapsulan paquetes IP con un payload determinado, simulando el proceso real de transmisión de datos en una red. 

Durante el ejercicio se analizan los mecanismos de resolución de direcciones mediante ARP, el uso del gateway para alcanzar redes remotas y el comportamiento hop-by-hop de los routers, incluyendo el decremento del campo TTL en cada salto. 

En una segunda etapa del laboratorio se introduce la modificación intencional de datos durante la transmisión para evaluar la aplicación de técnicas de detección y corrección de errores (EDAC). De esta manera, el trabajo permite comprender de forma práctica cómo se produce el transporte de información en redes, así como los mecanismos que garantizan su correcta entrega e integridad.

**Palabras clave**: *Redes de computadoras; direccionamiento IP; direccionamiento MAC; protocolo ARP; encapsulación de paquetes; ruteo entre redes; gateway por defecto; TTL; transmisión de datos; detección de errores (EDAC)*

---

## Introducción

Las redes de computadoras permiten la comunicación entre dispositivos mediante el intercambio de datos a través de distintos protocolos y mecanismos de direccionamiento. 

Para comprender cómo se produce este proceso, es fundamental analizar el recorrido que realiza un paquete de datos desde un host origen hasta un host destino, atravesando distintos dispositivos de red como routers y gateways. 

En este trabajo práctico se realiza una simulación didáctica del envío de paquetes en una red, permitiendo observar de manera práctica conceptos fundamentales como la encapsulación de datos, la resolución de direcciones mediante el protocolo ARP, el funcionamiento del gateway por defecto y el ruteo entre redes. 

A través de la construcción manual de frames Ethernet y paquetes IP, y la simulación del recorrido hop-by-hop entre routers, se busca comprender cómo interactúan las direcciones MAC e IP en el proceso de transmisión de información. 

Asimismo, el laboratorio incorpora una segunda etapa orientada a la detección de errores en la transmisión de datos mediante técnicas EDAC, lo que permite analizar la importancia de los mecanismos de verificación de integridad en las comunicaciones de red.

---

## Marco teórico

En las redes de computadoras, la comunicación entre dispositivos se realiza mediante el intercambio de paquetes de datos que atraviesan diferentes capas del modelo de red. En redes Ethernet, los datos se transmiten dentro de frames que contienen direcciones físicas o MAC, utilizadas para la comunicación dentro de una red local. Sin embargo, para permitir la comunicación entre redes distintas se utilizan direcciones IP, que representan un sistema de direccionamiento lógico independiente del hardware.

Cuando un host necesita enviar información a otro dispositivo, encapsula los datos en un paquete IP, el cual a su vez se encapsula dentro de un frame Ethernet para su transmisión por el medio físico. Si el destino pertenece a otra red, el host envía el paquete al gateway por defecto, que normalmente es un router encargado de reenviar los paquetes hacia otras redes según su tabla de ruteo. Durante este proceso, los routers desencapsulan el frame recibido, analizan el paquete IP y lo vuelven a encapsular en un nuevo frame Ethernet correspondiente al siguiente enlace de la red.

Para poder enviar un frame dentro de una red local es necesario conocer la dirección MAC del dispositivo destino. Este proceso se realiza mediante el Protocolo de Resolución de Direcciones (ARP), que permite asociar direcciones IP con direcciones MAC dentro de la red local. Además, los paquetes IP incluyen un campo llamado TTL (Time To Live) que se decrementa en cada salto entre routers, evitando que los paquetes circulen indefinidamente en caso de errores de ruteo.

Finalmente, para garantizar la integridad de los datos transmitidos, se utilizan mecanismos de detección y corrección de errores (EDAC), que permiten identificar si la información fue alterada durante la transmisión. Estos mecanismos son fundamentales para asegurar la confiabilidad de las comunicaciones en redes de computadoras.

---

## Resultados

### Identificación de dispositivos y armado de la topología

Cada miembro del grupo genero una tarjeta NIC especificando el nombre del dispositivo, la direccion IP, la direccion MAC, la mascara de subred y el gateway por defecto.

Mientras que la mayoria de los miembros resprento un host, uno de los miembros represento un default gateway (router) para la comunicacion con otras redes, conformando asi una LAN entre los miembros del grupo.

|Device|Role|MAC|IP|NETMASK|GATEWAY
|---|---|---|---|---|---|
|RouterConstanza|Router|AA:44:64|10.13.0.100|255.255.255.248|10.3.0.1
|HostSofia|Host|AD:43:93|10.13.0.101|255.255.255.248|10.3.0.1
|HostIgnacio|Host|AC:44:54|10.13.0.102|255.255.255.248|10.3.0.1
|HostNicolas|Host|AD:42:07|10.13.0.103|255.255.255.248|10.3.0.1

La mascara de subred tiene el valor de 255.255.255.248 ya que la red solo tiene 3 dispositivos ademas del default gateway.

### Armado de topología

Se realizo una simulacion de una rutina ARP donde nuestro router descubrio a sus vecinos, preguntando por sus IPs y recibiendo sus direcciones fisicas.

|IP|MAC|
|---|---|
|?|?

### Conformación de paquetes

Cada uno de los hosts genero un paquete para ser transmitido a traves de la red, con un payload y un destino en particular:

|MAC DESTINO|MAC ORIGEN|IP ORIGEN|IP DESTINO|TTL|PAYLOAD
|---|---|---|---|---|---|
|AA:44:64|AD:43:93|10.13.0.101|10.2.0.101|6|1101010010011010
|AA:44:64|AC:44:54|10.13.0.102|10.7.0.101|6|1000000110100101
|AA:44:64|AD:42:07|10.13.0.103|10.4.0.104|6|001100011001

### Simular las transmisiones y recepciones

Estos paquetes fueron enviados al default gateway para ser entregado al destino final, donde cada router desempaqueto y empaqueto los frames de acuerdo al recorrido de los mismo a traves de ethernet.

|MAC DESTINO|MAC ORIGEN|IP ORIGEN|IP DESTINO|TTL|PAYLOAD
|---|---|---|---|---|---|
|?|?|?|?|?|?

### Reflexiones y documentación

...

### Inyección y detección de errores

...

---

## Discusión y conclusiones

...

---

## Referencias

[1] - ...
