# Redes de Computadoras

## Tarea #4

### Cuestiones de Repaso

_18.1. Dé algunas razones para usar fragmentación y reensamblado._

La fragmentacion es necesaria porque las redes de comunicaciones imponen un tamaño máximo de bloque para la aceptacion de datos, lo que obliga a dividir los mensajes originales en unidades mas pequeñas denominadas fragmentos o segmentos. 

Fragmentar tambien tiene muchos beneficios, como permitir un control de errores más eficiente al reducir la cantidad de bits que se necesitan retransmitir ante un fallo, y facilitar un acceso más equitativo al medio de transmisión al evitar que una sola estación monopolice los recursos de red. Ademas, el uso de unidades de datos reducidas permite a los receptores gestionar memorias temporales mas pequeñas y facilita la implementación de puntos de control periódicos para operaciones de reinicio y recuperación. 

El reensamblado es necesario al fragmentar, ya que este es el proceso realizado en el destino para reconstruir los fragmentos recibidos y recuperar la información original para el nivel de aplicacion. Ambos procesos van de la mano, al realizar el primero debe realizarse el segundo.

_18.2. Enumere los requisitos de un mecanismo de interconexión de redes._

1. Proporcionar un enlace entre redes. Como minimo, se necesita una conexion física y de control del enlace.
2. Proporcionar el encaminamiento y entrega de los datos entre procesos en diferentes redes.
3. Proporcionar un servicio de contabilidad que realice un seguimiento de la utilizacion de las diferentes redes y dispositivos de encaminamiento y mantenga informacion de estado.
4. Proporcionar los servicios mencionados de forma que no se requiera la modificacion de la arquitectura de red de cualquiera de las redes interconectadas. Es decir que el sistema
de interconexion entre redes se debe acomodar a las diversas diferencias existentes entre las distintas redes.

_18.3. ¿Cuáles son los pros y los contras de limitar el reensamblado a los sistemas finales en lugar de permitirlo en los dispositivos de encaminamiento?_

Pros:
- Permite el uso del encaminamiento dinamico, ya que los fragmentos de un mismo datagrama no precisan pasar a traves del mismo dispositivo de encaminamiento de salida.
- Evita que los dispositivos de encaminamiento consuman recursos excesivos en memorias temporales para almecenar datagramas parciales.

Contras:
- Los fragmentos sólo se pueden hacer más pequeños a medida que los datos se mueven a través del conjunto de redes, por lo que no se puede optimizar el tamaño de las unidades de datos para la siguiente red en la ruta, posiblemente disminuyendo eficiencia de transmision al generar mucho overhead de cabeceras.

_18.4. Explique la función de los tres indicadores en la cabecera de IPv4._

Solamente dos bits están actualmente definidos. 
- El bit de `mas datos` se utiliza para la fragmentacion y el reensamblado.
- El bit de `no fragmentacion` prohibe la fragmentacion cuando es 1.
   - Este puede ser util si se conoce que el destino no tiene capacidad de reensamblar fragmentos.
   - Si vale 1, el datagrama se descartara si se excede el tamaño maximo de una red en la ruta.
   - Cuando vale 1, es aconsejable utilizar encaminamiento desde el origen para evitar redes con tamaño de paquete maximos pequeños.

_18.5. ¿Cómo se calcula la suma de comprobación de la cabecera de IPv4?_

Para iniciar el proceso, el campo de la suma de comprobacion debe inicializarse con un valor de todo ceros. 
El procedimiento tecnico consiste en realizar la suma en complemento a uno de todas las palabras de 16 bits contenidas en dicha cabecera. 
El valor final que se coloca en el campo es el complemento a uno del resultado de esa suma acumulada

_18.6. ¿Qué diferencia existe entre los campos clase de tráfico y etiqueta de flujo en la cabecera de IPv6?_

El campo clase de trafico consta de 8 bits que permiten a una fuente identificar las caracteristicas en el tratamiento de trafico que desea cada paquete en relacion con otros paquetes procedentes de la misma fuente, pero actualmente se usa con otra intencion. Los primeros 6 bits se denominan campo de servicios diferenciados, y los 2 restantes se reservan para un campo de notificacion explicita de congestion

El campo etiqueta de flujo consta de 20 bits que permite identificar a un flujo en particular, donde un flujo es una secuencia de paquetes enviados desde un origen particular a un destino particular, para los que se solicita un tratamiento especial por parte de los dispositivos de red

La diferencia esta en que la clase de trafico agrupa paquetes por categorias de clases o prioridades, mientras que la etiqueta de flujo esta enfocada en gestionar flujos individuales y especificos como la transmision de un video en tiempo real.

_18.7. Explique brevemente los tres tipos de direcciones IPv6._

La direccion de unidifusion funciona como un identificador para una interfaz individual de modo que los paquetes enviados a esta direccion llegan unicamente a ese destino especifico.

La direccion de monodifusion se asigna a un conjunto de interfaces que generalmente pertenecen a nodos distintos. En esta modalidad el paquete se entrega a una sola interfaz del grupo siendo seleccionada aquella que se encuentre mas cercana segun la metrica del protocolo de encaminamiento.

La direccion de multidifusion identifica igualmente a un conjunto de interfaces que suelen estar ubicadas en diferentes nodos de la red. El funcionamiento consiste en entregar el paquete a todas las interfaces identificadas por esa direccion de grupo de forma simultanea.

_18.8. ¿Cuál es el propósito de cada uno de los tipos de cabeceras presentes en IPv6?_

