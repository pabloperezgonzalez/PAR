---
title: 🌐 UP1.3. Elementos funcionales, físicos y lógicos de una red - CE1.g)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| g) Se han presentado y descrito los elementos funcionales, físicos y lógicos, de las redes de datos. | Teórico | 10 % | 

### 1. Introducción
Cuando hablamos de una red de datos solemos pensar en ordenadores conectados mediante cables o redes inalámbricas. Sin embargo, una red es mucho más que un conjunto de dispositivos unidos entre sí.

Para que una red funcione correctamente es necesario que intervengan **elementos físicos**, **elementos lógicos** y **elementos funcionales**, cada uno de ellos con una misión específica. Comprender estos tres tipos de elementos permitirá al administrador de redes diseñar, configurar y mantener infraestructuras de comunicaciones eficientes, seguras y escalables.

### 2. ¿Qué elementos forman una red?
Una red de datos puede entenderse como un sistema compuesto por tres grandes grupos de elementos:

- **Elementos físicos**, que corresponden al hardware.
- **Elementos lógicos**, que permiten identificar y organizar la comunicación.
- **Elementos funcionales**, que proporcionan los servicios necesarios para que la red pueda utilizarse.

Los tres trabajan conjuntamente para que la información pueda viajar desde un dispositivo hasta otro.

```text
                                       RED DE DATOS
                                            │
                            ┌───────────────┼───────────────┐
                            │               │               │
                        Elementos        Elementos       Elementos
                        físicos          lógicos       funcionales
                        (Hardware)    (Configuración)   (Servicios)
```

### 3. Elementos físicos
Los **elementos físicos** son todos aquellos componentes materiales que forman la infraestructura de la red. Sin ellos sería imposible establecer una comunicación entre los dispositivos.

#### 3.1. Equipos finales (Hosts)
Son los dispositivos que generan o reciben información. Ejemplos:

- Ordenadores personales.
- Portátiles.
- Smartphones.
- Tablets.
- Servidores.
- Impresoras de red.
- Cámaras IP.
- Dispositivos IoT.

Estos equipos reciben el nombre de **hosts** porque pueden actuar como origen o destino de una comunicación.

#### 3.2. Tarjetas de red (NIC)
La **Network Interface Card (NIC)** permite que un dispositivo pueda conectarse a una red. Puede ser:

- Ethernet.
- Wi-Fi.
- Fibra óptica.

Cada tarjeta dispone de una dirección física única denominada **dirección MAC**, que estudiaremos más adelante.

#### 3.3. Medios de transmisión
Son los elementos que transportan la información entre los dispositivos. Pueden ser:

##### Medios guiados

- Cable de par trenzado (UTP, STP).
- Fibra óptica.
- Cable coaxial.

##### Medios no guiados

- Wi-Fi.
- Bluetooth.
- Radio.
- Microondas.
- Redes móviles (4G, 5G).

#### 3.4. Dispositivos de interconexión
Permiten conectar diferentes equipos o segmentos de red. Algunos ejemplos son:

- Hub.
- Switch.
- Router.
- Punto de acceso (Access Point).
- Firewall.
- Gateway.

En el siguiente criterio de evaluación se estudiará en profundidad la función de cada uno de ellos.

#### 3.5. Armarios y elementos de infraestructura
En una red profesional también forman parte de la infraestructura física:

- Rack o armario de comunicaciones.
- Paneles de parcheo (Patch Panel).
- Latiguillos.
- Tomas de red.
- Canalizaciones.
- Sistemas de alimentación ininterrumpida (SAI).

Estos elementos facilitan la organización y el mantenimiento de la instalación.

### 4. Elementos lógicos
Los elementos físicos necesitan una serie de configuraciones que permitan identificar los dispositivos y dirigir correctamente la información. Estos componentes reciben el nombre de **elementos lógicos**.

#### 4.1. Dirección MAC
Cada tarjeta de red posee una dirección física única grabada por el fabricante. Ejemplo:

```text
00:1B:63:84:45:E6
```

##### Características:
- Identifica de forma única una interfaz de red.
- Trabaja en la capa de enlace del modelo OSI.
- No depende de la configuración del usuario.

#### 4.2. Dirección IP
Mientras que la dirección MAC identifica físicamente una tarjeta de red, la **dirección IP** identifica un dispositivo dentro de una red.

Ejemplo IPv4:

```text
192.168.1.25
```

Ejemplo IPv6:

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

Las direcciones IP permiten localizar el destino de una comunicación.

