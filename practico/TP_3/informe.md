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

Nuestro grupo trabajo con PC3 y PC4 para la realizacion de esta experiencia:

| PC3 | PC4 |
|---|---|
| 4.206.219.90 | 34.130.32.165 |

Comenzamos realizando una conexion por medio de SSH hacia la maquina virtual de PC3, utilizando el comando `ssh -i public_key.pem pc-alumnos-3@4.206.219.90`:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/addb16e6-9e01-4da8-957c-04703dda72b6" />

Una vez conectados documentamos nuestro paso por la VM generando una carpeta con el nombre de nuestro grupo.

<img width="400" alt="image" src="https://github.com/user-attachments/assets/cc52396d-1ffd-4d5c-a731-ee3672a24f34" />

### Analisis de Paquete

A continuacion utilizamos Wireshark para capturar el trafico SSH entre la PC propia y la maquina virtual remota:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/3158a343-22f9-45c3-84f8-4d1def4e78af" />

Escogimos un paquete y analizamos el contenido:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/f893ac4c-92c9-4778-b1b8-24f00fa47715" />

<img width="700" alt="image" src="https://github.com/user-attachments/assets/334f25a6-ed33-4c1a-a153-0028ec5de3cd" />

Observamos como no podemos visualizar la seccion de data en el mismo, y como logramos visualizar y descifrar el contenido.

Esto es porque SSH encripta todos los datos y Wireshark no puede desencriptarlos, esto solo puede realizarse en el destino con la llave privada.

### Despliegue de Servidores

Luego utilizamos netcat para desplegar servidores simples y capturar trafico.

Primero montamos un servidor TCP en el puerto 5050 de la maquina virtual:

<img width="500" alt="image" src="https://github.com/user-attachments/assets/9dde20d6-2c58-4a99-b433-ade93a05894f" />

Desde nuestra computadora local nos conectamos al servidor:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/a70c4075-4e53-419a-b416-cd4a14082dfd" />

Aqui enviamos un mensaje que es recibido en el servidor:

<img width="300" alt="image" src="https://github.com/user-attachments/assets/896f23e7-9720-41fc-9b25-84a466bcf0a2" /> </br>

<img width="500" alt="image" src="https://github.com/user-attachments/assets/0a2aa402-96be-4154-94d2-002d2b1c550e" />

Con Wireshark logramos capturar el handshake TCP de esta conexion:

<img width="1100" alt="image" src="https://github.com/user-attachments/assets/b243e174-9a89-4fc9-aa00-eed18f5b743a" />

Y logramos capturar el contenido del mensaje:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/1b2bd0c8-52e8-4815-a777-0ac89c09c289" />

A continuacion repetimos la experiencia con un servidor UDP en el puerto 5555:

<img width="400" alt="image" src="https://github.com/user-attachments/assets/18108dfc-c0fd-49ec-a135-167e74857aff" /> </br>

<img width="400" alt="image" src="https://github.com/user-attachments/assets/4571cacb-4c47-4394-bf1f-7ef36d3e5112" /></br>

<img width="700" alt="image" src="https://github.com/user-attachments/assets/da2044b1-09c9-4c88-af3f-45cca69e7646" /></br>

El ultimo paquete que podemos ver en el tablero de Wireshark corresponde al mensaje de las capturas.

Finalmente nos conectamos a la PC4, donde tambien registramos nuestra presencia:

<img width="700" alt="image" src="https://github.com/user-attachments/assets/c90a6700-4d61-473e-9957-e2edb4738a5f" />

Aqui establecimos una conexion netcat entre ambas maquinas virtuales y realizamos un ida y vuelta entre ellas:

https://github.com/user-attachments/assets/e27ae568-8825-44a5-9b13-8a033b60e5c6

### Servidor HTTP

En la PC3, navegamos a la carpeta de nuestro grupo y generamos un `index.html`, el cual utilizamos desplegando un servidor HTTP.

Si bien la consigna planteaba el comando con el puerto 8000, encontramos que en la VM un proceso ya estaba usando ese puerto. Intentamos utilizar el 8001 pero no conseguiamos llegar hacia la maquina virtual desde nuestra PC local por lo que determinamos que este no estaba habilitado para recibir trafico externo. Decidimos utilizar el puerto 5050 nuevamente que sabiamos podia recibir trafico:

<img width="500" alt="image" src="https://github.com/user-attachments/assets/aa34ee52-8056-40bf-aa9f-8f8c1da13e87" />