- La cabecera IPv6 contiene la informacion esencial para el encaminamiento y gestion del paquete.
- La cabecera de opciones salto a salto define opciones especiales que requieren procesamiento en cada salto.
- La cabecera de encaminamiento proporciona un encaminamiento ampliado, similar al encaminamiento en el origen de IPv4.
- La cabecera de fragmentacion contiene informacion de fragmentacion y reensamblado.
- La cabecera de autenticacion proporciona la integridad del paquete y la autenticacion.
- La cabecera de encapsulamiento de la carga de seguridad proporciona privacidad.
- La cabecera de las opciones para el destino contiene informacion opcional para que sea examinada en el nodo destino.

---

### Ejercicios

_18.1. En la discusión sobre IP, se mencionó que el identificador, el indicador de no fragmentar y el tiempo de vida se hallan presentes en la primitiva Send pero no en la primitiva Deliver, ya que esos parámetros no son competencia de IP. Indique, para cada una de estas primitivas, si es competencia de la entidad IP en el origen, de la entidad IP en cada dispositivo de encaminamiento intermedio o de la entidad IP en el sistema final destino. Justifique su respuesta._

El identificador es competencia del destino porque es el encargado de reensamblar los fragmentos al paquete original, y este campo identifica de una forma unica a la unidad de datos. El origen setea este campo para generar esta identificacion unica, y a los dispositivos de encaminamiento intermedios no les incumbe ya que estos no reensamblan el paquete.

El indicador de no fragmentacion es competencia de los dispositivos de encaminamiento intermedios, ya que este indica a estos que tiene prohibido fragmentar el paquete, y que deben descartarlo si el datagrama es demasiado grande para la siguiente red e informar al origen mediante un mensaje de error. El origen solo lo setea, mientras que no tiene utilidad para el destino.

El tiempo de vida es competencia de los dispositivos de encaminamiento intermedios, ya que estos lo decrementan en cada salto, y si el contador llega a cero el enrutador elimina el datagrama y lo notifica mediante ICMP. El origen solo lo setea, mientras que no tiene utilidad en el destino porque es un mecanismo exclusivo de la capa de red para asegurar la estabilidad del conjunto de redes.

_18.2. ¿Cuál es la información suplementaria de la cabecera en el protocolo IP?_

La informacion suplementaria en la cabecera IPv4 esta en el campo de opciones de longitud variable. Este permite integrar parametros opcionales como etiquetas de seguridad o el encaminamiento en el origen. Tambien incluye el registro de la ruta para conocer el camino seguido, la identificacion de la secuencia para trafico periodico como voz y las marcas de tiempo para registrar el paso por cada nodo. Se añade relleno para garantizar que la cabecera sea multiplo de 32 bits.

La informacion suplementaria en la cabecera IPv6 esta en cabeceras de extension entre la cabecera base y la unidad de datos. Los principales son las opciones salto a salto que examina cada nodo del camino y la cabecera de encaminamiento con la lista de estaciones intermedias. Tambien existen cabeceras especificas para el control de la fragmentacion por parte del origen, mecanismos de seguridad para autenticacion y privacidad, y opciones destinadas solo al examen del nodo destino final.

_18.3. Describa algunas circunstancias en las que sería deseable utilizar encaminamiento en el origen en lugar de dejar a los dispositivos de encaminamiento que realicen la decisión de encaminamiento._

Una de las razones principales es la seguridad. Al definir la ruta desde el origen, se puede asegurar que se atraviesen unicamente redes autorizadas para manejar informacion sensible, evitando nodos que podrian no ser confiables. 

Tambien es util por motivos de prioridad o para satisfacer requisitos especificos de calidad de servicio, buscando un tratamiento especial o caminos con menor retardo para trafico de voz por ejemplo.

Tambien podria usarse cuando no se desea fragmentar la informacion, para evitar redes con unidades de transferencia pequeñas y asi evitar el descarte de la informacion.

_18.5. Un datagrama de 4.480 octetos se va a transmitir y se necesita fragmentar ya que va a pasar por una red Ethernet con un campo máximo de carga útil de 1.500 octetos. Muestre los valores de los campos longitud total, indicador de más segmentos y desplazamiento de fragmento en cada uno de los fragmentos resultantes._

_18.7. Se va a segmentar un datagrama. ¿Qué opciones del campo de opción se necesitan copiar en la cabecera de cada fragmento y cuáles se necesitan copiar sólo en el primer fragmento? Justifique el tratamiento de cada opción._

_18.8. Un mensaje de la capa de transporte, que contiene 1.500 bits de datos y 160 bits de cabecera, se envía a la capa internet, la cual incorpora otros 160 bits de cabecera. El resultado se transmite a través de dos redes que utilizan cada una 24 bits de cabecera de paquete. La red destino tiene un tamaño de paquete máximo de 800 bits. ¿Cuántos bits, incluyendo cabeceras, se entregan al protocolo de la capa de red en el destino?_

_18.11. Compare los campos individuales de la cabecera IPv4 con los de la cabecera IPv6. Compare las posibilidades proporcionadas por cada uno de los campos de IPv4 con los de IPv6._

_18.12. Justifique el orden recomendado de las cabeceras de extensión de IPv6 (por ejemplo, ¿por qué va primero la cabecera de opciones salto-a-salto?, ¿por qué la cabecera de encaminamiento está antes que la cabecera de fragmentación?, y así hasta la cabecera final)._

_18.16. Las especificaciones originales de IPv6 combinaban los campos de etiqueta de flujo y prioridad en un solo campo de etiqueta de flujo de 28 bits. Esto permitía a los flujos redefinir la interpretación de los diferentes valores de prioridad. Sugiera una razón por la que la especificación final incluye un campo de prioridad en un campo distinto._

_18.17. Para el encaminamiento IPv6 tipo 0, especifique el algoritmo para actualizar las cabeceras IPv6 y de encaminamiento en los nodos intermedios._
