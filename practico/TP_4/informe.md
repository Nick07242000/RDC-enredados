# Trabajo Practico N°4

**Nombres**

- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Córdoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Teoria de Redes** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**14/05/2026**

---

### Información de los autores

* **Información de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - constanza.medran@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

En el presente trabajo práctico se desarrolló un sistema básico de comunicación cliente-servidor orientado a redes de computadoras, poniendo en práctica conceptos fundamentales de transporte de datos, serialización de información y seguridad en las comunicaciones.

Inicialmente, se implementó un servidor capaz de recibir mensajes enviados desde distintos clientes a través de sockets TCP/IP, verificando el establecimiento correcto de la conexión y el intercambio confiable de información. Posteriormente, se desarrolló una aplicación cliente configurable mediante dirección IP y puerto de destino, incorporando mecanismos de serialización de datos compatibles con el protocolo definido por el servidor.

Además, se introdujo una capa básica de seguridad mediante la implementación de técnicas de cifrado aplicadas únicamente a la carga útil (payload) de los mensajes transmitidos. Esto permitió analizar cómo la información puede viajar protegida a través de la red, incluso cuando los paquetes son interceptados mediante herramientas de captura como Wireshark.

Finalmente, se verificó experimentalmente el correcto funcionamiento del sistema, evaluando la transmisión de mensajes, la persistencia de conexiones TCP y el comportamiento del tráfico cifrado durante la comunicación entre cliente y servidor.

**Palabras clave**: *cliente-servidor, TCP/IP, sockets, serialización, cifrado, payload, Wireshark, comunicaciones seguras*

---

## Introducción

Las aplicaciones modernas dependen constantemente de mecanismos de comunicación entre procesos distribuidos, donde clientes y servidores intercambian información a través de redes de datos. Este modelo constituye la base de gran parte de los servicios actuales incluyendo plataformas web, aplicaciones móviles, sistemas IoT y servicios en la nube.

Para que estas comunicaciones sean eficientes y confiables es necesario comprender cómo se establecen las conexiones de red, cómo se estructuran los mensajes transmitidos y qué mecanismos permiten garantizar la integridad y confidencialidad de la información intercambiada.

En este trabajo práctico se aborda la implementación de una arquitectura cliente-servidor utilizando sockets TCP/IP, profundizando en aspectos como la serialización de datos y el envío persistente de mensajes. Ademas, se incorpora el estudio de técnicas de cifrado aplicadas a la carga útil de los paquetes, permitiendo analizar la importancia de la seguridad en redes y el impacto del cifrado sobre la observación del tráfico mediante herramientas de análisis de paquetes.

---

## Marco teórico

El modelo cliente-servidor es una arquitectura de comunicación donde un dispositivo cliente solicita servicios o recursos a un servidor mediante una red. Este paradigma permite centralizar recursos y gestionar múltiples conexiones simultáneas, siendo ampliamente utilizado en aplicaciones distribuidas y servicios de internet.

El protocolo TCP (Transmission Control Protocol) pertenece a la capa de transporte del modelo TCP/IP y proporciona una comunicación orientada a conexión, confiable y ordenada entre dispositivos. TCP garantiza la entrega correcta de los datos mediante mecanismos de control de errores, confirmaciones (ACK) y retransmisión de segmentos perdidos.

La serialización consiste en transformar estructuras de datos u objetos en un formato que pueda transmitirse a través de la red y posteriormente reconstruirse en el dispositivo receptor. Este proceso es fundamental para garantizar compatibilidad entre aplicaciones y sistemas heterogéneos.

Por otra parte, el cifrado de datos permite proteger la confidencialidad de la información transmitida mediante algoritmos criptográficos que transforman los datos originales en contenido ilegible para terceros no autorizados. En redes, el cifrado de la payload evita que la información sensible pueda interpretarse incluso si los paquetes son capturados durante la transmisión.

Finalmente, herramientas de análisis de tráfico como Wireshark permiten inspeccionar paquetes en tiempo real, analizar protocolos y verificar aspectos relacionados con conectividad, encapsulamiento y seguridad de las comunicaciones.
---

## Resultados

### Serializacion

> ¿Qué es la serialización en redes de computadoras?

Es el proceso de traducir una estructura de datos o el estado de un objeto que reside en la memoria de una computadora a un formato lineal que pueda ser transmitido a través de una red o almacenado en un archivo.

Es tomar información compleja que una computadora entiende internamente y transformarla en una secuencia de bytes o texto para poder enviarla por un cable o conexión inalámbrica.

Esto es porque las aplicaciones en la computadora o servidor trabajan con datos estructurados de formas complejas como objetos, listas, árboles, bases de datos con relaciones y referencias de memoria, etc. Sin embargo, las redes de computadoras no entienden de "objetos", solo entienden de flujos continuos de bits.

> ¿Cuál es la diferencia entre serialización binaria y no binaria?

La diferencia principal esta en cómo se codifican los datos antes de ser enviados por la red o guardados en un archivo.

La serialización no binaria transforma los objetos en una cadena de caracteres alfanuméricos y símbolos, utilizando codificaciones estándar como UTF-8 o ASCII.

La serialización binaria transforma los objetos en un formato denso de bytes que está optimizado para las máquinas, omitiendo caracteres innecesarios como espacios, corchetes o comillas.

Esta elección afecta directamente la velocidad, el tamaño de la información y la facilidad con la que los humanos pueden entenderla.

