---
title: 🌐 UP1.5. Arquitecturas de red y niveles que las componen - CE1.d)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| d) Se han descrito las arquitecturas de red y los niveles que las componen. | Teórico |  15 % | 

### 1. Introducción
Las redes actuales están formadas por una gran variedad de dispositivos, sistemas operativos y aplicaciones desarrollados por diferentes fabricantes. Sin embargo, todos ellos son capaces de comunicarse entre sí gracias a que utilizan una serie de **arquitecturas de red** y **protocolos estandarizados**.

Una arquitectura de red define la forma en que se organiza la comunicación entre dispositivos, dividiéndola en distintos niveles o capas. Cada nivel desempeña una función específica y coopera con el resto para conseguir que la información llegue correctamente desde el emisor hasta el receptor. Gracias a esta organización por capas es posible desarrollar nuevas tecnologías o sustituir determinados componentes sin modificar completamente el funcionamiento de la red.

### 2. ¿Qué es una arquitectura de red?
Una **arquitectura de red** es un modelo que organiza el proceso de comunicación entre dispositivos dividiendo las funciones necesarias en distintos niveles o capas. Cada capa tiene una misión concreta y ofrece servicios a la capa superior mientras utiliza los servicios de la capa inferior. Este diseño aporta numerosas ventajas:

- Facilita el diseño de redes.
- Simplifica la resolución de problemas.
- Favorece la interoperabilidad entre fabricantes.
- Permite la evolución independiente de cada tecnología.
- Facilita el aprendizaje y la documentación de las redes.

### 3. ¿Por qué se utilizan modelos por capas?
Imaginemos que queremos enviar un correo electrónico. Aunque para el usuario la operación parece sencilla, realmente intervienen numerosas funciones:

- La aplicación prepara el mensaje.
- El sistema operativo organiza la comunicación.
- Se determina la dirección del destinatario.
- Los datos se fragmentan.
- Se transmiten por el medio físico.
- El equipo receptor reconstruye la información.

Si todas estas tareas estuvieran mezcladas, el desarrollo y mantenimiento de las redes sería extremadamente complejo. Por este motivo se utilizan **arquitecturas por capas**, donde cada nivel realiza una función específica.

### 4. Principales arquitecturas de red
Actualmente existen dos modelos de referencia fundamentales:

- Modelo OSI.
- Modelo TCP/IP.

El primero tiene un carácter principalmente didáctico y sirve para comprender el funcionamiento de las redes. El segundo constituye la arquitectura utilizada realmente en Internet y en prácticamente todas las redes actuales.

### 5. El modelo OSI
El **Modelo OSI (Open Systems Interconnection)** fue desarrollado por la Organización Internacional de Normalización (ISO) con el objetivo de establecer un modelo común para las comunicaciones entre sistemas abiertos. Está formado por **siete capas**, cada una especializada en una función determinada.

<img
  src="/PAR/diagrams/osi.png"
  alt="Modelo OSI"
  class="diagram-img"
  style="width:500px; height:auto;"
  loading="lazy"
/>

#### Capa 1. Física
Es la capa encargada de transmitir los bits a través del medio físico. Trabaja con:

- Cables.
- Fibra óptica.
- Ondas de radio.
- Conectores.
- Voltajes.
- Señales eléctricas y luminosas.

No interpreta la información; únicamente transporta bits.

**Ejemplos de dispositivos**

- Cable UTP.
- Fibra óptica.
- Repetidores.
- Hubs.

#### Capa 2. Enlace de datos
Se ocupa de la comunicación entre dispositivos conectados a la misma red física. Sus principales funciones son:

- Direccionamiento mediante direcciones MAC.
- Detección de errores.
- Control de acceso al medio.
- Creación de tramas.

**Ejemplos**

- Ethernet.
- Wi-Fi.
- Switches.

#### Capa 3. Red
Permite que los datos puedan viajar entre diferentes redes. Sus funciones principales son:

- Direccionamiento lógico.
- Selección de rutas.
- Encaminamiento de paquetes.

Aquí aparece el protocolo IP.

**Dispositivos**

- Routers.
- Equipos de nivel 3.

#### Capa 4. Transporte
Garantiza que la información llegue correctamente al destino. Entre sus funciones destacan:

- Segmentación.
- Control de errores.
- Control de flujo.
- Confirmación de recepción.

Los protocolos más conocidos son:

- TCP.
- UDP.

#### Capa 5. Sesión
Gestiona el establecimiento, mantenimiento y finalización de las comunicaciones entre aplicaciones. Aunque muchas de sus funciones se encuentran integradas actualmente en otros protocolos, sigue formando parte del modelo OSI.

