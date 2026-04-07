# Trabajo Practico N°2

**Nombres**

- Constanza Medran  
- Fabian N Hidalgo  
- Juan I Vizgarra  
- Sofia V Castro

**Enredados**

**Universidad Nacional de Córdoba - Facultad de Ciencias Exactas Fisicas y Naturales**  

**Redes de Computadoras** 

**Santiago M. Henn - Facundo N. Oliva Cuneo** 

**29/03/2026**

---

### Información de los autores

* **Información de contacto**: *victoria.castro@mi.unc.edu.ar - fabian.hidalgo@mi.unc.edu.ar - constanza.medran@mi.unc.edu.ar - juan.vizgarra@mi.unc.edu.ar*

---

## Resumen

En el presente trabajo práctico se realizaron actividades relacionadas con la capa física y la capa de enlace de datos de las redes de computadoras, incluyendo la construcción y verificación de cables Ethernet bajo la norma T568A/B, la utilización de equipamiento de red empresarial y la configuración básica de una red local. 

En la primera parte se construyó un cable UTP derecho, el cual fue posteriormente verificado mediante inspección visual y pruebas eléctricas utilizando un tester de cables. 

En la segunda parte se trabajó con un switch Cisco Catalyst, identificando sus características principales, sus interfaces y su funcionamiento básico, además de intentar acceder a su consola mediante conexión serial utilizando PuTTY. Finalmente, se realizaron pruebas de conectividad entre computadoras conectadas al switch y se analizaron aspectos del tráfico de red como ARP e ICMP. Este trabajo permitió tomar contacto práctico con los elementos físicos de una red y comprender su funcionamiento básico dentro de una red local.

**Palabras clave**: *redes de computadoras, cable UTP, T568A, T568B, Ethernet, switch Cisco, ARP, ICMP, red local, capa física*

---

## Introducción

Las redes de computadoras están compuestas por diferentes capas que permiten la transmisión de información desde un dispositivo a otro. 

Las capas más bajas del modelo de red corresponden a la capa física y la capa de enlace de datos, las cuales se encargan de la transmisión de bits a través del medio físico y del envío de tramas dentro de una red local. Para comprender el funcionamiento de estas capas no solo es necesario estudiar los conceptos teóricos, sino también interactuar con el equipamiento físico y los elementos reales de una red.

En este trabajo práctico se realizaron actividades orientadas a la construcción de cables de red Ethernet, la verificación de su correcto funcionamiento y la utilización de equipamiento de red como switches empresariales Cisco. Además, se realizaron configuraciones básicas de red y pruebas de conectividad entre computadoras conectadas a un switch, observando el comportamiento de protocolos como ARP e ICMP. 

El objetivo principal del trabajo fue tomar contacto con los componentes físicos de una red, comprender su funcionamiento y relacionar los conceptos teóricos vistos en clase con su implementación práctica.

---

## Marco teórico

Las redes Ethernet utilizan cables de par trenzado (UTP) para la transmisión de datos en redes locales. Estos cables están formados por pares de conductores trenzados que reducen las interferencias electromagnéticas. Para la construcción de cables Ethernet se utilizan normas de cableado como T568A y T568B, que definen el orden de los colores de los conductores dentro del conector RJ-45. Un cable puede ser derecho o cruzado, dependiendo de la disposición de los pares en cada extremo, siendo el cable derecho el más utilizado para conectar computadoras a switches.

Los switches son dispositivos de red que operan principalmente en la capa de enlace de datos (Capa 2 del modelo OSI) y se encargan de reenviar tramas Ethernet dentro de una red local utilizando direcciones MAC. Estos dispositivos mantienen una tabla de direcciones MAC que les permite enviar las tramas únicamente al puerto donde se encuentra el dispositivo destino, mejorando la eficiencia de la red en comparación con los hubs.

Para la administración de switches empresariales, como los Cisco Catalyst, se puede acceder mediante un puerto de consola utilizando una conexión serial y software de terminal como PuTTY. Desde allí se pueden configurar parámetros de red, contraseñas, VLANs y otras funciones del dispositivo.

Cuando dos computadoras se comunican dentro de una red local, utilizan protocolos como ARP (Address Resolution Protocol) para resolver direcciones IP en direcciones MAC, y ICMP (Internet Control Message Protocol) para verificar conectividad mediante herramientas como el comando ping. Estos protocolos permiten el funcionamiento básico de la comunicación dentro de redes locales y son fundamentales para el diagnóstico y análisis de tráfico de red.

---

## Resultados

### _Parte 1: Armado y verificación de cables Cat5/Cat5e bajo estándar T568A/B_

#### 1) Investigar los pasos para crimpar un cable bajo la norma T568A/B DERECHO. No cruzado. 

<img width="1500" height="1000" alt="image" src="https://github.com/user-attachments/assets/aa3320e9-3a80-466a-9c9e-c46bc94d9ab6" />

