---
title: 📡 UP2.8. Representación del mapa físico y lógico de la red - CE2.h)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| h) Se han utilizado aplicaciones para representar el mapa físico y lógico de una red. | Práctico |  15 % | 

### 1. Introducción
Las redes actuales pueden estar formadas por decenas o incluso cientos de dispositivos interconectados. Para facilitar su instalación, administración y mantenimiento es necesario disponer de una representación gráfica que muestre cómo están organizados los equipos y cómo se comunican entre sí. Los **mapas de red** permiten documentar la infraestructura, localizar incidencias y comprender el funcionamiento global de la red.

En este criterio aprenderemos a diferenciar los mapas físicos y lógicos, conoceremos las aplicaciones más utilizadas para su representación y estudiaremos las buenas prácticas para documentar adecuadamente una red.

### 2. ¿Qué es un mapa de red?
Un **mapa de red** es una representación gráfica de los dispositivos, conexiones y relaciones existentes dentro de una infraestructura de comunicaciones. Su objetivo es facilitar:

- La comprensión de la red.
- La planificación de ampliaciones.
- La resolución de incidencias.
- La documentación técnica.
- La administración de la infraestructura.

Existen dos tipos principales de mapas: **Mapa físico** y **mapa lógico.**

### 3. Mapa físico de una red
El **mapa físico** representa la disposición real de los dispositivos y las conexiones existentes. Es especialmente útil para tareas de instalación y mantenimiento. Muestra información como:

- Ubicación de equipos.
- Cableado.
- Armarios de comunicaciones.
- Switches.
- Routers.
- Puntos de acceso.
- Servidores.

<img
  src="/PAR/diagrams/mapa-fisico.png"
  alt="Mapa físico de una red"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

### 4. Mapa lógico de una red
El **mapa lógico** representa cómo se comunican los dispositivos independientemente de su ubicación física. Es fundamental para comprender el funcionamiento interno de la red. Muestra información como:

- Direcciones IP.
- Redes y subredes.
- VLAN.
- Rutas.
- Servicios.
- Relaciones entre dispositivos.

<img
  src="/PAR/diagrams/mapa-logico.png"
  alt="Mapa lógico de una red"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

### 5. Diferencias entre mapa físico y lógico

| Característica | Mapa físico | Mapa lógico |
|----------------|-------------|-------------|
| Representa ubicación real | Sí | No |
| Muestra cableado | Sí | No |
| Muestra direcciones IP | No | Sí |
| Representa subredes | No | Sí |
| Facilita instalaciones | Sí | Parcialmente |
| Facilita administración | Parcialmente | Sí |

Ambos tipos de mapas son complementarios.

### 6. Importancia de la documentación
Una red correctamente documentada permite:

- Localizar equipos rápidamente.
- Reducir tiempos de reparación.
- Facilitar ampliaciones.
- Compartir información entre administradores.
- Mejorar la seguridad.

La documentación es una tarea esencial en cualquier infraestructura profesional.

### 7. Información que debe incluir un mapa de red
Un buen mapa de red debería incluir:

- Nombre de los dispositivos.
- Tipo de equipo.
- Direcciones IP.
- Conexiones.
- Velocidad de los enlaces.
- Número de puerto.
- VLAN (si existen).
- Ubicación física.

### 8. Aplicaciones para representar redes
Existen numerosas herramientas para crear mapas de red. Algunas permiten diseñarlos manualmente y otras pueden generarlos automáticamente.

#### 8.1. Herramientas de diseño manual
##### Cisco Packet Tracer
Esta herramienta cuenta con dos entornos de trabajo diseñados específicamente para realizar diagramas físicos y lógicos. Aunque es una herramienta de simulación y no de documentación pura, es excelente para diseñar, estructurar y probar redes antes de implementarlas.

>💡 **Características:** Gratuito, simulación y verificación en tiempo real y configuración real de dispositivos (CLI).

##### Draw.io (diagrams.net)
Es una de las herramientas más utilizadas.

>💡 **Características:** Gratuita, funciona en navegador, gran cantidad de iconos de red y fácil exportación.

>👉 **Ejemplo de uso:** Diagramas de aulas, redes pequeñas y documentación técnica.

##### Microsoft Visio
Herramienta profesional para crear diagramas, muy utilizada en empresas.

>💡 **Características:** Integración con Microsoft Office, plantillas específicas para redes y diagramas avanzados.

##### LibreOffice Draw
Alternativa libre para crear esquemas y diagramas.

#### 8.2. Herramientas de diagramación mediante código
Actualmente existen herramientas que permiten generar diagramas a partir de texto.

##### D2
Permite crear diagramas escribiendo código sencillo. Es especialmente útil en proyectos de documentación técnica.

👉 **Ejemplo:**

```d2
PC1 -> Switch
PC2 -> Switch
Switch -> Router
Router -> Internet
```

>✅ **Ventajas:** Fácil mantenimiento, integración con GitHub y control de versiones.

##### Mermaid
También permite generar diagramas mediante texto.

👉 **Ejemplo:**

```mermaid
graph LR
PC --> Switch
Switch --> Router
Router --> Internet
```

