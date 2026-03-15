# Redes de Computadoras

## Tarea #2

### Cuestiones de Repaso

2.1 ¿Cuál es la función principal de la capa de acceso a la red?

La capa de acceso a la red es responsable del intercambio de datos entre el sistema final y la red a la cual está conectado, esta permite que el sistema emisor entable un diálogo con la red para especificar la dirección del destino y solicitar servicios específicos, como puede ser la gestión de prioridades para el tráfico enviado. El software de las capas superiores puede entonces funcionar correctamente con independencia de la red a la que el computadorsté conectado.

2.2. ¿Qué tareas realiza la capa de transporte?

Se encaraga de que los datos se intercambien de una manera fiable, asegurandose de que todos los datos llegan a la aplicación destino y, además, llegan en el mismo orden en que fueron enviados. Los mecanismos que proporcionan dicha fiabilidad son independientes de la naturaleza de las aplicaciones.

Para cumplir con este objetivo, esta capa realiza la tarea crítica de asegurar la entrega en orden, lo que significa que todos los datos deben llegar a la aplicación de destino en la misma secuencia en que fueron enviados. Para ello, utiliza números de secuencia en las unidades de datos, lo que permite al receptor reordenar la información si esta llega desordenada a través de la red. Asimismo, se encarga del control de errores y fiabilidad, asegurando que los datos se entreguen libres de errores, sin pérdidas ni duplicaciones, mediante el uso de códigos de detección como la suma de comprobación.

Tambien realiza direccionamiento y la multiplexación mediante identificadores denominados puertos o puntos de acceso al servicio. Esto permite distinguir entre las diferentes aplicaciones que se ejecutan simultáneamente en un mismo computador, garantizando que los datos alcancen el proceso de usuario correcto. Operativamente, la capa realiza la segmentación y el encapsulamiento* ¿recibiendo bloques de datos de la capa de aplicación y dividiéndolos en unidades más pequeñas y manejables llamadas segmentos, a las que añade una cabecera con información de control.

2.3. ¿Qué es un protocolo?

Es un conjunto de reglas o convenciones que gobiernan el intercambio de datos entre dos sistemas. En el marco de una arquitectura de red, las capas paras de diferentes sistemas se comunican entre sí intercambiando bloques de datos que deben verificar estas reglas establecidas.

Para que un protocolo esté definido con precisión y permita la interoperatividad entre sistemas distintos, debe contar con tres elementos o características fundamentales:
- Sintaxis: Se refiere al formato de los bloques de datos, es decir, cómo se estructuran físicamente los datos y el orden en que se presentan dentro de la unidad de datos.
- Semántica: Incluye la información de control para la coordinación de la comunicación y la gestión de errores, definiendo qué significa cada campo y qué acciones deben tomarse.
 -Temporización: Trata sobre la secuenciación de los mensajes y la sintonización de las velocidades de transmisión para asegurar que el intercambio sea fluido y ordenado.

En resumen, los protocolos proporcionan las reglas necesarias para que entidades en diferentes computadores puedan cooperar y entenderse de manera efectiva.

2.4. ¿Qué es una unidad de datos del protocolo (PDU)?

Es el nombre que recibe el bloque de datos intercambiado entre entidades pares en cualquier nivel o capa de una arquitectura de protocolos. Básicamente, representa el conjunto de datos especificado en un protocolo particular que consta de información de control de esa capa y de los datos del usuario provenientes de la capa superior.

La información de control contenida en la cabecera de una PDU varía según la capa, pero suele incluir elementos críticos como direcciones, números de secuencia y códigos de detección de errores para asegurar que la información no se haya dañado durante la transmisión. Conforme los datos descienden por la pila de protocolos, cada nivel trata a la PDU del nivel superior como simples datos y le añade su propia información, repitiendo el proceso hasta alcanzar la capa física para su transmisión real.

2.5. ¿Qué es una arquitectura de protocolos?

