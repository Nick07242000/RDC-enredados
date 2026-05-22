# Trabajo Practico N°4

**Nombres**

- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Cordoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Teoria de Redes** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**14/05/2026**

---

### Informacion de los autores

* **Informacion de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - constanza.medran@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

En el presente trabajo practico se desarrollo un sistema basico de comunicacion cliente-servidor orientado a redes de computadoras, poniendo en practica conceptos fundamentales de transporte de datos, serializacion de informacion y seguridad en las comunicaciones.

Inicialmente, se implemento un servidor capaz de recibir mensajes enviados desde distintos clientes a traves de sockets TCP/IP, verificando el establecimiento correcto de la conexion y el intercambio confiable de informacion. Posteriormente, se desarrollo una aplicacion cliente configurable mediante direccion IP y puerto de destino, incorporando mecanismos de serializacion de datos compatibles con el protocolo definido por el servidor.

Ademas, se introdujo una capa basica de seguridad mediante la implementacion de tecnicas de cifrado aplicadas unicamente a la carga util (payload) de los mensajes transmitidos. Esto permitio analizar como la informacion puede viajar protegida a traves de la red, incluso cuando los paquetes son interceptados mediante herramientas de captura como Wireshark.

Finalmente, se verifico experimentalmente el correcto funcionamiento del sistema, evaluando la transmision de mensajes, la persistencia de conexiones TCP y el comportamiento del trafico cifrado durante la comunicacion entre cliente y servidor.

**Palabras clave**: *cliente-servidor, TCP/IP, sockets, serializacion, cifrado, payload, Wireshark, comunicaciones seguras*

---

## Introduccion

Las aplicaciones modernas dependen constantemente de mecanismos de comunicacion entre procesos distribuidos, donde clientes y servidores intercambian informacion a traves de redes de datos. Este modelo constituye la base de gran parte de los servicios actuales incluyendo plataformas web, aplicaciones moviles, sistemas IoT y servicios en la nube.

Para que estas comunicaciones sean eficientes y confiables es necesario comprender como se establecen las conexiones de red, como se estructuran los mensajes transmitidos y que mecanismos permiten garantizar la integridad y confidencialidad de la informacion intercambiada.

En este trabajo practico se aborda la implementacion de una arquitectura cliente-servidor utilizando sockets TCP/IP, profundizando en aspectos como la serializacion de datos y el envio persistente de mensajes. Ademas, se incorpora el estudio de tecnicas de cifrado aplicadas a la carga util de los paquetes, permitiendo analizar la importancia de la seguridad en redes y el impacto del cifrado sobre la observacion del trafico mediante herramientas de analisis de paquetes.

---

## Marco teorico

El modelo cliente-servidor es una arquitectura de comunicacion donde un dispositivo cliente solicita servicios o recursos a un servidor mediante una red. Este paradigma permite centralizar recursos y gestionar multiples conexiones simultaneas, siendo ampliamente utilizado en aplicaciones distribuidas y servicios de internet.

El protocolo TCP (Transmission Control Protocol) pertenece a la capa de transporte del modelo TCP/IP y proporciona una comunicacion orientada a conexion, confiable y ordenada entre dispositivos. TCP garantiza la entrega correcta de los datos mediante mecanismos de control de errores, confirmaciones (ACK) y retransmision de segmentos perdidos.

La serializacion consiste en transformar estructuras de datos u objetos en un formato que pueda transmitirse a traves de la red y posteriormente reconstruirse en el dispositivo receptor. Este proceso es fundamental para garantizar compatibilidad entre aplicaciones y sistemas heterogeneos.

Por otra parte, el cifrado de datos permite proteger la confidencialidad de la informacion transmitida mediante algoritmos criptograficos que transforman los datos originales en contenido ilegible para terceros no autorizados. En redes, el cifrado de la payload evita que la informacion sensible pueda interpretarse incluso si los paquetes son capturados durante la transmision.

Finalmente, herramientas de analisis de trafico como Wireshark permiten inspeccionar paquetes en tiempo real, analizar protocolos y verificar aspectos relacionados con conectividad, encapsulamiento y seguridad de las comunicaciones.

---

## Resultados

### Serializacion

> ¿Que es la serializacion en redes de computadoras?

Es el proceso de traducir una estructura de datos o el estado de un objeto que reside en la memoria de una computadora a un formato lineal que pueda ser transmitido a traves de una red o almacenado en un archivo.

