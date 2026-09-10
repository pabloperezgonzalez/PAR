---
title: 🌐 UP1.6. El concepto de protocolo de comunicación - CE1.e)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| e) Se ha descrito el concepto de protocolo de comunicación. | Teórico | 10 % | 

### 1. Introducción
Cuando dos personas desean comunicarse deben utilizar un idioma común y respetar unas normas básicas de comunicación. Por ejemplo, una conversación resulta imposible si cada persona habla un idioma diferente o si ambas hablan al mismo tiempo sin respetar los turnos.

En las redes de datos ocurre exactamente lo mismo. Los dispositivos que forman parte de una red necesitan un conjunto de reglas que les indiquen **cómo iniciar una comunicación, cómo intercambiar la información y cómo finalizarla correctamente**. Estas reglas reciben el nombre de **protocolos de comunicación**. Sin los protocolos de comunicación sería imposible que dispositivos de distintos fabricantes, sistemas operativos o tecnologías pudieran intercambiar información.

### 2. ¿Qué es un protocolo de comunicación?
Un **protocolo de comunicación** es un conjunto de normas y procedimientos que establece cómo deben intercambiar información dos o más dispositivos conectados a una red.

Los protocolos definen todos los aspectos necesarios para que la comunicación sea correcta, desde el formato de los datos hasta la forma de detectar errores o confirmar la recepción de la información. En otras palabras, un protocolo actúa como un **lenguaje común** que todos los dispositivos deben comprender para poder comunicarse.

```text
                                PROTOCOLOS DE COMUNICACIÓN

                                  Conjunto de reglas
                                           │
                        ┌──────────────────┼──────────────────┐
                        │                  │                  │
                        ▼                  ▼                  ▼
                    Establecen          Organizan          Garantizan
                  la comunicación       los datos        una transmisión
                                                            correcta
                                            │
                                            ▼
                                    Comunicación entre
                                dispositivos de cualquier
                                  fabricante o sistema
```

### 3. ¿Por qué son necesarios los protocolos?
Imaginemos que un ordenador envía información a otro. Antes de transmitir los datos deben resolverse numerosas cuestiones:

- ¿Cómo comienza la comunicación?
- ¿Quién envía primero?
- ¿Cómo se identifica el destinatario?
- ¿Cómo se organiza la información?
- ¿Qué ocurre si se pierde un dato?
- ¿Cómo sabe el emisor que el receptor ha recibido correctamente la información?
- ¿Cómo finaliza la comunicación?

Todas estas reglas están definidas por los protocolos. Sin ellas, cada fabricante utilizaría un sistema diferente y los dispositivos serían incompatibles entre sí.

### 4. Funciones de un protocolo de comunicación
Los protocolos realizan numerosas funciones durante una comunicación. Entre las más importantes destacan:

#### 4.1. Establecimiento de la comunicación
Antes de comenzar el intercambio de información, los dispositivos deben comprobar que ambos están disponibles y preparados para comunicarse.

#### 4.2. Identificación del origen y del destino
Cada mensaje debe indicar:

- Quién envía la información.
- Quién debe recibirla.

Para ello se utilizan direcciones lógicas (IP) y direcciones físicas (MAC), dependiendo del protocolo empleado.

#### 4.3. Formato de los datos
Todos los dispositivos deben interpretar la información de la misma forma. El protocolo establece:

- Cómo se organizan los datos.
- Qué campos contiene cada mensaje.
- Cómo se codifica la información.

#### 4.4. Control de errores
Durante la transmisión pueden producirse errores provocados por interferencias o pérdidas de información. Muchos protocolos incorporan mecanismos para:

- Detectar errores.
- Solicitar el reenvío de la información.
- Garantizar la integridad de los datos.

#### 4.5. Control del flujo
No todos los dispositivos trabajan a la misma velocidad. Los protocolos regulan la cantidad de información transmitida para evitar que un equipo reciba más datos de los que puede procesar.

#### 4.6. Finalización de la comunicación
Cuando el intercambio de información ha terminado, el protocolo establece cómo cerrar correctamente la conexión.

### 5. Características de los protocolos
Los protocolos presentan una serie de características comunes.

