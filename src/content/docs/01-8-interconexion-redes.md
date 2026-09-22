---
title: 🌐 UP1.8. Dispositivos de interconexión de redes según el nivel funcional en el que se encuadran - CE1.h)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| h) Se han diferenciado los dispositivos de interconexión de redes atendiendo al nivel funcional en el que se encuadran. | Teórico |  15 % | 

### 1. Introducción
Una red de datos está formada por numerosos dispositivos que permiten conectar equipos, intercambiar información y facilitar la comunicación entre diferentes redes. Sin embargo, **no todos los dispositivos realizan la misma función**. Algunos simplemente transmiten señales eléctricas, mientras que otros analizan direcciones MAC, direcciones IP o incluso información de las aplicaciones.

Para comprender cómo funciona una red es necesario conocer los **dispositivos de interconexión** y relacionarlos con la **capa del modelo OSI** en la que desarrollan su función principal. Este conocimiento permitirá al administrador de redes seleccionar el dispositivo más adecuado para cada situación, diseñar infraestructuras eficientes y diagnosticar incidencias de forma más sencilla.

### 2. ¿Qué es un dispositivo de interconexión?
Un **dispositivo de interconexión** es un equipo de red cuya función consiste en conectar dispositivos, segmentos o redes para permitir el intercambio de información. Dependiendo de la información que sea capaz de analizar, cada dispositivo trabaja principalmente en una o varias capas del modelo OSI.

```text
                              Dispositivos de interconexión

                                          │
                      ┌───────────────────┼───────────────────┐
                      │                   │                   │
                  Capa Física         Capa Enlace         Capa Red
                      │                   │                   │
                  Repetidor             Switch              Router
                     Hub                Bridge              Gateway
```

### 3. Clasificación según el modelo OSI
Los dispositivos de interconexión pueden clasificarse según la capa del modelo OSI en la que desarrollan su función principal.

| Capa OSI | Dispositivos |
|-----------|--------------|
| Capa 1. Física | Repetidor, Hub |
| Capa 2. Enlace de datos | Bridge, Switch, Punto de acceso (AP) |
| Capa 3. Red | Router, Switch de capa 3 |
| Capas superiores | Gateway, Firewall, Proxy |

### 4. Dispositivos de la capa física
Los dispositivos de la **capa física** únicamente trabajan con señales eléctricas, luminosas o de radio. No interpretan direcciones MAC ni direcciones IP. Su misión consiste en transportar los bits.

#### 4.1. Repetidor
El **repetidor** es uno de los dispositivos más sencillos. Su función consiste en regenerar la señal cuando esta pierde intensidad debido a la distancia.

```text
PC ───── Repetidor ───── PC
```

>💡 **Características:** Trabaja en la capa Física, regenera la señal, no interpreta los datos y amplía la distancia máxima de una red.

>✅ **Ventajas:** Muy sencillo, económico y aumenta el alcance de la comunicación.

>❌ **Inconvenientes:** No reduce el tráfico, no filtra información y actualmente apenas se utiliza en redes LAN.

#### 4.2. Hub (Concentrador)
El **Hub** conecta varios equipos formando un único segmento de red. Cuando recibe información por un puerto, la retransmite a todos los demás.

```text
      PC1
       │
PC2───Hub───PC3
       │
      PC4
```

>💡 **Características:** Trabaja en la capa Física, no conoce direcciones MAC, todos los equipos reciben todas las tramas y comparte el ancho de banda.

>✅ **Ventajas:** Muy económico y fácil instalación.

>❌ **Inconvenientes:** Muchas colisiones, bajo rendimiento, escasa seguridad  y pácticamente ha desaparecido.

### 5. Dispositivos de la capa de enlace
Estos dispositivos ya son capaces de interpretar las **direcciones MAC**. Gracias a ello pueden enviar la información únicamente al dispositivo destinatario.

#### 5.1. Bridge (Puente)
El **Bridge** conecta dos segmentos de una misma red. Aprende las direcciones MAC y decide por qué interfaz debe enviar cada trama.

```text
LAN 1 ─── Bridge ─── LAN 2
```

Actualmente su función ha sido asumida casi completamente por los switches.

#### 5.2. Switch
El **Switch** es el dispositivo más utilizado en las redes LAN actuales. Aprende automáticamente la dirección MAC de cada equipo conectado. Cuando recibe una trama únicamente la envía al puerto donde se encuentra el destinatario.

```text
       PC1
        │
PC2───Switch───PC3
        │
       PC4
```

El switch mantiene una **tabla MAC** similar a la siguiente:

| Dirección MAC | Puerto |
|---------------|--------|
| AA:11:22 | 1 |
| BB:33:44 | 2 |
| CC:55:66 | 3 |
| DD:77:88 | 4 |

Gracias a esta tabla evita enviar información innecesaria.

>✅ **Ventajas:** Reduce el tráfico, elimina prácticamente las colisiones, mayor rendimiento, mayor seguridad y permite crear VLAN.

>❌ **Inconvenientes:** Precio superior al Hub y requiere configuración en redes complejas.

#### 5.3. Punto de acceso (Access Point)
Un **Access Point (AP)** conecta dispositivos inalámbricos con una red Ethernet.