Es tomar informacion compleja que una computadora entiende internamente y transformarla en una secuencia de bytes o texto para poder enviarla por un cable o conexion inalambrica.

Esto es porque las aplicaciones en la computadora o servidor trabajan con datos estructurados de formas complejas como objetos, listas, arboles, bases de datos con relaciones y referencias de memoria, etc. Sin embargo, las redes de computadoras no entienden de "objetos", solo entienden de flujos continuos de bits.

> ¿Cual es la diferencia entre serializacion binaria y no binaria?

La diferencia principal esta en como se codifican los datos antes de ser enviados por la red o guardados en un archivo.

La serializacion no binaria transforma los objetos en una cadena de caracteres alfanumericos y simbolos, utilizando codificaciones estandar como UTF-8 o ASCII.

La serializacion binaria transforma los objetos en un formato denso de bytes que esta optimizado para las maquinas, omitiendo caracteres innecesarios como espacios, corchetes o comillas.

Esta eleccion afecta directamente la velocidad, el tamaño de la informacion y la facilidad con la que los humanos pueden entenderla.

|Caracteristica|Serializacion No Binaria|Serializacion Binaria|
|---|---|---|
Formato de salida|"Cadenas de caracteres (Ej: {""edad"": 30})"|Secuencia de bytes (00011110...)
Legibilidad humana|Alta (se puede leer a simple vista)|Nula (requiere herramientas especiales)
Tamaño en red|Mayor (ocupa mas ancho de banda)|Menor (altamente comprimido y denso)
Velocidad de proceso|Mas lenta (requiere parsing de texto)|Muy rapida (procesamiento directo)
Facilidad de depuracion|Excelente|Compleja

> Buscar ejemplos, ventajas y desventajas de cada una.

Con respecto a la serializacion no binaria, el formado mas utilizado hoy en dia es JSON:

```json
{
  "nombre": "Ana",
  "edad": 28
}
```

Tiene como ventaja que es muy legible, cualquier persona puede leer el codigo y entender exactamente que datos se estan transmitiendo sin necesidad de un manual. Esto signfica que si hay un error de comunicacion entre dos sistemas, el programador puede inspeccionar el trafico de red y ver rapidamente si falta un dato o si esta mal escrito.

Con respecto a JSON, practicamente todos los lenguajes de programacion y navegadores web del mundo lo entienden de forma nativa sin necesidad de instalar librerias complejas. Su flexibilidad aporta a su popularidad, ya que se puede agregar campos nuevos sobre la marcha, y el sistema receptor generalmente no se rompera, simplemente ignorara lo que no necesite.

Sin embargo, tiene como desventaja el mayor ancho de banda que ocupa. Cada espacio, comilla, llave {} o etiqueta <usuario> ocupa bytes en la red. Cuando envias millones de estos registros, el desperdicio de datos es gigante. Esto implica un rendimiento mas lento, ya que la computadora que recibe el texto tiene que leerlo caracter por caracter para deducir que es un texto y que es un numero. Esto consume tiempo de procesador y bateria.

Por otro lado, en la serializacion binaria uno de los formatos mas populares es Protocol Buffers (Protobuf) de Google, donde cada parte de la comunicacion tiene un esquema previo de tipo:

```proto
message Usuario {
  string nombre = 1;
  int32 edad = 2;
}
```

Al serializar los datos el resultado que viaja por la red es un flujo de bytes incomprensible a simple vista, que en codigo hexadecimal se veria como:

```0a 03 41 6e 61 10 1c```

Esto tiene de ventaja el tamaño ultracompacto pasando de 29 a solo 7 bytes. En sistemas de alto volumen, esto significa ahorrar terabytes de ancho de banda y reducir costos de servidores.

Ademas, como no hay que analizar sintaxis la maquina decodifica estos bytes y los asigna a la memoria de forma casi instantanea.

Y nos da seguridad al tener un esquema obligatorio, si alguien intenta enviar la edad como texto en lugar de un numero el sistema lo rechaza inmediatamente evitando errores silenciosos en la base de datos.

Sin embargo, tiene como desventaja que es imposible de leer a simple vista. Para leerlo y depurar errores, se necesitan herramientas especiales y el archivo de esquema original.

