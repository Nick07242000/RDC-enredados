CUESTIONES DE REPASO

18.1. Dé algunas razones para usar fragmentación y reensamblado.

18.2. Enumere los requisitos de un mecanismo de interconexión de redes.

18.3. ¿Cuáles son los pros y los contras de limitar el reensamblado a los sistemas finales en lugar de permitirlo
en los dispositivos de encaminamiento?

18.4. Explique la función de los tres indicadores en la cabecera de IPv4.

18.5. ¿Cómo se calcula la suma de comprobación de la cabecera de IPv4?

18.6. ¿Qué diferencia existe entre los campos clase de tráfico y etiqueta de flujo en la cabecera de IPv6?

18.7. Explique brevemente los tres tipos de direcciones IPv6.

18.8. ¿Cuál es el propósito de cada uno de los tipos de cabeceras presentes en IPv6?

EJERCICIOS

18.1. En la discusión sobre IP, se mencionó que el identificador, el indicador de no fragmentar y el tiempo de
vida se hallan presentes en la primitiva Send pero no en la primitiva Deliver, ya que esos parámetros no son
competencia de IP. Indique, para cada una de estas primitivas, si es competencia de la entidad IP en el origen,
de la entidad IP en cada dispositivo de encaminamiento intermedio o de la entidad IP en el sistema final destino.
Justifique su respuesta.

18.2. ¿Cuál es la información suplementaria de la cabecera en el protocolo IP?

18.3. Describa algunas circunstancias en las que sería deseable utilizar encaminamiento en el origen en lugar de
dejar a los dispositivos de encaminamiento que realicen la decisión de encaminamiento.

18.5. Un datagrama de 4.480 octetos se va a transmitir y se necesita fragmentar ya que va a pasar por una red
Ethernet con un campo máximo de carga útil de 1.500 octetos. Muestre los valores de los campos longitud total,
indicador de más segmentos y desplazamiento de fragmento en cada uno de los fragmentos resultantes.

18.7. Se va a segmentar un datagrama. ¿Qué opciones del campo de opción se necesitan copiar en la cabecera
de cada fragmento y cuáles se necesitan copiar sólo en el primer fragmento? Justifique el tratamiento de cada
opción.

18.8. Un mensaje de la capa de transporte, que contiene 1.500 bits de datos y 160 bits de cabecera, se envía a
la capa internet, la cual incorpora otros 160 bits de cabecera. El resultado se transmite a través de dos redes
que utilizan cada una 24 bits de cabecera de paquete. La red destino tiene un tamaño de paquete máximo de
800 bits. ¿Cuántos bits, incluyendo cabeceras, se entregan al protocolo de la capa de red en el destino?

18.11. Compare los campos individuales de la cabecera IPv4 con los de la cabecera IPv6. Compare las
posibilidades proporcionadas por cada uno de los campos de IPv4 con los de IPv6.

18.12. Justifique el orden recomendado de las cabeceras de extensión de IPv6 (por ejemplo, ¿por qué va
primero la cabecera de opciones salto-a-salto?, ¿por qué la cabecera de encaminamiento está antes que la
cabecera de fragmentación?, y así hasta la cabecera final).

18.16. Las especificaciones originales de IPv6 combinaban los campos de etiqueta de flujo y prioridad en un solo
campo de etiqueta de flujo de 28 bits. Esto permitía a los flujos redefinir la interpretación de los diferentes
valores de prioridad. Sugiera una razón por la que la especificación final incluye un campo de prioridad en un
campo distinto.

18.17. Para el encaminamiento IPv6 tipo 0, especifique el algoritmo para actualizar las cabeceras IPv6 y de
encaminamiento en los nodos intermedios.
