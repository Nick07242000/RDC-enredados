# Trabajo Practico N°3

**Nombres**

- Constanza Medran  
- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Cordoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Redes de Computadoras** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**21/04/2026**

---

### Informacion de los autores

* **Informacion de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - constanza.medran@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

En este trabajo practico se abordaron conceptos fundamentales relacionados con el acceso a infraestructura virtualizada y la comunicacion en redes mediante distintos protocolos. Se trabajo con máquinas virtuales en la nube, estableciendo conexiones seguras utilizando SSH y analizando sus características de autenticacion y cifrado. 

Asimismo, se implementaron servidores simples utilizando netcat para protocolos TCP y UDP, permitiendo observar el proceso de comunicacion y el intercambio de datos entre clientes y servidores. Mediante el uso de Wireshark, se capturo y analizo el tráfico generado, identificando diferencias entre protocolos cifrados y no cifrados. 

Finalmente, se desplego un servidor HTTP básico, lo que permitio comprender el funcionamiento de los servicios web y evidenciar la exposicion de informacion cuando no se utilizan mecanismos de seguridad. Este trabajo permitio relacionar conceptos teoricos con su aplicacion práctica en entornos reales de red.

**Palabras clave**: *SSH, TCP, UDP, HTTP, Wireshark, virtualizacion, red, cifrado, netcat*

---

## Introduccion

El acceso a servicios y recursos en redes modernas se basa en el uso de protocolos que permiten la comunicacion entre dispositivos de manera eficiente y segura. En este contexto tecnologías como SSH, HTTP y herramientas como netcat resultan fundamentales para comprender como se establecen las conexiones, como se transmiten los datos y qué mecanismos de seguridad intervienen en estos procesos.

En este trabajo práctico se explora la interaccion con infraestructura virtualizada en la nube, permitiendo a los usuarios conectarse remotamente a máquinas virtuales y desplegar servicios básicos. A través de la experimentacion con distintos protocolos de transporte como TCP y UDP y el análisis de tráfico mediante herramientas como Wireshark, se busca comprender el comportamiento real de la red y las diferencias entre comunicaciones cifradas y no cifradas.

Además, se analiza el funcionamiento de servicios web básicos mediante la implementacion de un servidor HTTP, lo que permite evidenciar como se transmiten los datos en la red y los riesgos asociados a la falta de mecanismos de seguridad. De esta manera el trabajo integra conocimientos teoricos y prácticos, brindando una vision más completa del funcionamiento de las redes modernas.

---

## Marco teorico

En las comunicaciones de red, es importante distinguir entre autenticacion y cifrado. La autenticacion permite verificar la identidad de los participantes, mientras que el cifrado protege el contenido de los mensajes para que no pueda ser interpretado por terceros.

El protocolo SSH es un mecanismo de comunicacion que permite el acceso remoto seguro a sistemas a través de una red. Su principal característica es el uso de cifrado, lo que garantiza la confidencialidad e integridad de los datos transmitidos, a diferencia de otros protocolos que envían la informacion en texto plano. SSH utiliza criptografía de clave pública, donde una clave pública puede compartirse libremente y una clave privada debe mantenerse en secreto, permitiendo autenticacion segura sin necesidad de contraseñas. 

Los protocolos de transporte TCP y UDP son la base de la comunicacion entre aplicaciones. TCP es un protocolo orientado a conexion que garantiza la entrega de datos mediante mecanismos como el handshake, control de errores y retransmision. Por otro lado, UDP es un protocolo no orientado a conexion, más rápido pero sin garantías de entrega ni control de errores, lo que lo hace adecuado para aplicaciones donde la latencia es crítica.

El protocolo HTTP es utilizado para la transferencia de informacion en la web. Funciona bajo un modelo cliente servidor y en su version básica transmite los datos en texto plano, lo que implica riesgos de seguridad. Por esta razon en aplicaciones reales se utiliza HTTPS que incorpora cifrado mediante TLS.

Herramientas como Wireshark permiten capturar y analizar paquetes de red, facilitando la observacion del comportamiento de los protocolos y la estructura de los datos transmitidos. A través de su uso es posible evidenciar diferencias entre tráfico cifrado y no cifrado.

Finalmente, la virtualizacion y el uso de máquinas virtuales en la nube permiten simular entornos reales de red, facilitando la experimentacion con distintos servicios y protocolos sin necesidad de infraestructura física propia.

---

## Resultados

### Investigacion

...

### Conexion SSH

...

### Analisis de Paquete

...

### Despliegue de Servidores

...

### Servidor HTTP

...

### Hacking

...

---

## Discusion y conclusiones

...

---

## Referencias

[1] - ...