#### 8.3. Herramientas de detección automática
Algunas aplicaciones pueden detectar automáticamente los dispositivos de una red.

##### Nmap
Permite descubrir equipos activos.

👉 **Ejemplo:**

```bash
nmap 192.168.1.0/24
```

Obtiene información sobre:

- Equipos activos.
- Servicios.
- Puertos abiertos.

##### Angry IP Scanner
Aplicación gráfica sencilla para detectar dispositivos.

##### Fing
Herramienta para análisis de redes. Puede utilizarse en ordenadores y dispositivos móviles.

### 9. Buenas prácticas
Para representar correctamente una red es recomendable:

- Utilizar símbolos estandarizados.
- Nombrar todos los dispositivos.
- Documentar direcciones IP.
- Actualizar los diagramas.
- Diferenciar claramente la parte física y lógica.
- Mantener versiones actualizadas.

### 10. Actividad UP2.8. Representación del mapa físico y lógico de la red - CE2.h)
Una pequeña empresa dispone de **6 redes diferentes**, correspondientes a distintos espacios o departamentos. Utilizando **Cisco Packet Tracer**, representa su **esquema físico y lógico**, indicando los dispositivos, sus conexiones, las direcciones IP y el espacio al que pertenece cada red. La representación debe ser clara y permitir identificar fácilmente **qué dispositivos hay, dónde están ubicados y a qué red pertenecen**.

#### Paso 1. Redes de la empresa
La empresa estará formada por las siguientes **6 redes**:

| Red   | Espacio           | Red IP            | Dispositivos |
| :---- | :---------------- | :---------------- | :----------- |
| Red 1 | Recepción         | `192.168.10.0/24` | 1 PC         |
| Red 2 | Administración    | `192.168.20.0/24` | 2 PCs        |
| Red 3 | Dirección         | `192.168.30.0/24` | 3 PCs        |
| Red 4 | Desarrollo        | `192.168.40.0/24` | 4 laptop     |
| Red 5 | Sala de reuniones | `192.168.50.0/24` | 1 PC         |
| Red 6 | Servidores        | `192.168.60.0/24` | 3 servidores |

Cada red tendrá su **propio switch (SW-XX)**, que se conectará a un **switch central (SWC)** ubicado en la sala de servidores. Además, toda la empresa utilizará solamente **1 router (R1)**.

#### Paso 2. Direccionamiento IP
Cada dispositivo deberá tener una dirección IP perteneciente a la red que corresponda a su espacio. Por ejemplo:

| Dispositivo  | Espacio        | Dirección IP    | Máscara         |
| :----------- | :------------- | :-------------- | :-------------- |
| PC-RECEPCION | Recepción      | `192.168.10.10` | `255.255.255.0` |
| PC-ADMIN-01  | Administración | `192.168.20.10` | `255.255.255.0` |
| PC-ADMIN-02  | Administración | `192.168.20.11` | `255.255.255.0` |
| ...          | ...            | ...             | ...             |

El resto de direcciones deberá ser asignado por el alumnado siguiendo el mismo criterio.

#### Paso 3. Representación física
En **Cisco Packet Tracer**, representa la distribución física de la empresa. Deberás:

1. Crear los espacios correspondientes a las 6 redes.
2. Colocar los dispositivos dentro del espacio al que pertenecen.
3. Añadir los switches y el router necesarios.
4. Conectar físicamente los dispositivos mediante los cables correspondientes.
5. Organizar la topología para que resulte clara y fácil de interpretar.
6. **Nombrar todos los dispositivos**.

#### Paso 4. Representación lógica
Sobre la misma topología, representa la estructura lógica de la red. Cada dispositivo deberá mostrar claramente:

* Nombre del dispositivo.
* Dirección IP.
* Máscara de subred.
* Red a la que pertenece.
* Espacio o departamento correspondiente.

Debes utilizar **etiquetas de texto** de Packet Tracer para identificar cada red.

Por ejemplo:

```text
RED 2 - ADMINISTRACIÓN
192.168.20.0/24

PC-ADMIN-01
192.168.20.10

PC-ADMIN-02
192.168.20.11
```
#### Paso 5. Cuestiones finales
Responde brevemente:

1. ¿Cuántas redes diferentes tiene la empresa?
2. ¿Cómo puedes identificar visualmente a qué red pertenece cada dispositivo?
3. ¿Por qué es importante nombrar correctamente los dispositivos?
4. ¿Qué diferencia existe entre el esquema físico y el esquema lógico?
5. ¿Qué información permite conocer el mapa lógico que no se aprecia directamente en el mapa físico?

#### Paso 6. Entrega
La entrega será individual a través de Aules, se entregará el Archivo `.pkt` de Cisco Packet Tracer y un documento, en formato PDF, que deberá contener:

* Captura del **esquema físico**.
* Captura del **esquema lógico**.
* Cuestiones finales respondidas.
* Tabla con todos los dispositivos y sus direcciones IP.

| Dispositivo | Espacio | Red | IP | Máscara |
| :---------- | :------ | :-- | :- | :------ |
|             |         |     |    |         |
|             |         |     |    |         |
|             |         |     |    |         |
|             |         |     |    |         |