Es una estructura organizada en capas de elementos de hardware y software diseñada para facilitar el intercambio de datos entre sistemas y permitir el funcionamiento de aplicaciones distribuidas. Se basa en la división de la lógica de comunicación en subtareas independiente donde en lugar de tener un único módulo que realice todas las funciones de comunicación, el problema se descompone en módulos más pequeños dispuestos en una pila vertical o jerárquica. Cada nivel o capa de esta arquitectura se encarga de realizar un subconjunto de tareas relacionadas entre sí, necesarias para la comunicación con otro sistema.

Los principios fundamentales que rigen una arquitectura de protocolos incluyen:

- Independencia de las capas: Las capas se definen de tal manera que las funciones más básicas se delegan a las inferiores, ocultando los detalles técnicos a los niveles superiores.
- Prestación de servicios: Cada capa proporciona un conjunto específico de servicios a la capa inmediatamente superior, de modo que los cambios en un nivel no deberían requerir modificaciones en los demás.
- Comunicación entre pares: La comunicación real se logra mediante el intercambio de bloques de datos entre capas correspondientes (entidades pares) de diferentes sistemas, siguiendo reglas o convenciones denominadas **protocolos**.

2.6. ¿Qué es TCP/IP?

Es una arquitectura de protocolos organizada en capas que constituye la base fundamental de Internet y de la mayoría de los productos comerciales de red actuales. TCP/IP se define como una estructura de elementos de hardware y software diseñada para facilitar el intercambio de datos entre sistemas, dividiendo las funciones de comunicación en cinco capas independientes:

- Capa física: Especifica la interfaz física entre el dispositivo y el medio de transmisión, incluyendo la naturaleza de las señales y la velocidad de los datos.
- Capa de acceso a la red: Se encarga del intercambio de datos entre el sistema final y la red a la que está conectado.
- Capa internet: Su función es permitir que los datos atraviesen múltiples redes interconectadas mediante el uso de routers.
- Capa de transporte: Garantiza que los datos lleguen a la aplicación de destino de forma fiable y en el mismo orden en que fueron enviados.
- Capa de aplicación: Contiene la lógica necesaria para admitir diversas aplicaciones de usuario.

2.7. ¿Qué ventajas aporta una arquitectura en capas como la usada en TCP/IP?

Una arquitectura en capas aporta la ventaja principal de simplificar la complejidad de la comunicación al dividir el proceso global en subtareas o módulos más pequeños y manejables. Esta estructura jerárquica permite que cada nivel se centre en funciones específicas, delegando los detalles técnicos de las tareas más básicas a las capas inferiores de manera transparente.

Otra ventaja es la independencia entre capas, lo que garantiza que los cambios, innovaciones o sustituciones de protocolos en un nivel determinado no afecten al funcionamiento ni requieran modificaciones en el resto de la pila. Esto facilita enormemente el mantenimiento y la evolución tecnológica, permitiendo que las capas superiores operen correctamente sin importar la tecnología de red específica utilizada abajo.

Finalmente, este diseño favorece la estandarización e interoperatividad, permitiendo que dispositivos de diferentes fabricantes puedan comunicarse de manera efectiva al seguir convenciones comunes en cada nivel. Esto no solo dota al usuario de mayor flexibilidad en la selección de equipos, sino que también estimula la producción masiva y ayuda a reducir los costes del hardware y software de comunicaciones.

2.8. ¿Qué es un encaminador?

Es un procesador cuya función principal es conectar dos o más redes y retransmitir datos entre ellas, actuando como un "porteador" que transporta bloques de datos de una red a otra, determinando la ruta adecuada para que la información alcance su destino final a través de la interconexión de redes. Permite que los datos atraviesen múltiples subredes interconectadas, haciendo que los sistemas finales puedan comunicarse aunque no estén en la misma red física.

En la arquitectura TCP/IP, el encaminador implementa el Protocolo Internet. Cuando recibe un paquete, elimina la cabecera de la red de origen, examina la dirección de destino en la cabecera IP y direcciona el paquete a través de la siguiente subred, añadiendo una nueva cabecera de acceso a la red.
