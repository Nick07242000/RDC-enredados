# Trabajo Practico N°5

**Nombres**

- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Cordoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Teoria de Redes** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**08/06/2026**

---

### Informacion de los autores

* **Informacion de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

En el presente trabajo practico se analizan conceptos fundamentales de arquitectura de servicios e infraestructura cloud mediante el uso de un simulador de sistemas distribuidos. 

A traves de diferentes escenarios de carga y procesamiento de trafico, se estudia el comportamiento de componentes habituales en plataformas modernas, tales como balanceadores de carga, bases de datos, sistemas de cache, colas de mensajes, redes de distribucion de contenido y mecanismos de filtrado de trafico.

Asimismo, se evalua como distintos tipos de solicitudes impactan sobre los recursos del sistema y como las decisiones de diseño influyen en la disponibilidad, escalabilidad y rendimiento de los servicios. 

Se exploran tambien estrategias para mejorar la capacidad de procesamiento mediante tecnicas de escalamiento horizontal, balanceo de carga y separacion funcional de componentes.

Finalmente, se analizan los principales cuellos de botella que aparecen en arquitecturas distribuidas y se discute la importancia de una correcta planificacion de infraestructura para garantizar la continuidad operativa frente a incrementos de trafico o situaciones adversas.

**Palabras clave**: *cloud computing, escalabilidad, balanceo de carga, cache, bases de datos, colas de mensajes, CDN, infraestructura distribuida, disponibilidad, rendimiento*

---

## Introduccion

Las aplicaciones modernas deben atender volumenes crecientes de usuarios y datos, manteniendo simultaneamente altos niveles de disponibilidad, rendimiento y tolerancia a fallos. 

Para lograr estos objetivos, las arquitecturas de software actuales se apoyan en una amplia variedad de componentes especializados que permiten distribuir la carga de trabajo, optimizar el acceso a la informacion y proteger los servicios frente a fallos o ataques.

En entornos cloud, conceptos como balanceo de carga, almacenamiento distribuido, sistemas de cache, bases de datos escalables y procesamiento desacoplado mediante colas de mensajes forman parte de la infraestructura basica de numerosas aplicaciones web y servicios digitales.

El objetivo de este trabajo practico es analizar el funcionamiento de estos componentes a traves de un entorno de simulacion que permite observar como una arquitectura responde frente a diferentes tipos de trafico y niveles de demanda. 

A partir de la construccion y evaluacion de diversas configuraciones, se busca comprender los mecanismos que permiten mejorar la escalabilidad y la resiliencia de los sistemas, asi como identificar los factores que pueden convertirse en cuellos de botella dentro de una infraestructura distribuida.

---

## Marco teorico

Las arquitecturas modernas basadas en servicios distribuidos utilizan multiples componentes especializados para procesar, almacenar y distribuir informacion de manera eficiente. El objetivo principal de estas arquitecturas es garantizar disponibilidad, escalabilidad y tolerancia a fallos frente a variaciones de carga o eventos inesperados.

Los balanceadores de carga (Load Balancers) permiten distribuir solicitudes entre multiples servidores, evitando la sobrecarga de instancias individuales y mejorando la disponibilidad del servicio. Complementariamente, el escalamiento horizontal consiste en agregar nuevas instancias de procesamiento para incrementar la capacidad total del sistema.

Las colas de mensajes (Queues) permiten desacoplar productores y consumidores de informacion, absorbiendo picos de trafico y evitando que las aplicaciones colapsen ante incrementos repentinos de solicitudes.

Los sistemas de cache almacenan temporalmente informacion de acceso frecuente para reducir la carga sobre bases de datos y disminuir los tiempos de respuesta.

Las bases de datos SQL y NoSQL constituyen el nucleo del almacenamiento de informacion. Mientras que las bases SQL priorizan la consistencia y las relaciones estructuradas entre datos, las bases NoSQL ofrecen mayor flexibilidad y escalabilidad para aplicaciones con grandes volumenes de informacion.

Asimismo, las CDN (Content Delivery Networks) y los sistemas de almacenamiento estatico permiten distribuir contenido de forma eficiente hacia usuarios geograficamente dispersos, reduciendo latencia y consumo de recursos de los servidores principales.

