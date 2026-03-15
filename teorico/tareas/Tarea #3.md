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

...

---

2.2 b) Suponga ahora que el traductor del primer ministro chino puede traducir sólo al japonés y que el primer ministro francés tiene un traductor alemán. Un traductor de japonés a alemán se encuentra disponible en Alemania. Dibuje el diagrama que refleje esta nueva situación y describa la hipotética conversación telefónica.

...

2.3. Enumere las desventajas del diseño en capas para los protocolos.

...

---

2.4. Dos cuerpos de ejército (de color azul), situados sobre dos colinas, están preparando un ataque a un único ejército (de color rojo) situado en el valle que las separa. El ejército rojo puede vencer por separado a cada cuerpo del ejército azul, pero fracasará si los dos ejércitos azules le atacan simultáneamente. Los cuerpos de ejército azules se comunican mediante un sistema de comunicación no fiable (un soldado de infantería). El comandante de uno de los cuerpos de ejército azul desearía atacar al mediodía. Su problema es éste: si envía un mensaje ordenando el ataque, no puede estar seguro de que el mensaje haya llegado. Podría solicitar una confirmación, pero ésta también podría ser interceptada. ¿Existe algún protocolo que pueda utilizar el ejército azul para evitar la derrota?

...

---

2.5. Una red de difusión es aquella en la que las transmisiones de cualquier estación son recibidas por todas las estaciones conectadas al medio compartido. Ejemplos son una red de área local con topología en bus, como Ethernet, o una red inalámbrica. Discuta si es necesaria o no una capa de red (capa 3 de OSI) en una red de difusión.

...

---

2.6 Basándose en los principios enunciados en la Tabla 2.1:

a) Diseñe una arquitectura con ocho capas y ponga un ejemplo de su utilización.

...

b) Diseñe otra con seis capas y ponga otro ejemplo para ésta.

...

---

2.7. En la Figura 2.14, la unidad de datos del protocolo (PDU) de la capa N se encapsula en una PDU de la capa (N. 1). Igualmente, se puede partir la PDU del nivel N en varias PDU del nivel (N .1) (segmentación) o agrupar varias PDU del nivel N en una única PDU del nivel (N.1) (agrupamiento).

a) En la segmentación, ¿es necesario que cada segmento del nivel (N.1) contenga unacopia de la cabecera del nivel N?

...

b) En el agrupamiento, ¿es necesario que cada una de las PDU conserve su cabecera o se pueden agrupar los datos en una única PDU de nivel N con una única cabecera de nivel N?

...