Con el servidor iniciado pudimos visualizar el contenido de nuestro html desde la PC local:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/b2e5c5ba-17dc-492b-a49b-450b9ebc8896" /> </br> </br>

<img width="500" alt="image" src="https://github.com/user-attachments/assets/b143ebb1-6c41-4f98-8709-10968c74f071" />

Y con Wireshark conseguimos capturar los paquetes HTTP donde podemos facilmente descifrar el contenido:

<img width="800" alt="image" src="https://github.com/user-attachments/assets/083f8b1d-f36c-4b00-af57-ac1f63a0bf00" /></br></br>

<img width="800" alt="image" src="https://github.com/user-attachments/assets/2e9c09c7-f46b-4bae-989b-236056dd2664" />

Determinamos que podriamos intervenir el contenido mediante un ataque Man in the Middle, ya que el contenido del paquete no esta cifrado y podemos ver el cuerpo y las cabeceras de este. Esto deja a la comunicacion vulnerable a la inyeccion de datos en el transito por la red.

### Hacking

El video de Veritasium detalla una vulnerabilidad muy interesante que ocurre al combinar la funcionalidad de Apple que permite pagar en el transporte publico sin requerir FaceID o PIN con la forma en que las tarjetas Visa manejan la criptografia en las transacciones. 

Al interceptar la comunicacion inalambrica los atacantes logran alterar los datos binarios en tiempo real para engañar al telefono haciéndole creer que esta pagando un pasaje de metro de bajo valor, mientras simultáneamente engañan a la terminal de pago real convenciendola de que el usuario verifico la transaccion, logrando asi evadir todas las capas de seguridad.

#### Relacion con Experiencias

**_TP #1 :_** En este practico observamos como los datos pueden ser modificados en transito, el tipo de exploit exacto utilizando en el video, un ataque de tipo Man in The Middle. Mientras que en nuestro caso se modificaba un bit random en transito, el ataque del video ataca bits especificos para modificar el comportamiento del receptor del mensaje.

**_TP #2 :_** En este practico observamos como viajan las tramas entre dispositivos, y el medio fisico de la conexion. En el ataque es precisamente el medio fisico el punto de ataque, explotando el campo magnetico donde se transmiten los bits. El ataque se inserta en el enlace de datos entre el iPhone y la terminal de pago, la capa exacta que vimos en la experiencia.

**_TP #3 :_** En este practico observamos la diferencia entre trafico plano y cifrado, a traves de SSH y HTTP/UDP/TCP, observando lo trivial que es leer los datos si estos no se cifran. Precisamente esto es lo que esta siendo explotado en el video, los datos viajan por el medio sin encriptacion, lo que permite leer la comunicacion entre los dispositivos, descifrar el funcionamiento de esta, y manipular la transmision de manera sencilla.

---

## Discusion y conclusiones

El trabajo permitio comprobar en la practica cómo los conceptos teoricos de redes se aplican en entornos reales. La experiencia con maquinas virtuales, conexiones remotas y analisis de tráfico facilito entender el comportamiento de los protocolos y visualizar tanto sus ventajas como sus riesgos.

Un resultado clave fue la comparacion entre comunicaciones cifradas y no cifradas. Mientras SSH protege la informacion e impide su lectura, protocolos como HTTP o el uso de netcat exponen completamente los datos, evidenciando la importancia del cifrado para garantizar la confidencialidad.

Tambien se comprendieron las diferencias entre TCP y UDP, donde el primero prioriza la confiabilidad mediante mecanismos de control, mientras que el segundo ofrece mayor rapidez a costa de no garantizar la entrega. Esto resalta la necesidad de elegir adecuadamente el protocolo segun el contexto.

Por otro lado, se identificaron limitaciones reales del entorno, como restricciones de puertos, que influyen en el despliegue de servicios. Ademas, el análisis del caso del video permitio relacionar los conceptos con vulnerabilidades reales, mostrando como la falta de seguridad puede ser explotada mediante ataques Man in the Middle.

En conclusion, el trabajo refuerza la importancia del uso de comunicaciones seguras y del analisis de tráfico como herramienta clave para comprender, diagnosticar y proteger redes en escenarios reales.

---

## Referencias

[1] - [Secure Shell](https://es.wikipedia.org/wiki/Secure_Shell)

[2] - [Netcat](https://www.ionos.com/es-us/digitalguide/servidores/herramientas/netcat/)

[3] - [Veritasium Exploit](https://www.youtube.com/watch?v=PPJ6NJkmDAo&t=1s)