Finalmente, componentes como firewalls, sistemas de filtrado de trafico y mecanismos de replicacion contribuyen a mejorar la seguridad, disponibilidad y resiliencia de la infraestructura, permitiendo que los servicios continuen operando incluso ante fallos parciales o intentos de acceso malicioso.

---

## Resultados

### Reconocimiento de Arquitectura

> Identificá qué función cumple cada uno de estos elementos:

| Elemento            | Funcion                                                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------------------- |
| Firewall            | Primera linea de defensa, bloquea trafico maliciosa que puede destruir la reputacion                     |
| Load Balancer       | Distribuye el trafico a multiple servidores, lo que previene sobre carga y mejora la confiabilidad       |
| Queue               | Almacena temporalmente requests para prevenir caidas ante picos de trafico                               |
| Compute             | Procesa todas las request, rutea el trafico al destino correcto a Storage o Database                     |
| Serverless Function | Sirve para atender trafico no constante eventual de bajo volumen                                         |
| SQL DB              | Atiende requests de lectura, escritura y busqueda                                                        |
| NoSQL               | Atiende requests de lectura y escritura de forma mas rapida y barata pero no atiende trafico de busqueda |
| Cache               | Reduce la carga de la base de datos cacheando respuestas                                                 |
| CDN                 | Mejora la velocida de la entrega de contenido estatico                                                   |
| Storage             | Almacena contenido estatico o subidas de contenido                                                       |
| Search Engine       | Procesa trafico de busqueda tres veces mas rapido que SQL, solo atiende busqueda                         |
| Réplica             | Procesa trafico de lectura mas rapido que la DB maestra a la que esta conectada                          |

> Para cada uno, respondé brevemente:
> a) ¿Qué problema resuelve?
> b) ¿En qué capa o capas del modelo TCP/IP podríamos ubicar su función principal?
> c) ¿Qué pasaría si ese componente falta en una arquitectura real?

| Elemento                | Problema Resuelve                                                                             | Capa TCP/IP             | ¿Que pasa si falta?                                                                                              |
| ----------------------- | --------------------------------------------------------------------------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Firewall                | Filtra trafico malicioso y accesos no autorizados, protegiendo los servicios.                 | Internet y Transporte   | Aumenta el riesgo de ataques, intrusiones y degradacion del servicio.                                            |
| Load Balancer           | Distribuye las solicitudes entre varios servidores para evitar sobrecargas.                   | Aplicacion y Transporte | Algunos servidores pueden saturarse mientras otros permanecen ociosos, reduciendo disponibilidad y rendimiento.  |
| Queue                   | Absorbe picos de tráfico almacenando solicitudes temporalmente.                               | Aplicacion              | Las solicitudes excedentes pueden perderse o provocar caidas del sistema durante momentos de alta demanda.       |
| Compute                 | Ejecuta la logica de negocio y procesa las solicitudes de los usuarios.                       | Aplicacion              | No existiria procesamiento de las peticiones, la aplicación dejaria de funcionar.                                |
| Serverless Function     | Permite ejecutar tareas bajo demanda sin mantener servidores activos permanentemente.         | Aplicacion              | Seria necesario mantener infraestructura dedicada incluso para cargas pequeñas o esporadicas, aumentando costos. |
| SQL DB                  | Almacena datos estructurados y permite consultas complejas, busquedas y transacciones.        | Aplicacion              | No habria almacenamiento persistente confiable para la informacion principal del sistema.                        |
| NoSQL                   | Gestiona grandes volumenes de datos con acceso rapido y escalabilidad horizontal.             | Aplicacion              | Algunas cargas de trabajo tendrian peor rendimiento o mayores costos al depender unicamente de bases SQL.        |
| Cache                   | Reduce accesos repetitivos a la base de datos almacenando datos frecuentes en memoria.        | Aplicacion              | La base de datos recibiria mas carga, aumentando la latencia y el riesgo de saturacion.                          |
| CDN                     | Acerca el contenido estatico a los usuarios mediante servidores distribuidos geograficamente. | Aplicacion              | Mayor latencia, mas consumo de ancho de banda en el servidor principal y peor experiencia de usuario.            |
| Storage                 | Almacena archivos, imagenes, videos y otros contenidos estaticos.                             | Aplicacion              | No habria un lugar adecuado para guardar archivos persistentes de los usuarios o de la aplicacion.               |
| Search Engine           | Optimiza y acelera las búsquedas sobre grandes volumenes de informacion.                      | Aplicacion              | Las busquedas recaerian sobre la base de datos principal, aumentando la carga y reduciendo el rendimiento.       |
| Réplica                 | Permite distribuir consultas de lectura y mejorar la disponibilidad de la base de datos.      | Aplicacion              | La base de datos principal soportaria toda la carga de lectura, reduciendo escalabilidad y tolerancia a fallos.  |

