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



---

## Discusion y conclusiones



---

## Referencias
