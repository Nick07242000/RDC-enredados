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

En este trabajo practico se abordaron conceptos fundamentales relacionados con el acceso a infraestructura virtualizada y la comunicacion en redes mediante distintos protocolos. Se trabajo con maquinas virtuales en la nube, estableciendo conexiones seguras utilizando SSH y analizando sus características de autenticacion y cifrado. 

Asimismo, se implementaron servidores simples utilizando netcat para protocolos TCP y UDP, permitiendo observar el proceso de comunicacion y el intercambio de datos entre clientes y servidores. Mediante el uso de Wireshark, se capturo y analizo el trafico generado, identificando diferencias entre protocolos cifrados y no cifrados. 

Finalmente, se desplego un servidor HTTP basico, lo que permitio comprender el funcionamiento de los servicios web y evidenciar la exposicion de informacion cuando no se utilizan mecanismos de seguridad. Este trabajo permitio relacionar conceptos teoricos con su aplicacion practica en entornos reales de red.

**Palabras clave**: *SSH, TCP, UDP, HTTP, Wireshark, virtualizacion, red, cifrado, netcat*

---

## Introduccion

El acceso a servicios y recursos en redes modernas se basa en el uso de protocolos que permiten la comunicacion entre dispositivos de manera eficiente y segura. En este contexto tecnologías como SSH, HTTP y herramientas como netcat resultan fundamentales para comprender como se establecen las conexiones, como se transmiten los datos y qué mecanismos de seguridad intervienen en estos procesos.

En este trabajo practico se explora la interaccion con infraestructura virtualizada en la nube, permitiendo a los usuarios conectarse remotamente a maquinas virtuales y desplegar servicios basicos. A través de la experimentacion con distintos protocolos de transporte como TCP y UDP y el analisis de trafico mediante herramientas como Wireshark, se busca comprender el comportamiento real de la red y las diferencias entre comunicaciones cifradas y no cifradas.

Ademas, se analiza el funcionamiento de servicios web basicos mediante la implementacion de un servidor HTTP, lo que permite evidenciar como se transmiten los datos en la red y los riesgos asociados a la falta de mecanismos de seguridad. De esta manera el trabajo integra conocimientos teoricos y practicos, brindando una vision mas completa del funcionamiento de las redes modernas.

---

## Marco teorico

Los protocolos de transporte TCP y UDP son la base de la comunicacion entre aplicaciones. TCP es un protocolo orientado a conexion que garantiza la entrega de datos mediante mecanismos como el handshake, control de errores y retransmision. Por otro lado, UDP es un protocolo no orientado a conexion, mas rapido pero sin garantías de entrega ni control de errores, lo que lo hace adecuado para aplicaciones donde la latencia es crítica.

El protocolo HTTP es utilizado para la transferencia de informacion en la web. Funciona bajo un modelo cliente servidor y en su version basica transmite los datos en texto plano, lo que implica riesgos de seguridad. Por esta razon en aplicaciones reales se utiliza HTTPS que incorpora cifrado mediante TLS.

Herramientas como Wireshark permiten capturar y analizar paquetes de red, facilitando la observacion del comportamiento de los protocolos y la estructura de los datos transmitidos. A través de su uso es posible evidenciar diferencias entre trafico cifrado y no cifrado.

Finalmente, la virtualizacion y el uso de maquinas virtuales en la nube permiten simular entornos reales de red, facilitando la experimentacion con distintos servicios y protocolos sin necesidad de infraestructura física propia.

---

## Resultados

### Investigacion

_¿Qué es SSH y qué problema resuelve?_

Secure Shell (SSH( es un protocolo de red que permite conectarse de forma segura a otro sistema, especialmente para administracion remota.  
Su objetivo principal es evitar que la informacion viaje en texto plano, utilizando cifrado y mecanismos de autenticacion para proteger la comunicacion frente a interceptaciones.

_Diferencia entre autenticacion y cifrado_

La autenticacion es el proceso de verificar la identidad de un usuario o sistema mientras que el cifrado es la técnica de proteger los datos transformandolos en un formato ilegible para terceros.  
En otras palabras, la autenticacion responde “quién sos” y el cifrado responde “qué tan protegida esta la informacion”.

_¿Qué es una clave pública y una clave privada?_

Una clave pública y una clave privada forman un par en criptografía asimétrica donde la clave pública puede compartirse libremente y se utiliza para cifrar datos o verificar firmas mientras que la clave privada debe mantenerse en secreto y se usa para descifrar o firmar.  
Ambas estan matematicamente relacionadas, pero no es posible obtener la privada a partir de la pública.

_¿Por qué la clave privada no debe compartirse?_

La clave privada no debe compartirse porque representa la identidad del usuario en un sistema seguro.  
Si otra persona la obtiene puede autenticarse como si fuera el propietario legítimo, acceder a sistemas protegidos y comprometer informacion, lo que equivale a una pérdida total de seguridad.

_¿Qué ventajas tienen las claves SSH frente a contraseñas?_

- Son mucho mas difíciles de vulnerar mediante ataques de fuerza bruta.
- No se transmiten por la red durante la autenticacion.
- Permiten automatizar conexiones seguras sin intervencion humana.
- Reducen el riesgo de ataques como phishing.
- Facilitan una gestion mas controlada de accesos.

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