|Característica|Serialización No Binaria|Serialización Binaria|
|---|---|---|
Formato de salida|"Cadenas de caracteres (Ej: {""edad"": 30})"|Secuencia de bytes (00011110...)
Legibilidad humana|Alta (se puede leer a simple vista)|Nula (requiere herramientas especiales)
Tamaño en red|Mayor (ocupa más ancho de banda)|Menor (altamente comprimido y denso)
Velocidad de proceso|Más lenta (requiere parsing de texto)|Muy rápida (procesamiento directo)
Facilidad de depuración|Excelente|Compleja

> Buscar ejemplos, ventajas y desventajas de cada una.

Con respecto a la serializacion no binaria, el formado mas utilizado hoy en dia es JSON:

```json
{
  "nombre": "Ana",
  "edad": 28
}
```

Tiene como ventaja que es muy legible, cualquier persona puede leer el código y entender exactamente qué datos se están transmitiendo sin necesidad de un manual. Esto signfica que si hay un error de comunicación entre dos sistemas, el programador puede inspeccionar el tráfico de red y ver rápidamente si falta un dato o si está mal escrito.

Con respecto a JSON, prácticamente todos los lenguajes de programación y navegadores web del mundo lo entienden de forma nativa sin necesidad de instalar librerías complejas. Su flexibilidad aporta a su popularidad, ya que se puede agregar campos nuevos sobre la marcha, y el sistema receptor generalmente no se romperá, simplemente ignorará lo que no necesite.

Sin embargo, tiene como desventaja el mayor ancho de banda que ocupa. Cada espacio, comilla, llave {} o etiqueta <usuario> ocupa bytes en la red. Cuando envías millones de estos registros, el desperdicio de datos es gigante. Esto implica un rendimiento mas lento, ya que la computadora que recibe el texto tiene que leerlo carácter por carácter para deducir qué es un texto y qué es un número. Esto consume tiempo de procesador y batería.

Por otro lado, en la serializacion binaria uno de los formatos más populares es Protocol Buffers (Protobuf) de Google, donde cada parte de la comunicacion tiene un esquema previo de tipo:

```proto
message Usuario {
  string nombre = 1;
  int32 edad = 2;
}
```

Al serializar los datos el resultado que viaja por la red es un flujo de bytes incomprensible a simple vista, que en código hexadecimal se vería como:

```0a 03 41 6e 61 10 1c```

Esto tiene de ventaja el tamaño ultracompacto pasando de 29 a solo 7 bytes. En sistemas de alto volumen, esto significa ahorrar terabytes de ancho de banda y reducir costos de servidores.

Ademas, como no hay que analizar sintaxis la máquina decodifica estos bytes y los asigna a la memoria de forma casi instantánea.

Y nos da seguridad al tener un esquema obligatorio, si alguien intenta enviar la edad como texto en lugar de un número el sistema lo rechaza inmediatamente evitando errores silenciosos en la base de datos.

Sin embargo, tiene como desventaja que es imposible de leer a simple vista. Para leerlo y depurar errores, se necesitan herramientas especiales y el archivo de esquema original.

Ademas adiciona complejidad al requerir instalar herramientas adicionales como compiladores de Protobuf. No es tan simple como abrir un archivo de texto y escribir datos. Tambien al querer agregar o quitar un campo en la estructura de datos, hay que actualizar el esquema en ambas máquinas siguiendo reglas muy cuidadosas para no romper la compatibilidad de los datos antiguos.

### Multithreaded TCP Server

Nuestro grupo realizo esta actividad de forma presencial, donde se levanto un servidor para usar de forma conjunta y cada equipo enviaba su payload serializada en ASCII desde su propio cliente a el servidor.

Para esto generamos nuestra payload con la estructura apropiada:

<img width="1366" height="768" alt="IMG-20260519-WA0016" src="https://github.com/user-attachments/assets/37f86427-d813-4dab-8313-6f91cbd5f071" />

Luego utilizando Packet Sender nos conectamos por medio de TCP al servidor:

<img width="1366" height="768" alt="IMG-20260519-WA0015" src="https://github.com/user-attachments/assets/db2e7497-a4ff-429d-96a7-dd8b6b1ce38c" />

Y enviamos el paquete codificado, el cual logramos visualizar en el output del servidor descerializado (nuestra IP es 181.238.18.10):

<img width="2046" height="1150" alt="1779235815342" src="https://github.com/user-attachments/assets/9c90652c-5412-490d-bb49-b8a37b8d5e41" />

### Client

A continuacion, utilizamos el cliente disponible en Drive para enviar mensajes al servidor.

Configuramos el mismo con la direccion IP y el puerto del servidor y serializamos la informacion antes del envio:

<img width="1366" height="768" alt="IMG-20260519-WA0014" src="https://github.com/user-attachments/assets/dc0483c7-1870-474e-8ecb-42e333be2f4a" />

Al ejecutar nuestro cliente vemos como se reciben los mensajes deserializados en el servidor.

<img width="2046" height="1150" alt="1779235815316" src="https://github.com/user-attachments/assets/cb45ca64-44c4-4b35-83b0-b68fe86f915f" />

### Security

A continuacion, nos apoyamos en la libreria `cryptography` de Python para encriptar nuestro mensaje.

<img width="696" height="577" alt="image" src="https://github.com/user-attachments/assets/44d281d9-e8ca-411a-8b12-f9505fa6d75e" />

Aqui, generamos una key simetrica, la cual utilizamos para encriptar nuestro mensaje y enviarlo al servidor serializado, donde el mensaje es recibido pero ahora el contenido no es legible:

<img width="2046" height="1150" alt="1779235815295" src="https://github.com/user-attachments/assets/57da9cea-28be-44bc-bcba-7f77ae2a8bf7" />

### Decipher

_this is optional_

---

## Discusión y conclusiones

...

---

## Referencias

[1] - ...
