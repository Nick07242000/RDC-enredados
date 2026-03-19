# Redes de Computadoras

## Tarea #3

### Ejercicios

2.1. Usando los modelos de capas de la Figura 2.16, describa el procedimiento de pedir y enviar una pizza, indicando las interacciones habidas en cada nivel.

Podemos dividir el procedimiento en dos fases, la solicitud de la pizza (Modelo 1) y el envío de la misma (Modelo 2). Cada capa realiza tareas específicas que delega a la inferior, comunicándose de forma lógica con su entidad par en el otro extremo.

Modelo 1: Pedido de la Pizza
- El invitado decide el tipo de pizza que desea. El objetivo final es que el cocinero cocine el tipo de pizza que quiere, pero para esto debe pasar por otras capas ya que no se comunica directamente con el cocinero. El invitado le comunica al anfitrion que tipo de pizza quiere, y no interviene en las subsecuentes etapas de la comunicacion.
- El anfitrión actúa como intermediario. Toma el deseo del invitado y se comunica con el Encargado de Pedidos para gestionar los detalles de la transacción, como la dirección y el pago. Pero el Encargado esta fisicamente en otro lugar, por lo que se apoya en la siguiente capa.
- El teléfono funciona como el transmisor de los datos. Convierte la voz en señales eléctricas capaces de viajar por la infraestructura.
- La linea telefonica es el camino físico por el cual se propagan las señales electromagnéticas entre ambos sistemas.
- Del otro lado de la linea el telefono del encargado convierte las señales electricas en voz nuevamente.
- El encargado toma los detalles del pedido y comunica al cocinero solamente las pizzas que debe cocinar, abstrayendo el detalle de para quien es o adonde deben ir.
- El cocinero cocina lo que le solicita, solo necesita saber que tipo de pizza cocinar.

Modelo 2: Envío de la Pizza
- Una vez preparada la pizza según las especificaciones recibidas, el cocinero la entrega a la capa inferior para su logística.
- El encargado prepara el paquete, añade la información de control (etiqueta con dirección) y lo entrega a la unidad de transporte.
- La furgoneta actúa como el mecanismo de transporte extremo a extremo. Es la responsable de mover la unidad física a través de la infraestructura de red hasta el punto de destino.
- La carretera proporciona la infraestructura física sólida sobre la cual se desplaza el vehículo para conectar el origen con el destino.
- En el destino, el Anfitrión recibe el paquete y verifica que corresponda al pedido realizado.
- Finalmente, el invitado recibe la pizza que solicito.

---

2.2 a) Los primeros ministros de China y Francia necesitan alcanzar un acuerdo por teléfono, pero ninguno de los dos habla el idioma de su interlocutor. Es más, ninguno tiene cerca un traductor que traduzca el idioma del otro. No obstante, ambos tienen un traductor de inglés. Dibuje un diagrama similar al de la Figura 2.16 que describa la situación y detalle las interacciones que haya en cada nivel.

<img width="600" height="300" alt="image" src="https://github.com/user-attachments/assets/b3c2f348-eaf0-4c3a-9cb5-03c887745c06" />

- En primer nivel tenemos cada ministro, que quiere comunicarse con el otro para llegar a un acuerdo, formulan el discurso diplomatico y lo transmiten a sus traductores.
- Los traductores a ingles, reciben los mensajes y los transforman de idioma al ingles, y los comunican al telefono.
- El telefono transforma la voz en señales para ser transmitidas por el medio.
- El medio transmite las señales recibidas por los telefonos.

b) Suponga ahora que el traductor del primer ministro chino puede traducir sólo al japonés y que el primer ministro francés tiene un traductor alemán. Un traductor de japonés a alemán se encuentra disponible en Alemania. Dibuje el diagrama que refleje esta nueva situación y describa la hipotética conversación telefónica.

<img width="900" height="300" alt="image" src="https://github.com/user-attachments/assets/5cc351ef-cb32-42b9-8a9f-0972a2d0db64" />

- Cada ministro formula el discurso diplomatico y lo transmite a sus traductores.
- Los traductores reciben los mensajes y los transforman de idioma al Japones o al Aleman, y los comunican al telefono.
- El telefono transforma la voz en señales para ser transmitidas por el medio.
- El medio transmite las señales recibidas por los telefonos.
- El telefono en Alemania traduce las señales a voz nuevamente.
- En traductor en Alemania recibe el mensaje y lo traduce al idioma correspondiente.
- El telefono en Alemania traduce la voz a señales nuevamente.
- El medio transmite las señales recibidas por los telefonos.
- El telefono del ministro opuesto traduce las señales a voz nuevamente.
- El traductor opuesto traduce el mensaje al idioma del ministro.
- El ministro recibe el mensaje.

---

2.3. Enumere las desventajas del diseño en capas para los protocolos.