### Tipos de Trafico

> El simulador trabaja con distintos tipos de solicitudes: STATIC, READ, WRITE, UPLOAD, SEARCH, MALICIOUS
> Para cada tipo de tráfico, completar una tabla con:
> ● Tipo de tráfico
> ● Ejemplo real
> ● Componente recomendado para procesarlo
> ● Riesgo si se procesa incorrectamente

| Tipo de tráfico      | Descripción                                                                                                                                                                                                                                                                                                                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| STATIC (GET)         | Puede representar imagenes, archivos CSS, JavaScript o recursos multimedia de una pagina web. En una arquitectura real suele servirse desde un CDN o un sistema de almacenamiento estatico. Si se procesa desde servidores de aplicacion, se desperdician recursos de computo y aumenta la carga innecesariamente.                          |
| READ (GET)           | Puede representar consultas de informacion, como ver un perfil de usuario, una lista de productos o el historial de compras. Generalmente se procesa en una base de datos SQL o en replicas de lectura. Si se gestiona incorrectamente, la base de datos puede saturarse y aumentar significativamente los tiempos de respuesta.            |
| WRITE (POST/PUT)     | Puede representar operaciones de creacion o modificacion de datos, como registrar usuarios, actualizar perfiles o realizar compras. Normalmente se procesa en la base de datos principal. Si falla o se enruta incorrectamente, pueden producirse perdidas de informacion o inconsistencias en los datos.                                   |
| UPLOAD (POST)        | Puede representar la carga de imagenes, documentos o videos por parte de los usuarios. En una arquitectura real suele almacenarse en servicios de almacenamiento de objetos. Si se procesa directamente en los servidores de aplicacion, puede consumir mucho ancho de banda y recursos, afectando el rendimiento general del sistema.      |
| SEARCH (GET)         | Puede representar busquedas de productos, articulos o contenido dentro de una plataforma. En sistemas grandes suele utilizarse un motor de busqueda especializado. Si se procesa unicamente con la base de datos principal, las consultas complejas pueden generar lentitud y sobrecarga del sistema.                                       |
| MALICIOUS            | Representa trafico malicioso como ataques DDoS, intentos de explotacion o solicitudes automatizadas no legitimas. En una arquitectura real debe ser filtrado por un firewall o sistemas de proteccion perimetral. Si alcanza los servicios internos, puede consumir recursos, provocar caidas y afectar la disponibilidad de la aplicacion. |

### Testeamos Queues

> Construiremos una infraestructura mínima para testear queues.
> Conectarán un firewall, una queue y una instancia de computación.
> Denle play y jueguen con el throughput (rate de tráfico).
> Incrementen el rate: que sucede después de la queue?.
> Mantengan el rate alto y luego llevenlo a cero rápidamente. Qué sucede después de la queue?

Al iniciar con tan solo una request por segundo, observamos como las requests tan solo pasaban el firewall (si no eran maliciosas), y pasaban a traves de la queue sin delay alguno derecho al centro de computo.

<img width="1272" height="1095" alt="image" src="https://github.com/user-attachments/assets/70636cb8-44c0-456b-91cd-a96bae36f8ce" />

Al aumnetar a cinco requests por segundo comenzamos a observar las request esperar levemente antes de pasar al centro de computo.

<img width="1261" height="1087" alt="image" src="https://github.com/user-attachments/assets/1fd0fb20-e1e7-4327-ae14-604c332ec546" />

Al aumentar a diez comenzamos algunas requests siendo buffered, es decir que estan esperando dentro de la cola para ser procesadas.

<img width="1269" height="1098" alt="image" src="https://github.com/user-attachments/assets/9eff887b-183e-4db0-bd74-8dfe099650f2" />

Cuando volvemos a uno de nuevo vemos como empiezan a salir de la cola y ser procesadas por el computo.


---

## Discusion y conclusiones



---

## Referencias
