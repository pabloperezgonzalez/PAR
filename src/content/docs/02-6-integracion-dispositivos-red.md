---
title: 📡 UP2.6. Integración de dispositivos en redes cableadas e inalámbricas - CE2.f)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| f) Se han integrado dispositivos en redes cableadas e inalámbricas. | Práctico | 10 % | 

### 1. Introducción
Una red de datos no está formada únicamente por ordenadores. En la actualidad, una infraestructura de red integra una gran variedad de dispositivos que deben comunicarse entre sí de forma eficiente y segura. Ordenadores, servidores, impresoras, teléfonos IP, cámaras de videovigilancia, puntos de acceso inalámbricos, dispositivos móviles o equipos IoT forman parte de las redes actuales. Todos ellos deben configurarse correctamente para garantizar su funcionamiento y permitir el acceso a los recursos compartidos.

En este criterio aprenderemos cómo integrar diferentes dispositivos en redes cableadas e inalámbricas, identificando los elementos necesarios para establecer la comunicación y comprobando que la integración se realiza correctamente.

### 2. ¿Qué significa integrar un dispositivo en una red?
**Integrar un dispositivo en una red** consiste en conectarlo físicamente o de forma inalámbrica, configurarlo correctamente y verificar que puede comunicarse con el resto de equipos. Este proceso implica:

- Conectar el dispositivo al medio de transmisión.
- Configurar sus parámetros de red.
- Comprobar la conectividad.
- Verificar el acceso a los recursos compartidos.

La integración debe realizarse siguiendo la planificación establecida por el administrador de la red.

### 3. Tipos de dispositivos que pueden integrarse
En una red local pueden encontrarse numerosos dispositivos. Los más habituales son:

| Dispositivo | Función |
|--------------|---------|
| Ordenador | Puesto de trabajo del usuario. |
| Servidor | Proporciona servicios a la red. |
| Switch | Interconecta equipos dentro de una LAN. |
| Router | Comunica diferentes redes. |
| Punto de acceso (AP) | Permite el acceso inalámbrico. |
| Impresora de red | Servicio de impresión compartido. |
| Cámara IP | Videovigilancia. |
| Teléfono IP | Comunicaciones VoIP. |
| NAS | Almacenamiento compartido. |
| Dispositivos IoT | Sensores, actuadores y domótica. |

Todos estos dispositivos deben configurarse para poder comunicarse correctamente.

### 4. Requisitos para integrar un dispositivo
Antes de conectar un equipo a una red es necesario comprobar varios aspectos.

#### 4.1. Compatibilidad física
El dispositivo debe disponer de un adaptador de red compatible. Por ejemplo:

- Ethernet RJ-45.
- Wi-Fi.
- Fibra óptica (en algunos equipos).

#### 4.2. Compatibilidad lógica
Debe utilizar el mismo protocolo de comunicación que el resto de la red. En la mayoría de redes actuales:

- Ethernet.
- IPv4.
- TCP/IP.

#### 4.3. Configuración IP
Todo dispositivo necesita disponer de:

- Dirección IP.
- Máscara de subred.
- Puerta de enlace (si accede a otras redes).
- Servidor DNS (si necesita resolver nombres).

### 5. Integración en redes cableadas
Las redes cableadas continúan siendo la opción preferida en entornos profesionales debido a su estabilidad y rendimiento. El proceso de integración suele seguir esta secuencia.

```text
                    Conectar cable Ethernet
                            │
                            ▼
                    Comprobar LED del puerto
                            │
                            ▼
                    Configurar dirección IP
                            │
                            ▼
                    Comprobar conectividad
                            │
                            ▼
                    Acceder a recursos compartidos
```

### 6. Conexión física
El dispositivo se conecta mediante un cable Ethernet a un switch.

```text
PC ───────── RJ-45 ───────── Switch
```

Una vez conectado, deben encenderse los **indicadores luminosos (LED) del puerto**. Estos LED indican normalmente:

- Existencia de enlace.
- Actividad de la red.
- Velocidad negociada.

### 7. Configuración del adaptador
Una vez establecida la conexión física se configura el adaptador de red. Puede utilizar:

- DHCP.
- Dirección IP estática.

La elección dependerá del tipo de dispositivo.

### 8. Integración en redes inalámbricas
En una red Wi-Fi el proceso es similar, aunque incorpora algunos pasos adicionales.

```text
                    Activar adaptador Wi-Fi
                            │
                            ▼
                    Buscar redes disponibles
                            │
                            ▼
                    Seleccionar SSID
                            │
                            ▼
                    Introducir contraseña
                            │
                            ▼
                    Obtener dirección IP
                            │
                            ▼
                    Comprobar conectividad
```

### 9. Parámetros de una conexión Wi-Fi
Para conectarse correctamente es necesario conocer:

- SSID.
- Tipo de seguridad.
- Contraseña.
- Banda de frecuencia.
- Dirección IP (si es estática).

### 10. Integración de diferentes dispositivos
Cada dispositivo requiere una configuración específica.

#### 10.1. Ordenadores
Normalmente utilizan:

- DHCP.
- Nombre de equipo.
- DNS automático.

Son los dispositivos más sencillos de integrar.

#### 10.2. Servidores
Los servidores suelen utilizar:

- Dirección IP fija.
- Nombre permanente.
- Servicios de red configurados.

Es fundamental que su dirección IP no cambie.

#### 10.3. Impresoras de red
Habitualmente disponen de:

- Dirección IP estática.
- Interfaz web de administración.

Esto permite que todos los usuarios puedan acceder siempre a la misma dirección.

#### 10.4. Puntos de acceso inalámbricos
Los puntos de acceso deben configurarse con:

- Dirección IP.
- SSID.
- Canal.
- Seguridad WPA2 o WPA3.
- Contraseña.

Después permitirán la conexión de dispositivos inalámbricos.

#### 10.5. Cámaras IP
Las cámaras IP suelen configurarse con:

- Dirección IP fija.
- Máscara.
- Gateway.
- Credenciales de acceso.

Muchas utilizan alimentación mediante **PoE (Power over Ethernet)**.

#### 10.6. Teléfonos IP
Los teléfonos VoIP requieren:

- Dirección IP.
- Servidor SIP.
- Credenciales de usuario.

En muchas empresas también utilizan PoE.

### 11. Integración de dispositivos móviles
Los teléfonos inteligentes y tabletas se integran normalmente mediante Wi-Fi. El procedimiento consiste en:

- Seleccionar la red.
- Introducir la contraseña.
- Obtener una dirección IP mediante DHCP.

Posteriormente pueden acceder a:

- Internet.
- Impresoras.
- Recursos compartidos.
- Aplicaciones corporativas.

### 12. Comprobación de la integración
Una vez integrado el dispositivo deben realizarse varias comprobaciones. Las más habituales son:

- Comprobar la dirección IP.
- Realizar un ping a la puerta de enlace.
- Acceder a otros equipos.
- Acceder a Internet.
- Comprobar el acceso a recursos compartidos.

### 13. Herramientas de comprobación
Las herramientas más utilizadas son:

| Herramienta | Función |
|-------------|----------|
| `ping` | Comprueba la conectividad. |
| `ipconfig` / `ip addr` | Muestra la configuración IP. |
| `tracert` / `traceroute` | Analiza el recorrido de los paquetes. |
| `arp` | Consulta la tabla ARP. |
| Navegador web | Verifica el acceso a Internet. |

### 14. Problemas habituales
Durante la integración pueden aparecer diferentes incidencias.

| Problema | Posible causa |
|-----------|---------------|
| No hay enlace físico | Cable defectuoso o puerto dañado. |
| No obtiene dirección IP | Problema con el servidor DHCP. |
| No conecta al Wi-Fi | Contraseña incorrecta. |
| No accede a Internet | Gateway mal configurado. |
| No resuelve nombres | DNS incorrecto. |
| Conflicto IP | Dirección duplicada. |

La identificación rápida de estos problemas reduce considerablemente el tiempo de resolución de incidencias.

### 15. Buenas prácticas
Durante la integración de dispositivos es recomendable:

- Etiquetar todos los equipos.
- Mantener un inventario actualizado.
- Asignar nombres descriptivos.
- Reservar direcciones IP para servidores e impresoras.
- Utilizar WPA3 en redes inalámbricas.
- Cambiar las contraseñas predeterminadas.
- Documentar la configuración realizada.

### 16. Actividad UP2.6. Integración de dispositivos en redes cableadas e inalámbricas - CE2.f)
A partir de los dos ordenadores ya configurados en la actividad del **CE2.e)**, amplía la red incorporando un **conmutador (switch)** y conecta los equipos a él para formar una pequeña red cableada. El objetivo es **integrar correctamente los dispositivos y comprobar que los enlaces físicos se encuentran correctamente establecidos**.

> **Importante:** en esta actividad no se realizará ninguna prueba de conectividad entre los equipos.

#### Paso 1. Ampliar la topología
En Cisco Packet Tracer:

* Mantén los equipos `PC1` y `PC2` de la actividad anterior.
* Añade un **switch** a la topología.
* Conecta `PC1` al switch.
* Conecta `PC2` al switch.
* Utiliza las interfaces Ethernet correspondientes.

La topología deberá quedar similar a:

```text
PC1 ───────── Switch ───────── PC2
```

#### Paso 2. Comprobar las conexiones
Comprueba que:

* Cada PC está conectado a un puerto del switch.
* Los cables están conectados correctamente.
* Las interfaces utilizadas muestran que existe un enlace físico activo.

#### Paso 3. Identificar los dispositivos y puertos
Identifica en la topología:

* Los dos ordenadores.
* El switch.
* La interfaz de red utilizada en cada PC.
* El puerto del switch utilizado para cada conexión.

Completa:

| Dispositivo | Interfaz/puerto | Dispositivo conectado |
| :---------- | :-------------- | :-------------------- |
| PC1         |                 |                       |
| PC2         |                 |                       |

#### Paso 4. Comprobar la configuración IP
Sin modificar la configuración realizada en la actividad anterior, comprueba que los equipos mantienen sus direcciones:

| Equipo | Dirección IPv4  | Máscara         |
| :----- | :-------------- | :-------------- |
| PC1    | `192.168.10.10` | `255.255.255.0` |
| PC2    | `192.168.10.20` | `255.255.255.0` |

#### Paso 5. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules.