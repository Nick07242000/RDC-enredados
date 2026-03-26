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

EDAC (Error Detection And Correction) es un conjunto de técnicas utilizadas en sistemas digitales y de comunicaciones para garantizar la integridad de los datos, permitiendo detectar y, en algunos casos, corregir errores que pueden producirse durante la transmisión o el almacenamiento. Estos errores pueden originarse por interferencias, ruido o fallas de hardware.

Dentro de las técnicas de EDAC, una de las más simples es la **paridad**, la cual se utiliza principalmente para la detección de errores. Este método consiste en agregar un bit adicional a una secuencia de datos, denominado bit de paridad, cuyo valor se determina en función de la cantidad de bits en ‘1’ presentes en el mensaje. Existen dos tipos principales de paridad: la paridad par, donde se busca que la cantidad total de unos sea un número par, y la paridad impar, donde se busca que sea impar. En nuestro caso, tomaremos la paridad par, por lo que si la cantidad de 1 es par, el bit de paridad es 0.

La segunda técnica es la de **XOR** en donde se realizan combinaciones específicas de bits mediante XOR para generar información redundante adicional. En este caso, se toma el primer nibble y se aplica la operación XOR con el segundo nibble. El resultado, se utiliza para hacer otra operación XOR con el tercer nibble y así hasta el último nibble cuyo resultado es el código EDAC. Esta información permite no solo detectar la presencia de errores, sino también identificar su posición exacta y corregirlos automáticamente.


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
|10.8.0.1|AA:43:80

### Conformación de paquetes

Cada uno de los hosts genero un paquete para ser transmitido a traves de la red, con un payload y un destino en particular:

|MAC DESTINO|MAC ORIGEN|IP ORIGEN|IP DESTINO|TTL|PAYLOAD
|---|---|---|---|---|---|
|AA:44:64|AD:43:93|10.13.0.101|10.2.0.101|6|1101010010011010
|AA:44:64|AC:44:54|10.13.0.102|10.7.0.101|6|1000000110100101
|AA:44:64|AD:42:07|10.13.0.103|10.4.0.104|6|001100011001

### Simular las transmisiones y recepciones

Estos paquetes fueron enviados al default gateway para ser entregado al destino final, donde cada router desempaqueto y empaqueto los frames de acuerdo al recorrido de los mismo a traves de ethernet.

**Recepción de Frame Ethernet:**

Se recibió el siguiente frame:

<img src="https://github.com/user-attachments/assets/4c6a20f4-0716-4f64-8b6e-b9cfc1560302" width="300">

|MAC DESTINO|MAC ORIGEN|IP ORIGEN|IP DESTINO|TTL|PAYLOAD
|---|---|---|---|---|---|
|AD:43.93|AD:44:54|10.14.0.104|10.13.0.101|2|0011010101011011

### Reflexiones y documentación
La dirección IP se mantiene constante durante todo el trayecto porque actúa como un identificador global, permitiendo que los nodos intermedios determinen la ruta hacia el host de destino final sin importar cuántas subredes deba atravesar el paquete. En contraste, la dirección MAC cambia en cada salto debido a que su alcance es estrictamente local y solo sirve para la entrega física dentro de un mismo segmento de red; por lo tanto, cada router debe desencapsular el frame Ethernet para procesar la IP de destino y, tras consultar su tabla de ruteo, volver a encapsular el paquete en un nuevo frame con la MAC de destino del siguiente dispositivo  obtenida mediante el protocolo ARP, asegurando así que el mensaje avance físicamente de un nodo a otro hasta alcanzar su destino final.

El gateway se encarga de resolver la incapacidad del host para alcanzar destinos fuera de su propia red local. Debido al protocolo ARP , un host no tiene forma de obtener la direccion MAC del dispositivo destino fuerda de red, ni conoce las rutas externas para encaminar el paquete. Entonces esta Default gateway actua como intermediario, recibe los paquetes para dispositivos externos y utiliza su tabla de ruteo para reenviarlos hacia la red correcta funcionando como unico punto de salida.

El modelo de ruteo hop-by-hop ofrece ventajas en términos de escalabilidad, eficiencia y resiliencia para redes de gran escala. Al basar las decisiones únicamente en tablas de ruteo locales, se evita que cada dispositivo deba conocer la topología completa de internet, lo cual sería técnicamente imposible debido al volumen de datos y al procesamiento requerido. Este diseño permite que la red sea altamente dinámica: si un enlace se cae o un router falla, el resto de los nodos simplemente actualizan su "siguiente salto" para rodear el problema sin necesidad de que el emisor original sepa qué ocurrió. De esta forma descentraliza la red haciendola robusta ante fallos.

Es obligatorio reconstruir el frame Ethernet en cada salto porque las direcciones MAC solo tienen validez dentro de una red local y sirven para mover el dato entre dos equipos vecinos. Si un router reenviara el frame original sin cambios, este contendría la MAC de destino del salto anterior, provocando que el paquete sea descartado por los nuevos dispositivos al no reconocerlo como propio.

El mecanismo de decremento del TTL previene el bucle infinito (routing loop) de paquetes en la red, un problema que ocurre cuando hay errores en las tablas de ruteo que hacen que un paquete circule eternamente entre dos o más routers sin alcanzar nunca su destino. Si el TTL no existiera, estos paquetes "huérfanos" nunca serían eliminados, acumulándose de forma indefinida hasta saturar el ancho de banda y consumir todos los recursos de procesamiento de los routers, lo que provocaría un colapso total de la red. Cuando el contador llega a cero, el router descarta el paquete y envía un mensaje ICMP de "Time Exceeded" al origen, garantizando que la red se mantenga limpia de tráfico basura.

### Inyección y detección de errores

Parte 2. **Inyección y detección de errores**

El ejercicio es simple:

a. Routers no default gateway (sin LAN debajo): al momento de re-empaquetar los paquetes, modificar (o no) en uno o más bits la payload. Documentar de manera secreta qué paquetes fueron modificados y que paquetes no (registrar payload + destino). Reenviar el paquete.

En este ejercicio, la modificación de la payload fue realizada por el profesor, quien actúa como un agente que introduce errores de forma controlada en los paquetes, simulando condiciones reales de transmisión en las que pueden ocurrir corrupciones de datos debido a ruido o interferencias y luego también realizo el reenvío de los paquetes entre los grupos. 
Se establece como base que el código EDAC es correcto.

b. Hosts / End devices: al enviar paquetes aplicar técnicas de EDAC. Al recibir paquetes,
determinar si fueron o no modificados. Justificar.

Envío de paquete:

Se nos entregó un payload en hexadecimal, el cual teníamos que pasar a binario	y luego calcular el EDAC con la **técnica de paridad** y con ello, completar un frame para simular el envío de este a otra IP.

payload hexadecimal: 9e06
payload binario: 1001 1110 0000 0110

Cálculo de bits de paridad: se agrupan nibbles y sobre estos se calcula el bit de paridad de cada uno. como hay 4 nibbles, van a haber 4 bits de paridad:

1001: el número de 1 es 2 (par) por lo tanto el bit de paridad es 0.
1110: el número de 1 es 3 (impar) por lo tanto el bit de paridad es 1.
0000: el número de 1 es 0 (par) por lo tanto el bit de paridad es 0.
0110: el número de 1 es 2 (par) por lo tanto el bit de paridad es 0.

EDAC paridad: 0 1 0 0
IP origen: 10.13.0.101

Esta información se envió a otro grupo para la parte dos.

Recepción de paquete:

Se recibió un frame enviado por otro grupo el cual contenía un payload, una dirección IP origen y destino y un código EDAC con **técnica XOR**. 

<img src="https://github.com/user-attachments/assets/9fd6feca-3c25-43ba-b225-4b3eadefb6ef" width="800">

Para confirmar si el payload no fue modificado sobre el payload realizamos las operaciones de XOR para comparar si el código EDAC que nos daba como resultado era el mismo que el código que se recibió en el frame.

1001 XOR 1100 = 0101

0101 XOR 1111 = 1010

1010 XOR 0101 = 1111

Esto daría como EDAC **1111** y como nos dieron diferentes códigos, podemos confirmar que el payload fue modificado. 

---

## Discusión y conclusiones

En este ejercicio aplicamos técnicas de EDAC para verificar si los datos se modificaban durante la transmisión. En el envío usamos paridad por nibble, que es un método simple para detectar errores, aunque no es totalmente confiable para todos los casos.

En la recepción usamos XOR para recalcular el EDAC y compararlo con el que venía en el frame. Como los resultados no coincidieron, pudimos concluir que el payload fue modificado. En este caso, la modificación fue intencional, pero sirve para simular errores reales en la red.

Las técnicas vistas permiten detectar errores en los datos transmitidos.
La paridad es útil pero limitada, mientras que XOR resulta más confiable para este tipo de verificación.

En este caso, como los EDAC no coincidieron, se confirmó que hubo una alteración en el mensaje. Esto demuestra la importancia de estos métodos para asegurar la integridad de la información en redes y la dificultad de poder predecir (al menos a mano) que bit se cree que se cree que fue modificado.

---

## Referencias

[1] - Stallings - Comunicacion y Redes de Computadores 
