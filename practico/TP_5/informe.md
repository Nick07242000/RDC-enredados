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

| Tipo de trafico  | Ejemplo real                                                                                                  | Componente recomendado para procesarlo               | Riesgo si se procesa incorrectamente                                                                 |
| ---------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| STATIC (GET)     | Puede representar imagenes, archivos CSS, JavaScript o logos de un sitio web.                                 | Storage + Cache/CDN                                  | Mayor latencia, consumo innecesario de recursos de computo y sobrecarga de los servidores.           |
| READ (GET)       | Puede representar consultas de perfil de usuario, listados de productos o historial de compras.               | SQL DB (opcionalmente Replica para escalar lecturas) | Datos no disponibles, respuestas lentas o saturacion de la base de datos principal.                  |
| WRITE (POST/PUT) | Puede representar registro de un usuario, creacion de una orden de compra o actualizacion de datos.           | SQL DB                                               | Perdida de datos, inconsistencias o errores en las transacciones.                                    |
| UPLOAD (POST)    | Puede representar subida de imagenes, documentos, videos o archivos adjuntos.                                 | Storage (apoyado por Compute para procesamiento)     | Perdida de archivos, lentitud del sistema o saturacion de los servidores de aplicacion.              |
| SEARCH (GET)     | Puede representar busqueda de productos en un e-commerce o consulta de articulos en una plataforma.           | Search Engine (o SQL DB en sistemas simples)         | Consultas lentas, alto consumo de recursos y degradacion del rendimiento general.                    |
| MALICIOUS        | Puede representar ataques DDoS, escaneo de puertos, intentos de explotación o tráfico automatizado malicioso. | Firewall                                             | Caida de servicios, consumo excesivo de recursos, perdida de disponibilidad y daños a la reputacion. |

### Testeamos Queues

> Construiremos una infraestructura mínima para testear queues.  
> Conectarán un firewall, una queue y una instancia de computación.  
> Denle play y jueguen con el throughput (rate de tráfico).  
> Incrementen el rate: que sucede después de la queue?  
> Mantengan el rate alto y luego llevenlo a cero rápidamente. Qué sucede después de la queue?  

Al iniciar con tan solo una request por segundo, observamos como las requests tan solo pasaban el firewall (si no eran maliciosas), y pasaban a traves de la queue sin delay alguno derecho al centro de computo.

<img width="1272" height="1095" alt="image" src="https://github.com/user-attachments/assets/70636cb8-44c0-456b-91cd-a96bae36f8ce" />

Al aumentar a cinco requests por segundo comenzamos a observar las request esperar levemente antes de pasar al centro de computo.

<img width="1261" height="1087" alt="image" src="https://github.com/user-attachments/assets/1fd0fb20-e1e7-4327-ae14-604c332ec546" />

Al aumentar a diez comenzamos algunas requests siendo buffered, es decir que estan esperando dentro de la cola para ser procesadas.

<img width="1269" height="1098" alt="image" src="https://github.com/user-attachments/assets/9eff887b-183e-4db0-bd74-8dfe099650f2" />

Aqui es donde podemos ver claramente como la queue protege el compute manteniendo el ritmo de flujos de requests constantes, aunque el trafico real aumente exponencialmente.

Cuando volvemos a uno de nuevo vemos como las requests que habian quedado encoladas empiezan a salir de la cola y ser procesadas por el computo.

<img width="1289" height="1098" alt="image" src="https://github.com/user-attachments/assets/0f8f947c-c00c-4779-9034-a4add5d63d98" />

Podemos hacer el ejercicio de setear un rate muy alto donde de nuevo vemos como el rate hacia el compute se mantiene constante:

<img width="1282" height="1090" alt="image" src="https://github.com/user-attachments/assets/2a068f0d-ec29-48f9-903f-987d985c704c" />

Y al bajarlo a cero de nuevo vemos como las requests encoladas terminan de procesarse:

<img width="1284" height="1102" alt="image" src="https://github.com/user-attachments/assets/97015414-5147-49da-8524-fc07dd37ba31" />

Este es el proposito de la queue, protege nuestra infraestructura de picos de trafico, encolando las requests para ser procesadas al ritmo que nuestra infra soporte, evitando asi el colapso de la misma por sobrecarga de los recursos.

### Primera Infraestructura Minima

> Tu arquitectura debe intentar resolver:  
> ● Tráfico estático y uploads.  
> ● Lecturas y escrituras de datos.  
> ● Búsquedas.  
> ● Ataques o tráfico malicioso.  
> En modo sandbox, modificá la distribución de tráfico y modificá el rate. Documenta con capturas:  
> a) La arquitectura inicial.  
> b) El presupuesto inicial.  
> c) El estado de salud de los servicios.  
> d) El momento en que la arquitectura empieza a fallar, si ocurre.

Empezamos con la siguiente configuracion:

<img width="1279" height="1099" alt="image" src="https://github.com/user-attachments/assets/d410a59b-39d1-4164-81dd-0886744a592b" />

Tenemos un firewall para protegernos de los ataque maliciosos, una queue para protegernos de los picos de trafico, un load balancer para distribuir la carga equitativamente a tres centros de computo, los cuales disponen de una NoSQL para requests de escritura y lectura, y una Search para busquedas. Ademas agregamos un CDN y un Storage para el contenido estatico.

Para esto usamos $600 del presupuesto inicial por defecto de $2000.

> ¿Qué componente falló primero?  
> ¿Por qué creés que falló?  
> ¿Fue un problema de capacidad, diseño, costo o seguridad?

Iniciando con tan solo 1 req/s pudimos ver como obtuvimos el primer fallo en una request de upload. Esto puede significar que nuestro procesamiento de contenido estatico esta subdimensionado.

<img width="1281" height="1089" alt="image" src="https://github.com/user-attachments/assets/bed2939e-f741-4a11-893f-894fc90c3044" />

Aumentando a 5 req/s vimos como este trend se mantenia, las unicas requests que presentaban fallos eran las de upload:

<img width="1280" height="1096" alt="image" src="https://github.com/user-attachments/assets/447f3362-baf7-449b-8ce6-ad3f1189ce21" />

Este trend se mantuvo hasta llegar a 18 req/s, donde comenzamos a ver fallos en trafico es escritura y busqueda, lo cual atribuimos a una sobrecarga de los centros de computo. Podemos observar como estan al limite de su carga:

<img width="1284" height="1089" alt="image" src="https://github.com/user-attachments/assets/b2115ca3-fe80-4749-8df4-772ce7a8dd93" />

A 25 req/s vemos como los centros de computo estan en estado critico, estan recibiendo trafico que supera su capacidad de procesamiento y las requests estan siendo encoladas, la tasa de fallo ya es demasiado grande y esta impactando seriamente a la reputacion:

<img width="1292" height="1094" alt="image" src="https://github.com/user-attachments/assets/708dfa5f-3a79-424d-87a0-29932cde88e2" />

Llevando esta arquitectura simplificada a un solo centro de computo al modo survival podemos observar claramente que ahi esta presente el cuello de botella:

<img width="1276" height="993" alt="image" src="https://github.com/user-attachments/assets/b7ac7a14-7e47-4ccb-b8f9-d3b2546219c3" />

Atribuumos los fallos a un problema de diseño, donde el contenido estatico no estaba siendo propiamente procesado, y donde los centros de computo eran pocos, o no lo suficientemente potentes para procesar al nivel del resto de la arquitectura.

### Escalabilidad y Balanceo

---

## Discusion y conclusiones



---

## Referencias