- Sobrecarga de procesamiento: Cada capa de la pila requiere tiempo y recursos de cómputo adicionales para procesar su propia información de control y cabeceras, lo que puede ralentizar la comunicación si el número de capas es excesivo.
- Sobrecarga de datos: Debido al proceso de encapsulamiento, cada nivel añade su propia cabecera (y a veces cola) a los datos, lo que incrementa el volumen total de bits transmitidos y reduce la eficiencia en el uso del ancho de banda disponible.
- Complejidad de integración: Un diseño con demasiados niveles puede dificultar la descripción y la integración de las funciones, creando complicaciones técnicas innecesarias en el desarrollo del software y hardware.
- Duplicidad de funciones: Con frecuencia, funciones similares se implementan en varias capas distintas lo que genera una redundancia que consume recursos adicionales.
- Fragmentación ineficiente: El tener que dividir los datos para ajustarse a los límites de las capas inferiores puede generar una carga adicional de interrupciones y procesamiento en el receptor para reensamblar la información original.

---

2.4. Dos cuerpos de ejército (de color azul), situados sobre dos colinas, están preparando un ataque a un único ejército (de color rojo) situado en el valle que las separa. El ejército rojo puede vencer por separado a cada cuerpo del ejército azul, pero fracasará si los dos ejércitos azules le atacan simultáneamente. Los cuerpos de ejército azules se comunican mediante un sistema de comunicación no fiable (un soldado de infantería). El comandante de uno de los cuerpos de ejército azul desearía atacar al mediodía. Su problema es éste: si envía un mensaje ordenando el ataque, no puede estar seguro de que el mensaje haya llegado. Podría solicitar una confirmación, pero ésta también podría ser interceptada. ¿Existe algún protocolo que pueda utilizar el ejército azul para evitar la derrota?

No existe un protocolo que garantice con certeza absoluta que ambos ejércitos atacarán simultáneamente a través de un canal no fiable. Esto se debe a que, sin importar cuántas confirmaciones se envíen, el emisor del último mensaje nunca podrá estar seguro de que este llegó a su destino, lo que genera una cadena infinita de confirmaciones necesarias para alcanzar un consenso perfecto.

Sin embargo, podemos usar un three-way handshake para establecer una conexión. En este procedimiento, el primer general enviaría la orden (SYN), el segundo respondería confirmando la recepción y enviando su propia sincronización (SYN/ACK), y el primero enviaría una confirmación final (ACK) para asegurar que ambos están listos. Este método aumenta significativamente la fiabilidad de la comunicación. Para manejar la posible pérdida de mensajeros, si el comandante que envía la orden no recibe una confirmación en un tiempo determinado, asume que el mensaje se perdió y lo envía de nuevo. De esta manera, mediante el uso de retransmisiones y números de secuencia, se logra que un sistema de comunicación intrínsecamente no fiable funcione de manera fiable y transparente en la práctica.

---

2.5. Una red de difusión es aquella en la que las transmisiones de cualquier estación son recibidas por todas las estaciones conectadas al medio compartido. Ejemplos son una red de área local con topología en bus, como Ethernet, o una red inalámbrica. Discuta si es necesaria o no una capa de red (capa 3 de OSI) en una red de difusión.

En una red de difusión, donde todas las estaciones comparten el medio y reciben las mismas señales, la capa de red no es estrictamente necesaria para la comunicación interna entre dispositivos de la misma subred. En estos escenarios, las funciones de gestión y direccionamiento físico pueden ser resueltas íntegramente por la capa de enlace de datos, empleando las direccions MAC para identificar a los destinatarios y regular el canal. Al no requerirse inteligencia de encaminamiento o conmutación para mover datos entre nodos intermedios dentro del mismo entorno local, el uso de una capa de red resulta superfluo.

---

2.6 Basándose en los principios enunciados en la Tabla 2.1:

a) Diseñe una arquitectura con ocho capas y ponga un ejemplo de su utilización.

1.  Capa Física: Se encarga de la transmisión de cadenas de bits no estructuradas sobre el medio físico, definiendo las características mecánicas y eléctricas.
2.  Capa de Acceso al Medio: Gestiona el acceso a medios compartidos y el direccionamiento físico, resolviendo conflictos de contención o turnos de transmisión.
3.  Capa de Control de Enlace Lógico: Proporciona una interfaz hacia las capas superiores y gestiona el control de errores y flujo en el enlace.
4.  Capa de Red: Responsable del encaminamiento de los paquetes a través de sistemas intermedios hasta alcanzar el sistema destino.
5.  Capa de Transporte: Garantiza una transferencia de datos fiable, transparente y en orden entre los puntos finales.
6.  Capa de Sesión: Organiza y sincroniza el diálogo entre las aplicaciones, permitiendo la gestión de puntos de recuperación.
7.  Capa de Presentación: Gestiona la sintaxis y la representación de los datos, permitiendo funciones como el cifrado o la compresión.
8.  Capa de Aplicación: Contiene la lógica necesaria para que las aplicaciones de usuario accedan a los servicios de la red.

Esta separación se basa en el Principio 3, ya que la tarea de regular el acceso a un cable compartido requiere tecnologías y lógica de control muy distintas a las de mantener un enlace lógico fiable entre dos puntos. El Principio 8 justifica mantener la división de las capas superiores debido a los diferentes niveles de abstracción.

Ejemplo de utilización: Envío de un archivo confidencial en una red local