Pasos para construcción de cable con norma T568A/B DERECHO no cruzado:

    a. Se corta cable UTP del largo neccesario (en nuestro caso fue de 1.5 m)

    b. Se corta un poco de la cubierta exterior, lo cual deja visible los 4 pares de cables trenzados.

    c. Se agregan los 2 capuchones.

    d. Se desenriedan y ordenan los cables segun el orden de colores antes mencionado y se insertan en el conector RJ-45 asegurandonos que lleguen lo mas al fondo posible.

    e. Se colocá el conector en la pinza crimpeadora y se presiona fuerte hasta que haga click. Esto fija los pines y asegura el contacto eléctrico.


#### 2) Construir 1 (un) cable por grupo, de 1 - 1.5 m. aproximadamente. Tipo DERECHO, NO CRUZADO.

| | | |
|---|---|---|
|<img src="https://github.com/user-attachments/assets/0bf6f3a8-793a-4239-b576-f15ca4d34aa1" width="200"><br>|<img src="https://github.com/user-attachments/assets/e3e72264-73f6-4712-9286-8dd5f40d6be4" width="200"><br>|<img src="https://github.com/user-attachments/assets/43d7ecf1-2761-4461-9639-7969dd66467a" width="200"><br>

#### 3) VERIFICAR la buena construcción de un cable. Para ello, buscar otro grupo e intercambiar cables.

a) Inspección visual para la calidad constructiva

Por lo que se puede ver el cable de nuestros compañeros parece estar en muy buen estado, todos los cables llegan al fondo del conector, tienen la misma longitud y estan bien crimpeados. El capuchon cubre la unión perfectamente lo cual protege bien al cable y pasa con exito el testeo de cables con el tester.

b) Verificación eléctrica utilizando un tester para cables ethernet.

<img src="https://github.com/user-attachments/assets/9d64f49f-fc24-46f7-94bf-6001e4439e1e" width="200"><br>

#### 4) Documentar con que grupo intercambiaron cables. Tomar fotografías que evidencien el proceso técnico de verificación.

Grupo The Lords of Pings:

<img src="https://github.com/user-attachments/assets/d4fc9df7-bf37-4f55-8941-94b4a3e6a147" width="200"><br>

https://github.com/user-attachments/assets/7675bf64-da65-45b1-b979-05253304d359

---

### Parte 2: Equipamiento físico, verificación y utilización de equipos de red y análisis de tráfico.

#### 1) Utilizando internet y el datasheet del switch Cisco, documentar las características principales del mismo.

Switch CISCO CATALYST 2950 SERIES:<br>

| | |
|---|---|
|<img src="https://github.com/user-attachments/assets/89f74f5f-bb62-4d36-b74e-922ee695cd16" width="200"><br>|<img src="https://github.com/user-attachments/assets/d1bdd4d0-6202-443c-b306-c784b9fdb66b" width="200"><br>|

_I. Descripción general_

    - Switch gestionable (managed) de configuración fija.
    - Diseñado para redes pequeñas y medianas (LAN de acceso).
    - Opera en Capa 2 (Switching Ethernet).
    - Usa Cisco IOS.
    - Soporta tráfico de datos, voz y video.
    - Configuración mediante:
        CLI
        Web (Cisco Device Manager)
        Cisco Network Assistant

_II. Modelos y puertos_

Distintas variantes según cantidad de puertos: 12, 24 o 48 puertos Fast Ethernet (10/100 Mbps)

Uplink: es un puerto de alta capacidad en un switch utilizado para conectarlo con otros dispositivos de red, permitiendo la comunicación con redes superiores.

    Uplinks:
    - Fibra (1000BASE-SX) en modelos SX
    - Cobre (10/100/1000) en modelos T
    
    - 2950-12 → 12 puertos
    - 2950-24 → 24 puertos
    - 2950T-48 → 48 + uplinks Gigabit cobre
    - 2950SX-48 → 48 + uplinks fibra

_III. Rendimiento_

    Switching fabric es el sistema interno del switch que mueve los datos entre los puertos.
    - Switching fabric: Hasta 13.6 Gbps
    
    Forwarding es el proceso de enviar un paquete desde un puerto de entrada al puerto de salida correcto. Cuántos paquetes puede procesar.
    - Forwarding: Hasta 10.1 Mpps
    
    Funcionamiento a wire-speed (máximo rendimiento en todos los puertos)
    - Buffer compartido: 8 MB
    - Tabla MAC: hasta 8000 direcciones

_IV. Funciones de red_

    Conectividad:
        Soporta VLANs (IEEE 802.1Q)
        Soporta Trunking (técnica que permite que un mismo enlace físico transporte tráfico de múltiples VLANs. Sirve para conectar switch con switch, switch con router o extender VLANs a través de la red)
        Soporta EtherChannel (agregación de enlaces)
    Multicast:
        IGMP Snooping (optimiza tráfico multicast)

_V. Seguridad_

Incluye múltiples mecanismos:

    Port Security (por MAC)
    802.1X (autenticación por puerto)
    SSH v2 (acceso seguro)
    VLAN privada (aislamiento de puertos)
    Autenticación con:
        RADIUS
        TACACS+

_VI. Calidad de servicio (QoS)_

    Priorización de tráfico (voz, datos críticos)
    4 colas de salida por puerto
    Algoritmos:
        Strict Priority
        WRR (Weighted Round Robin)
        Clasificación por CoS (802.1p)