```text
Portátil ))))

          Access Point ───── Switch  

Smartphone ))))
```

Trabaja principalmente en la capa de Enlace, ya que actúa como puente entre la red inalámbrica y la red cableada.

### 6. Dispositivos de la capa de red
Estos dispositivos trabajan con **direcciones IP**. Su misión consiste en comunicar redes diferentes.

#### 6.1. Router
El **Router** conecta varias redes entre sí. Analiza la dirección IP de destino y determina el mejor camino para enviar los paquetes.

```text
Red A ─── Router ─── Internet ─── Router ─── Red B
```

>💡 **Funciones:** Interconectar redes, encaminar paquetes, seleccionar rutas, separar dominios de broadcast y conectar redes locales con Internet.

>✅ **Ventajas:** Permite comunicar distintas redes, es escalable, admite múltiples protocolos y mejora la organización de la infraestructura.

>❌ **Inconvenientes:** Limitaciones de cobertura inalámbrica e interferencias y conlleva riesgos de seguridad en la red.

#### 6.2. Switch de capa 3
Los **Switches multicapa** combinan las funciones de un switch tradicional con las capacidades de encaminamiento de un router. Se utilizan habitualmente en:

- Grandes empresas.
- Universidades.
- Centros de datos.

Permiten realizar enrutamiento entre VLAN con un rendimiento muy elevado.


### 7. Dispositivos de capas superiores
Algunos dispositivos trabajan analizando información perteneciente a las capas superiores del modelo OSI.

#### 7.1. Gateway
Un **Gateway** permite la comunicación entre sistemas que utilizan protocolos diferentes. Por ejemplo:

- Red IPv4 ↔ IPv6.
- Red local ↔ Servicios Cloud.
- Redes industriales ↔ Redes IP.

Actúa como un traductor entre tecnologías distintas.

#### 7.2. Firewall
El **Firewall** controla el tráfico que entra y sale de la red. Puede permitir o bloquear conexiones en función de:

- Dirección IP.
- Puerto.
- Protocolo.
- Aplicación.
- Usuario.

Es uno de los principales mecanismos de seguridad de una red.

#### 7.3. Proxy
Un **Proxy** actúa como intermediario entre los clientes y los servidores. Sus funciones principales son:

- Filtrado de contenidos.
- Caché web.
- Anonimización.
- Control del acceso a Internet.

### 8. Comparativa de dispositivos

| Dispositivo | Capa OSI | Función principal |
|--------------|---------|-------------------|
| Repetidor | 1 | Regenera la señal. |
| Hub | 1 | Reenvía la señal a todos los puertos. |
| Bridge | 2 | Une dos segmentos utilizando direcciones MAC. |
| Switch | 2 | Conecta equipos dentro de una LAN utilizando direcciones MAC. |
| Access Point | 2 | Conecta dispositivos Wi-Fi con una red Ethernet. |
| Router | 3 | Comunica redes diferentes mediante direcciones IP. |
| Switch multicapa | 3 | Conmutación y enrutamiento entre VLAN. |
| Firewall | 3-7 | Filtra y protege el tráfico de red. |
| Proxy | 7 | Intermediario entre clientes y servidores. |
| Gateway | Variable | Traduce entre protocolos o arquitecturas diferentes. |

### 9. ¿Cómo circula la información?
Supongamos que un ordenador accede a una página web.

```text
PC
 ↓
Switch
 ↓
Router
 ↓
Internet
 ↓
Servidor Web
```

Durante esta comunicación:

- El **Switch** utiliza la dirección MAC para entregar la trama dentro de la red local.
- El **Router** utiliza la dirección IP para enviar el paquete hacia otra red.
- Los **Firewalls** controlan el tráfico permitido.
- El **Servidor Web** responde utilizando los protocolos HTTP o HTTPS.

Cada dispositivo desempeña una función diferente dentro de la comunicación.

### 10. Evolución de los dispositivos de red

Con el paso del tiempo algunos dispositivos han quedado prácticamente en desuso.

| Dispositivo | Situación actual |
|--------------|------------------|
| Repetidor | Poco frecuente. |
| Hub | Prácticamente desaparecido. |
| Bridge | Sustituido por switches. |
| Switch | Muy utilizado. |
| Router | Imprescindible. |
| Firewall | Imprescindible. |
| Access Point | Muy utilizado. |
| Switch multicapa | Muy utilizado en redes empresariales. |

### 11. Caso práctico
Una empresa va a inaugurar una nueva sede con cuatro plantas. Cada planta contará con varias oficinas conectadas mediante una red Ethernet y dispondrá de cobertura Wi-Fi para empleados y visitantes. Además, todas las plantas deberán comunicarse entre sí y compartir el acceso a Internet, los servidores corporativos y los servicios de impresión. La dirección de la empresa solicita al departamento de sistemas que diseñe la infraestructura de interconexión, seleccionando los dispositivos adecuados para cada parte de la red y justificando su función dentro de la arquitectura.

> **Analiza la infraestructura propuesta e identifica qué dispositivos de interconexión serían necesarios, indicando en qué capa del modelo OSI trabajan principalmente y justificando por qué son adecuados para cada función.**