Ademas adiciona complejidad al requerir instalar herramientas adicionales como compiladores de Protobuf. No es tan simple como abrir un archivo de texto y escribir datos. Tambien al querer agregar o quitar un campo en la estructura de datos, hay que actualizar el esquema en ambas maquinas siguiendo reglas muy cuidadosas para no romper la compatibilidad de los datos antiguos.

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

Para cifrar utilizamos una tecnica que se llama Fernet que es un estandar de cifrado simetrico autenticado basado en el algoritmo AES-128. 

Simetrico significa utiliza la misma clave tanto para ocultar el mensaje en el cliente como para revelarlo en el servidor. 

Su gran ventaja de seguridad es que genera un Vector de Inicializacion dinamico en cada ejecucion que hace que aunque se envie exactamente el mismo mensaje cien veces el resultado encriptado en el JSON siempre sera completamente diferente, impidiendo que un atacante intercepte el trafico y deduzca patrones.

Ademas tiene autenticacion e integridad integrada mediante HMAC-SHA256 que le da al mensaje que viaja una firma digital unica. Si alguien intenta alterar un solo bit de los datos en la red, el servidor lo detectara de inmediato y lanzara un error rechazando el paquete. 

Finalmente tambien incluye un timestamp interno que permite verificar cuando se creo el mensaje que permite proteger contra ataques de repeticion de forma automatica.

### Decipher

Finalmente modificamos el servidor, para que el mismo sea capaz de descifrar el payload cifrado.

<img width="1980" height="1198" alt="image" src="https://github.com/user-attachments/assets/7062e471-6cfe-4bb2-9def-a65d0eae85f2" />

Vemos como el servidor recibe el mensaje descifrado:

<img width="467" height="136" alt="image" src="https://github.com/user-attachments/assets/eb923358-8b01-44ba-a2b4-d6cdba28298c" />

Y com Wireshark podemos ver como el payload viajo cifrado hasta el servidor:

<img width="1770" height="802" alt="image" src="https://github.com/user-attachments/assets/34201b99-ad8a-4b53-be83-876d37eb39cd" />

Agregando un log podemos ver como coincide el payload predescifrado con lo visualizado en Wireshark:

<img width="1438" height="895" alt="image" src="https://github.com/user-attachments/assets/75cfd709-89d2-4030-a5bc-49d9dc26ac61" />

---

## Discusion y conclusiones

## Discusion y conclusiones

El estudio de la serializacion permitio analizar la importancia de transformar estructuras complejas de datos en formatos transmisibles por red. La comparacion entre serializacion binaria y no binaria mostro claramente el compromiso existente entre legibilidad humana, eficiencia y rendimiento. En este contexto, JSON resulto especialmente util para tareas de depuracion y pruebas debido a su simplicidad y amplia compatibilidad.

Uno de los aspectos mas relevantes del trabajo fue la incorporacion de mecanismos de seguridad mediante cifrado simetrico utilizando Fernet. La implementacion permitio observar experimentalmente como la carga util de los mensajes puede protegerse frente a la inspeccion directa del trafico de red. Mediante Wireshark se comprobo que, aunque los paquetes pueden capturarse durante la transmision, el contenido permanece ilegible sin la clave correspondiente, evidenciando la importancia del cifrado en sistemas distribuidos modernos.

Asimismo, la modificacion del servidor para incorporar el descifrado de la payload permitio comprender el funcionamiento completo de una comunicacion segura extremo a extremo, incluyendo autenticacion e integridad de datos mediante HMAC. Esto permitio relacionar directamente conceptos teoricos de criptografia con aplicaciones practicas reales.

Como limitacion, el sistema implementado utiliza un mecanismo de seguridad relativamente basico y centralizado, donde cliente y servidor comparten la misma clave simetrica. En sistemas reales de produccion suelen emplearse protocolos mas robustos, como TLS, junto con esquemas de intercambio seguro de claves y certificados digitales.

En conclusion, el trabajo permitio integrar conocimientos de redes, programacion y seguridad informatica en un entorno practico y experimental. La experiencia adquirida facilito la comprension de como funcionan internamente las comunicaciones modernas, destacando la importancia de la serializacion, el transporte confiable y el cifrado para construir aplicaciones distribuidas seguras y eficientes.

---

## Referencias

[1] - [Cryptography.py](https://cryptography.io/en/latest/)

[2] - [Fernet](https://github.com/fernet/spec/)