#### 4.3. Máscara de red
La máscara determina qué parte de una dirección IP identifica la red y cuál identifica al equipo. Ejemplo:

```text
255.255.255.0
```

Su función es permitir que un dispositivo sepa si el destino pertenece a su misma red o debe enviar el tráfico a un router.

#### 4.4. Puerta de enlace (Gateway)
Es la dirección IP del router que permite acceder a otras redes. Cuando un equipo desea comunicarse con un dispositivo situado fuera de su red local, envía la información a la puerta de enlace.

#### 4.5. Servidores DNS
Recordar una dirección IP resulta complicado. Los servidores **DNS (Domain Name System)** traducen nombres de dominio en direcciones IP. Ejemplo:

```text
www.google.es
      │
      ▼
142.250.177.14
```

Gracias al DNS podemos navegar utilizando nombres fáciles de recordar.

#### 4.6. Protocolos de comunicación
Los protocolos establecen las normas que deben seguir los dispositivos para comunicarse. Algunos de los más conocidos son:

- IP
- TCP
- UDP
- HTTP
- HTTPS
- FTP
- DHCP
- DNS

Cada protocolo desempeña una función específica dentro de la red.

#### 4.7. VLAN
Una **VLAN (Virtual Local Area Network)** permite dividir una red física en varias redes lógicas independientes. Gracias a las VLAN es posible mejorar:

- La seguridad.
- La organización.
- El rendimiento.

Su funcionamiento se estudiará en unidades posteriores.

### 5. Elementos funcionales
Los elementos funcionales son los encargados de proporcionar los servicios que utilizan los usuarios. Podemos entenderlos como las funciones que hacen útil una red.

#### 5.1. Compartición de recursos
Las redes permiten compartir recursos comunes como:

- Impresoras.
- Carpetas.
- Archivos.
- Escáneres.
- Almacenamiento.

De este modo se reduce el coste y se facilita el trabajo colaborativo.

#### 5.2. Comunicación
Uno de los principales objetivos de una red consiste en permitir la comunicación entre usuarios. Por ejemplo:

- Correo electrónico.
- Mensajería instantánea.
- Videoconferencias.
- Telefonía IP.

#### 5.3. Acceso a Internet
En la mayoría de organizaciones la red proporciona acceso a Internet mediante un router conectado al proveedor de servicios. Este acceso permite utilizar:

- Navegación web.
- Correo electrónico.
- Plataformas educativas.
- Servicios en la nube.

#### 5.4. Autenticación de usuarios
Las empresas necesitan controlar quién puede acceder a la red. Para ello utilizan sistemas de autenticación que permiten:

- Identificar usuarios.
- Verificar contraseñas.
- Asignar permisos.

#### 5.5. Servicios de red
Las redes ofrecen numerosos servicios, entre ellos:

| Servicio | Función |
|-----------|---------|
| DHCP | Asigna automáticamente direcciones IP. |
| DNS | Traduce nombres de dominio en direcciones IP. |
| FTP/SFTP | Transferencia de archivos. |
| HTTP/HTTPS | Acceso a páginas web. |
| NTP | Sincronización de fecha y hora. |
| LDAP o Active Directory | Gestión centralizada de usuarios. |

#### 5.6. Seguridad
Las redes modernas incorporan múltiples mecanismos de protección. Entre ellos destacan:

- Firewalls.
- Antivirus corporativos.
- Sistemas IDS/IPS.
- VPN.
- Cifrado de comunicaciones.

Su objetivo consiste en proteger la información frente a accesos no autorizados.

### 6. Relación entre los tres tipos de elementos
Todos los elementos de una red trabajan conjuntamente. Por ejemplo, cuando un alumno abre una página web ocurre lo siguiente:

1. El ordenador (elemento físico) genera una petición.
2. Utiliza su dirección IP y el protocolo HTTP (elementos lógicos).
3. El servidor DNS traduce el nombre de la página.
4. El switch y el router encaminan la información.
5. El servidor web responde ofreciendo el servicio solicitado (elemento funcional).

Ninguno de estos elementos sería suficiente por sí solo.

### 7. Actividad
Clasifica cada uno de los siguientes elementos como **físico**, **lógico** o **funcional**.

| Elemento | Tipo | Justificación |
|-----------|------|------|
| Dirección IP | | |
| Router | | |
| DNS | | |
| Cable UTP | | |
| Servidor de archivos | | |
| Dirección MAC | | |
| Wi-Fi | | |
| DHCP | | |
| Switch | | |
| VLAN | | |