_VII. Gestión y administración_

    SNMP (v1, v2, v3)
    CLI (consola)
    Web GUI (Cisco Device Manager)
    Cisco Network Assistant:
        Configuración masiva
        Monitoreo
        Soporte RMON (monitoreo de red)
        SPAN (análisis de tráfico)

_VIII. Características físicas_

    Formato rack 1U
    Conectores:
        RJ-45 (UTP)
        Fibra (MT-RJ en modelos SX)
        LEDs de estado por puerto
    Alimentación:
        100–240V AC
    Consumo:
        30W a 45W

_IX. Estándares soportados_

    IEEE:
        802.3 (Ethernet)
        802.3u (Fast Ethernet)
        802.3z (Gigabit)
        802.1Q (VLAN)
        802.1p (QoS)
        802.1X (seguridad)

#### 2) Elaborar checklists (manuales, indicaciones) de procedimientos para las siguientes actividades:

a) Conectar una PC al puerto de consola del switch Cisco a 9600 baudios utilizando PUTTY. Turnense para verificar el acceso a la consola del Switch.

    Requerimientos: PuTTY previamente instalado

    Pasos:
    1) Conectar el cable consola al puerto Console del switch y el otro extremo a la PC.

    2) Asegurarse de tener el drivevr para reconocerlo (en nuestro caso tuvimos que descargarlo) y revisar el puerto en que se reconoce (COM).

    3) Abrir PuTTY y configurarlo para conexión serial de 9600 baudios y en el COM correspondiente (del punto 2).

    4) Presionar Open y enter hasta que aparezca el prompt del switch.

    Nuestra experiencia: luego de tener inconvenientes con el driver, una vez que se instalo correctamente no se logro la conexión porque a pesar de que aparecia el dispositivo en el COM5, a la hora de configurarlo en PuTTY no lo registraba bien por lo que esta parte de la experiencia no la pudimos terminar de realizar bien pero escribimos aqui todo lo que tendria que pasar en teoría.

b) Acceder a las opciones de administración del switch y modificar claves de acceso.

    1) Acceso al modo privilegiado:

    enable

    2) Entrar a configuración global:

    configure terminal

    3) Cambiar contraseña de modo privilegiado:

    enable secret NUEVA_CLAVE

    4) Configurar contraseña de consola:

    line console 0
    password NUEVA_CLAVE
    login

    5) Guardar configuración:

    end
    write memory

    Nuestra experiencia: Nuestros compañeros pudieron ingresar hasta el prompt pero no se sabian las contraseñas por lo que no se pudo seguir con la configuración.

c) Conectar computadoras al switch, configurar una red y testear conectividad.

    1) Conectar las PCs a un puerto del switch y verificar con las luces si esta bien la conexión (UP verde).

    2) Configuración de IP en PCs: en cada PC ir a configuración de red y asignar IP y máscara manual.

    3) Verificar configuración.

    4) Test de conectividad: hacer ping con otra IP de la red.

#### 2) De a dos o más grupos por switch, conectarán una computadora por cada grupo al mismo utilizando los cables que tengan de la parte 1 de este TP. Verificar que pueden llegar a la PC de otro grupo usando ping o captura de paquetes.

**Nuestra experiencia**: los cables conectaron bien basados en las luces de los puertos pero no llegamos a configurar las IPs de cada PC por lo que los pings que realizamos nunca llegaron a destino.

---

## Discusión y conclusiones

Durante la realización del trabajo práctico se pudo observar la importancia de los elementos físicos en el funcionamiento de una red de computadoras. La construcción del cable Ethernet permitió comprender la estructura interna de los cables UTP y la importancia de respetar las normas de cableado para asegurar una correcta transmisión de datos. La verificación mediante inspección visual y tester permitió comprobar la continuidad eléctrica y detectar posibles errores de construcción.

En la segunda parte del trabajo se tomó contacto con equipamiento de red real, como switches Cisco, lo que permitió comprender mejor su funcionamiento, sus interfaces y las formas de administración mediante consola. Si bien se presentaron algunas dificultades para acceder a la consola del switch y configurar la red correctamente, la experiencia permitió comprender el procedimiento necesario para la configuración de equipos de red empresariales.

Las pruebas de conectividad entre computadoras permitieron observar la importancia de la correcta configuración de direcciones IP y máscaras de red para que los dispositivos puedan comunicarse dentro de una red local. Además, el análisis del tráfico permitió relacionar los protocolos ARP e ICMP con el proceso real de comunicación entre dispositivos.

En conclusión, el trabajo práctico permitió complementar los conocimientos teóricos con experiencia práctica en el armado de cables, utilización de equipamiento de red y configuración básica de redes locales, proporcionando una mejor comprensión del funcionamiento de las capas físicas y de enlace de datos en redes de computadoras.

---

## Referencias

[1] - Stallings - Comunicacion y Redes de Computadores

[2] - Cisco Systems - Cisco Catalyst 2950 Series Switches Data Sheet

[3] - Putty.org - PuTTY User Manual
