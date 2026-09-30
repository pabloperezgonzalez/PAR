---
title: 📡 UP2.9. Monitorización de redes mediante SNMP - CE2.i)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| i) Se ha monitorizado la red mediante aplicaciones basadas en el protocolo SNMP. | Práctico |  10 % | 

### 1. Introducción
En cualquier red informática es fundamental conocer el estado de los dispositivos que la componen para garantizar su correcto funcionamiento. Una red puede sufrir problemas de rendimiento, fallos de hardware, saturación del tráfico o interrupciones del servicio que, si no se detectan a tiempo, pueden afectar al trabajo de los usuarios.

La **monitorización de redes** consiste en supervisar continuamente el funcionamiento de los dispositivos y servicios de una infraestructura de comunicaciones. Gracias a esta supervisión es posible detectar incidencias, analizar el rendimiento de la red y actuar antes de que un problema provoque una interrupción del servicio.

Uno de los protocolos más utilizados para realizar esta tarea es **SNMP (Simple Network Management Protocol)**, presente en la mayoría de routers, switches, servidores, impresoras de red y otros dispositivos de comunicaciones.

### 2. ¿Qué es la monitorización de una red?
La **monitorización de redes** es el proceso de recopilar información sobre el estado y funcionamiento de los dispositivos conectados a una red. Su objetivo es:

- Detectar averías.
- Supervisar el rendimiento.
- Analizar el tráfico de red.
- Comprobar la disponibilidad de los equipos.
- Anticiparse a posibles fallos.

### 3. ¿Qué es SNMP?
**SNMP (Simple Network Management Protocol)** es un protocolo de administración de redes que permite obtener información sobre el estado de los dispositivos conectados. Mediante SNMP es posible consultar datos como:

- Estado del dispositivo.
- Uso de la CPU.
- Memoria utilizada.
- Tráfico de las interfaces de red.
- Temperatura del equipo.
- Estado de los puertos.
- Tiempo de funcionamiento (*uptime*).

SNMP se ha convertido en uno de los protocolos más utilizados para la supervisión de infraestructuras de red.

### 4. Objetivos de SNMP
SNMP permite:

- Supervisar dispositivos de red.
- Detectar incidencias automáticamente.
- Obtener estadísticas de funcionamiento.
- Recibir avisos cuando ocurre un problema.
- Facilitar el mantenimiento preventivo.

### 5. Componentes de SNMP
El funcionamiento de SNMP se basa en tres elementos principales.

#### 5.1. Gestor (Manager)
Es el equipo que supervisa la red. Normalmente se trata de un servidor que ejecuta una aplicación de monitorización. Su función consiste en:

- Solicitar información.
- Recibir respuestas.
- Mostrar gráficos e informes.
- Generar alertas.

#### 5.2. Agente (Agent)
Es un programa instalado en cada dispositivo que responde a las consultas del gestor. Los agentes pueden encontrarse en:

- Routers.
- Switches.
- Servidores.
- Impresoras de red.
- Puntos de acceso.
- Sistemas operativos.

Su misión es proporcionar información sobre el dispositivo.

#### 5.3. Dispositivo gestionado
Es el equipo que incorpora un agente SNMP. Ejemplos:

- Router.
- Switch.
- Servidor.
- Cámara IP.
- NAS.
- Impresora.

### 6. Funcionamiento de SNMP
El proceso de monitorización sigue una secuencia sencilla.

```text
Gestor SNMP

       │

Solicita información

       │

Agente SNMP

       │

Consulta el dispositivo

       │

Envía la respuesta

       │

Gestor muestra resultados
```

### 7. La MIB (Management Information Base)
Toda la información que puede consultar SNMP se encuentra organizada en una base de datos denominada **MIB (Management Information Base)**. La MIB contiene miles de variables organizadas jerárquicamente. Cada variable recibe un identificador denominado **OID (Object Identifier)**. Ejemplos de información disponible:

- Nombre del dispositivo.
- Tiempo de funcionamiento.
- Interfaces de red.
- Velocidad de los enlaces.
- Tráfico transmitido.
- Uso del procesador.

### 8. Versiones de SNMP
Actualmente existen tres versiones principales.

| Versión | Características |
|----------|-----------------|
| **SNMPv1** | Primera versión. Seguridad limitada. |
| **SNMPv2c** | Mayor rendimiento. Sigue utilizando comunidades como mecanismo de autenticación. |
| **SNMPv3** | Añade autenticación, cifrado y mayor seguridad. Es la versión recomendada. |

En redes profesionales se recomienda utilizar **SNMPv3**, ya que protege la información intercambiada.

### 9. Información que puede monitorizarse
Mediante SNMP es posible conocer numerosos parámetros. Entre los más habituales destacan:

- Estado de los dispositivos.
- Interfaces activas.
- Velocidad de los enlaces.
- Ancho de banda utilizado.
- Errores de transmisión.
- Consumo de CPU.
- Memoria utilizada.
- Temperatura.
- Espacio libre en disco.
- Tiempo de funcionamiento.

### 10. Alertas SNMP
Además de responder a consultas, SNMP puede enviar **notificaciones automáticas** cuando ocurre un determinado evento. Estas notificaciones reciben el nombre de **Traps**. Ejemplos:

- Un switch deja de funcionar.
- Se desconecta un puerto.
- Se supera un determinado uso de CPU.
- Un servidor pierde conectividad.

### 11. Aplicaciones de monitorización
Existen numerosas aplicaciones compatibles con SNMP.

#### 11.1. Zabbix
Es una de las herramientas de monitorización más utilizadas, de código abierto ampliamente utilizada en empresas. Permite:

- Supervisar equipos.
- Crear gráficos.
- Configurar alertas.
- Monitorizar servidores y redes.

#### 11.2. PRTG Network Monitor
Aplicación comercial muy utilizada en pequeñas y medianas empresas. Características:

- Configuración sencilla.
- Paneles gráficos.
- Alertas automáticas.
- Monitorización mediante sensores.

#### 11.3. Nagios
Una de las soluciones más conocidas para la supervisión de infraestructuras. Permite monitorizar:

- Redes.
- Servidores.
- Servicios.
- Aplicaciones.

#### 11.4. Cacti
Especializada en representar gráficamente el uso del ancho de banda mediante SNMP. Resulta muy útil para analizar el rendimiento de la red.

### 12. Ventajas de la monitorización
La utilización de herramientas SNMP aporta numerosas ventajas.

- Detecta incidencias rápidamente.
- Reduce los tiempos de inactividad.
- Facilita el mantenimiento preventivo.
- Permite analizar el rendimiento.
- Ayuda a planificar ampliaciones.
- Mejora la disponibilidad de los servicios.

### 13. Limitaciones de SNMP
Aunque es un protocolo muy utilizado, presenta algunas limitaciones.

- No corrige automáticamente los problemas.
- Depende de que los dispositivos soporten SNMP.
- SNMPv1 y SNMPv2 ofrecen poca seguridad.
- Es necesario configurar correctamente los agentes.

Por este motivo, actualmente se recomienda utilizar **SNMPv3** siempre que sea posible.

### 14. Actividad UP2.9. Monitorización de redes mediante SNMP - CE2.i)
A partir de la red de la pequeña empresa creada en la actividad del **criterio CE2.h)**, utiliza las herramientas de **Cisco Packet Tracer** para monitorizar su funcionamiento, analizar el tráfico y consultar el estado de los dispositivos de red.

#### Paso 1. Comprobación del estado de los dispositivos
Abre el archivo de Packet Tracer realizado en la actividad anterior. En el router y en los switches, utiliza la CLI para consultar el estado de sus interfaces. Ejecuta:

```bash
show ip interface brief
```

Completa una tabla como la siguiente y responde a las siguientes preguntas:

| Dispositivo | Interfaz | Dirección IP | Estado | Protocolo |
| :---------- | :------- | :----------- | :----- | :-------- |
| R1          |          |              |        |           |
| SWC         |          |              |        |           |
| SW-01       |          |              |        |           |
| SW-02       |          |              |        |           |

1. ¿Qué significa que una interfaz aparezca como `up`?
2. ¿Qué diferencia hay entre el estado de la interfaz y el estado del protocolo?
3. ¿Hay alguna interfaz que esté desactivada?

#### Paso 2. Monitorización de las interfaces
En el router, utiliza:

```bash
show interfaces
```

Selecciona al menos **dos interfaces** y registra la información relacionada con el tráfico. Presta atención a datos como:

* Paquetes recibidos.
* Paquetes enviados.
* Bytes recibidos.
* Bytes enviados.
* Errores.
* Paquetes descartados.

Realiza una pequeña tabla y responde a la siguiente pregunta:

| Dispositivo | Interfaz | Paquetes recibidos | Paquetes enviados | Errores |
| :---------- | :------- | -----------------: | ----------------: | ------: |
| R1          |          |                    |                   |         |

4. Si realizas un `ping` entre dos dispositivos de la red y vuelves a consultar las estadísticas. ¿Qué cambios observas después de generar tráfico con este comando?

#### Paso 3. Monitorización de la tabla MAC
En uno de los switches ejecuta:

```bash
show mac address-table
```

Identifica las direcciones MAC que el switch ha aprendido y responde las siguientes preguntas:

| Dirección MAC | VLAN | Puerto |
| :------------ | :--: | :----: |
|               |      |        |
|               |      |        |
|               |      |        |

5. ¿Qué información proporciona la tabla MAC?
6. ¿Cómo sabe el switch por qué puerto se encuentra cada dispositivo?
7. ¿Qué relación existe entre una dirección MAC y un puerto del switch?

#### Paso 4. Analizar el tráfico mediante Simulation Mode
Activa el modo:

**Simulation**

Realiza un `ping` entre dos equipos pertenecientes a **redes diferentes** de la empresa. Observa el recorrido de los paquetes. Debes identificar:

* Dispositivo origen.
* Dispositivo destino.
* Protocolos utilizados.
* Dispositivos por los que pasa el tráfico.
* Resultado de la comunicación.

Registra los resultados, realizando una captura de pantalla del recorrido de los paquetes:

| Origen | Destino | Protocolo | Dispositivos intermedios | Resultado |
| :----- | :------ | :-------- | :----------------------- | :-------- |
|        |         |           |                          |           |

#### Paso 5. Generar y analizar tráfico
Realiza las siguientes pruebas:

##### Prueba 1
Realiza un `ping` entre dos equipos de la **misma red**.

##### Prueba 2
Realiza un `ping` entre dos equipos de **redes diferentes**.

##### Prueba 3
Realiza un `ping` entre un equipo y uno de los servidores.

Para cada prueba utiliza **Simulation Mode** y observa qué ocurre.

| Prueba | Origen | Destino | ¿Hay comunicación? | Observaciones |
| :----: | :----- | :------ | :----------------: | :------------ |
|    1   |        |         |                    |               |
|    2   |        |         |                    |               |
|    3   |        |         |                    |               |

#### Paso 6. Preguntas finales

1. ¿Qué herramientas de Packet Tracer has utilizado para monitorizar la red?
2. ¿Qué información puede obtenerse mediante `show ip interface brief`?
3. ¿Qué información proporciona `show interfaces`?
4. ¿Qué información proporciona `show mac address-table`?
5. ¿Qué ventajas tiene observar los paquetes mediante **Simulation Mode**?
6. ¿Qué problemas de una red podrían detectarse mediante estas herramientas?

#### Paso 8. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules. El documento debe contener todas las capturas de pantalla, tablas y preguntas respondidas que se requieren en la actividad.