#### 5.1. Están estandarizados
La mayoría son desarrollados por organismos internacionales como:

- IEEE.
- IETF.
- ISO.

Gracias a ello pueden comunicarse dispositivos de distintos fabricantes.

#### 5.2. Son independientes del fabricante
Un ordenador con Windows puede comunicarse con un servidor Linux o con un dispositivo Cisco porque todos utilizan los mismos protocolos.

#### 5.3. Trabajan conjuntamente
Una comunicación no utiliza un único protocolo. Por el contrario, intervienen varios protocolos simultáneamente. Por ejemplo, al acceder a una página web pueden intervenir:

- Ethernet.
- IP.
- TCP.
- DNS.
- HTTPS.

Cada uno realiza una función diferente.

### 6. Protocolos y arquitectura por capas
Como ya se estudió en el criterio anterior, las redes se organizan mediante arquitecturas por capas. Cada capa utiliza uno o varios protocolos especializados.

<img
  src="/PAR/diagrams/protocolos.jpeg"
  alt="Protocolos en distintas capas"
  class="diagram-img"
  style="width:500px; height:auto;"
  loading="lazy"
/>

Cada protocolo se comunica únicamente con su equivalente en el dispositivo remoto.

### 7. Principales protocolos de red
A continuación se muestran algunos de los protocolos más utilizados.

| Protocolo | Función |
|-----------|---------|
| IP | Direccionamiento y envío de paquetes entre redes. |
| TCP | Garantiza una transmisión fiable y ordenada. |
| UDP | Transmisión rápida sin confirmación de recepción. |
| HTTP | Acceso a páginas web. |
| HTTPS | Acceso seguro a páginas web mediante cifrado. |
| FTP | Transferencia de archivos. |
| DNS | Traducción de nombres de dominio en direcciones IP. |
| DHCP | Asignación automática de direcciones IP. |
| SMTP | Envío de correo electrónico. |
| IMAP | Acceso y sincronización del correo electrónico. |
| SSH | Administración remota segura de equipos. |

### 8. Ejemplo de comunicación
Cuando un usuario escribe la dirección:

```text
https://portal.edu.gva.es/aules
```

se ponen en funcionamiento numerosos protocolos.

1. El navegador solicita la dirección IP al servidor **DNS**.
2. Se establece una conexión mediante **TCP**.
3. La información viaja utilizando **IP**.
4. La página web se solicita mediante **HTTPS**.
5. Los datos se transmiten físicamente mediante **Ethernet**, **Wi-Fi** o fibra óptica.

Aunque el usuario únicamente observa una página web, en realidad están trabajando simultáneamente varios protocolos especializados.

### 9. Diferencias entre protocolo, servicio y aplicación
Es frecuente confundir estos conceptos.

#### 9.1. Protocolo
Define las reglas de comunicación. Ejemplo:

- TCP.
- IP.
- HTTP.

#### 9.2. Servicio
Es la funcionalidad que ofrece un equipo a otros dispositivos de la red. Ejemplos:

- Servicio web.
- Servicio DNS.
- Servicio DHCP.
- Servicio de correo electrónico.

#### 9.3. Aplicación
Es el programa utilizado por el usuario. Ejemplos:

- Google Chrome.
- Mozilla Firefox.
- Microsoft Outlook.
- FileZilla.

Las aplicaciones utilizan protocolos para acceder a los distintos servicios de red.

### 10. Caso práctico
Una empresa va a implantar una nueva plataforma de trabajo colaborativo accesible desde Internet.

Los empleados deberán consultar documentos mediante un navegador web, acceder remotamente a los servidores para realizar tareas de administración y recibir automáticamente una dirección IP al conectar sus equipos a la red corporativa.
El administrador de sistemas debe seleccionar los protocolos de comunicación adecuados para cada uno de estos servicios y justificar su elección teniendo en cuenta la función que desempeña cada protocolo dentro de la arquitectura de red.

> **Analiza la situación e identifica qué protocolos serían necesarios para prestar cada uno de los servicios descritos, explicando el papel que desempeña cada uno durante la comunicación.**