#### Capa 6. Presentación
Se ocupa del formato de los datos. Entre sus funciones encontramos:

- Cifrado.
- Compresión.
- Conversión de formatos.
- Codificación de caracteres.

Gracias a esta capa, aplicaciones desarrolladas en sistemas diferentes pueden intercambiar información correctamente.

#### Capa 7. Aplicación
Es la capa más cercana al usuario. Proporciona los servicios que utilizan las aplicaciones. Ejemplos:

- HTTP.
- HTTPS.
- FTP.
- SMTP.
- DNS.
- DHCP.

Es importante recordar que esta capa **no es la aplicación**, sino el conjunto de protocolos que permiten a las aplicaciones utilizar la red.

#### Resumen del modelo OSI

| Capa | Nombre | Función principal |
|------:|---------|------------------|
| 7 | Aplicación | Servicios de red para las aplicaciones |
| 6 | Presentación | Formato, compresión y cifrado |
| 5 | Sesión | Gestión de las comunicaciones |
| 4 | Transporte | Entrega fiable de los datos |
| 3 | Red | Direccionamiento y encaminamiento |
| 2 | Enlace | Comunicación dentro de la misma red |
| 1 | Física | Transmisión de bits |

### 6. El modelo TCP/IP
Aunque el modelo OSI es el más utilizado para explicar el funcionamiento de las redes, Internet funciona utilizando la **arquitectura TCP/IP**. Este modelo es más sencillo y está compuesto por **cuatro capas**.

<img
  src="/PAR/diagrams/tcpip.png"
  alt="Modelo TCP/IP"
  class="diagram-img"
  style="width:500px; height:auto;"
  loading="lazy"
/>

#### Capa 1. Acceso a la red
Incluye todo lo relacionado con el acceso físico al medio. Equivale aproximadamente a las capas Física y Enlace del modelo OSI. Ejemplos:

- Ethernet.
- Wi-Fi.
- Fibra óptica.

#### Capa 2. Internet
Su función consiste en transportar los paquetes entre diferentes redes. El protocolo principal es:

- IP (Internet Protocol)

También trabajan aquí protocolos como:

- ICMP.
- ARP (en IPv4).

#### Capa 3. Transporte
Se encarga de garantizar la comunicación entre aplicaciones. Los protocolos fundamentales son:

- TCP.
- UDP.

#### Capa 4. Aplicación
Agrupa todas las funciones relacionadas con los servicios utilizados por las aplicaciones. Ejemplos:

- HTTP.
- HTTPS.
- FTP.
- DNS.
- SMTP.
- SSH.

### 7. Relación entre el modelo OSI y TCP/IP
Aunque ambos modelos presentan un número diferente de capas, desempeñan funciones similares.

<img
  src="/PAR/diagrams/osi-tcpip.png"
  alt="Modelo OSI vs TCP/IP"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

El modelo TCP/IP simplifica las funciones del modelo OSI agrupando varias capas.

### 8. ¿Qué modelo se utiliza realmente?
En la práctica:

- El **modelo OSI** se utiliza como herramienta de aprendizaje y para analizar el funcionamiento de las redes.
- El **modelo TCP/IP** es la arquitectura utilizada en Internet y en la mayoría de las redes actuales.

Ambos modelos son complementarios y es importante conocerlos.

### 9. Beneficios de la organización por capas
El diseño por capas aporta numerosas ventajas:

- Facilita el desarrollo de nuevos protocolos.
- Permite sustituir tecnologías sin afectar al resto de la arquitectura.
- Simplifica la resolución de incidencias.
- Favorece la interoperabilidad entre fabricantes.
- Hace posible la evolución continua de las redes.

Por ejemplo, la sustitución del cable de cobre por fibra óptica afecta principalmente a la capa física, mientras que las aplicaciones siguen funcionando sin modificaciones.

### 10. Caso práctico
Una empresa va a renovar la infraestructura de comunicaciones de su sede principal.

Durante el proyecto se plantea sustituir el cableado de cobre por fibra óptica, instalar nuevos switches y routers, actualizar los protocolos de comunicación y desplegar nuevos servicios web accesibles desde Internet.

El responsable del departamento de sistemas debe analizar cómo afectan estos cambios a la arquitectura de la red y determinar qué capas del modelo OSI y del modelo TCP/IP intervienen en cada uno de ellos.

> **Analiza la situación e identifica cómo participa cada nivel de las arquitecturas de red en el funcionamiento de la nueva infraestructura, justificando el papel que desempeña cada capa.**