- Aplicación: Un usuario inicia la transferencia de un archivo mediante un software específico.
- Presentación: El sistema cifra el archivo para asegurar su privacidad antes de que abandone el host.
- Sesión: Se establecen puntos de comprobación en la transferencia para que, si falla la red, el envío se retome desde el último bloque confirmado.
- Transporte: Los datos se dividen en segmentos y se les asignan números de secuencia para garantizar que lleguen sin errores ni duplicados.
- Red: Se añade la dirección IP de destino para que los encaminadores determinen la ruta óptima hacia el receptor.
- Control de Enlace Logico: Se añade información de control para gestionar el flujo punto a punto entre la estación y el nodo de red.
- Acceso al Medio: La red aplica un algoritmo para determinar el instante exacto en que puede transmitir la trama al cable sin colisionar con otros.
- Física: Los bits se transforman en niveles de tensión eléctrica que viajan por el cable de par trenzado.

b) Diseñe otra con seis capas y ponga otro ejemplo para ésta.

1. Capa Física: Se encarga de la interfaz física entre dispositivos y define las reglas para la transmisión de cadenas de bits no estructuradas sobre el medio. Su función es transformar los datos en señales electromagnéticas capaces de propagarse.
2. Capa de Acceso al Medio: Esta capa gestiona el acceso coordinado a medios de transmisión compartidos y el direccionamiento físico. Se justifica su separación de la capa física por emplear lógicas de control distintas, como la detección de colisiones.
3. Capa de Control de Enlace Lógico: Actúa como interfaz hacia las capas superiores y proporciona servicios de transferencia de datos fiables, incluyendo el control de flujo y errores básico. Sigue el Principio 11 al reestructurar funciones de enlace en subcapas según las necesidades de comunicación.
4. Capa de Red: Es la responsable de la transferencia de información entre sistemas finales y de determinar la ruta óptima a través de nodos intermedios. Proporciona independencia a los niveles superiores respecto a las tecnologías de conmutación subyacentes.
5. Capa de Transporte: Proporciona un mecanismo de intercambio de datos extremo a extremo que garantiza que la información se entregue libre de errores, en orden y sin duplicados. Libera a las capas superiores de cualquier preocupación técnica sobre el transporte.
6. Capa de Aplicación: Agrupa la lógica necesaria para admitir aplicaciones de usuario junto con la gestión del formato y la sintaxis de los datos. Siguiendo el Principio 1 esta capa fusiona las funciones de Aplicación, Presentación y Sesión del modelo OSI para reducir la complejidad de integración.

Ejemplo de utilización: Consulta a un servidor web

- Aplicación: El navegador genera una solicitud HTTP para obtener una página web, gestionando internamente la representación de los caracteres.
- Transporte: Se utiliza el protocolo TCP para establecer una conexión lógica y asegurar que la solicitud llegue íntegra mediante el uso de números de secuencia.
- Red: El protocolo IP añade la dirección global de destino para que los encaminadores determinen el camino a través de la interconexión de redes.
- Control de Enlace Lógico: La unidad de datos se encapsula añadiendo información de control de enlace para gestionar el flujo lógico hacia el siguiente salto.
- Acceso al Medio: El sistema aplica un algoritmo para escuchar el medio y transmitir la trama solo cuando el canal esté libre, evitando colisiones.
- Física: Los datos se convierten en señales eléctricas que viajan por un cable de par trenzado hasta el dispositivo de red.

---

2.7. En la Figura 2.14, la unidad de datos del protocolo (PDU) de la capa N se encapsula en una PDU de la capa (N. 1). Igualmente, se puede partir la PDU del nivel N en varias PDU del nivel (N .1) (segmentación) o agrupar varias PDU del nivel N en una única PDU del nivel (N.1) (agrupamiento).

a) En la segmentación, ¿es necesario que cada segmento del nivel (N.1) contenga unacopia de la cabecera del nivel N?

No es necesario que cada segmento del nivel N-1 contenga una copia de la cabecera del nivel N, ya que la capa inferior trata a la PDU superior como un bloque indivisible de datos de usuario e ignora su contenido específico. Durante este proceso, la cabecera original del nivel N queda integrada simplemente como parte de la carga útil del primer fragmento. Aunque cada unidad de datos de nivel N-1 requiere su propia cabecera de ese nivel para su transporte independiente, la cabecera de nivel N solo se recupera y procesa una vez que todos los fragmentos han sido reensamblados por la entidad par en el destino.

b) En el agrupamiento, ¿es necesario que cada una de las PDU conserve su cabecera o se pueden agrupar los datos en una única PDU de nivel N con una única cabecera de nivel N?

En el agrupamiento, es indispensable que cada PDU conserve su propia cabecera, ya que estas contienen información de control crítica necesaria para que la entidad par en el destino pueda identificar y procesar cada mensaje de forma independiente. Dado que la capa inferior trata a las PDU recibidas como datos de usuario opacos, no tiene la capacidad de consolidar las cabeceras de la capa superior; simplemente las empaqueta en una unidad mayor para su transporte, manteniendo la integridad individual de cada bloque original para su correcta entrega final.
