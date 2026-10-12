---
title: 🔌 UP3.2. Interpretación de la información proporcionada por los LED del conmutador - CE3.b)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| b) Se ha interpretado la información que proporcionan los «leds» del conmutador | Teórico |  % | 

### 1. Introducción
Los **conmutadores de red (switches)** disponen de diferentes indicadores luminosos o **LED** que permiten conocer rápidamente su estado y el de los puertos de red. Estos indicadores proporcionan información sobre aspectos como:

- Alimentación del dispositivo.
- Estado de los puertos.
- Existencia de un enlace.
- Actividad de la red.
- Velocidad de conexión.
- Posibles problemas o estados especiales.

La interpretación de estos indicadores constituye una de las primeras herramientas de diagnóstico que puede utilizar un administrador de redes.

> **Importante:** el significado exacto de cada LED puede variar según el fabricante y el modelo del switch. Por ello, siempre es recomendable consultar la documentación del dispositivo.

### 2. ¿Qué es un LED de un conmutador?
Un **LED (Light Emitting Diode)** es un indicador luminoso que muestra información sobre el estado del dispositivo. Los switches suelen incorporar LED:

- Generales, relacionados con el propio equipo.
- Asociados a cada puerto Ethernet.
- Específicos para indicar velocidad o actividad.

Por ejemplo:

```text
┌─────────────────────────────────────┐
│              SWITCH                 │
│                                     │
│ POWER  🟢                           │
│                                     │
│  1 🟢   2 🟢   3 🟠   4 ⚫          │
│                                     │
└─────────────────────────────────────┘
```

Cada indicador debe interpretarse según las instrucciones del fabricante.


### 3. LED de alimentación
Uno de los indicadores más importantes es el LED que informa sobre la **alimentación del switch**. Puede aparecer identificado como "POWER" o "PWR. Generalmente:

- **LED encendido 🟢:** el switch está recibiendo alimentación.
- **LED apagado ⚫:** el dispositivo no está recibiendo alimentación o existe algún problema.
- **LED parpadeando 🟢 ↔ ⚫:** en algunos modelos puede indicar un proceso de arranque o un estado determinado.

### 4. LED de los puertos
Cada puerto Ethernet puede disponer de uno o varios LED. Estos indicadores permiten conocer si existe un enlace entre el switch y el dispositivo conectado.

Ejemplo:

```text
Puerto 1 → 🟢
Puerto 2 → 🟢
Puerto 3 → ⚫
Puerto 4 → 🟢
```

Podríamos interpretar inicialmente que los puertos 1, 2 y 4 tienen un enlace activo, mientras que el puerto 3 no tiene un enlace detectado.

### 5. LED de enlace (Link)
El indicador **Link** permite conocer si existe una conexión física entre el puerto del switch y el dispositivo conectado. Por ejemplo:

```text
PC ───────────── Switch
                  │
                  ▼
               LINK 🟢
```

Si está apagado, debemos comprobar:

- Cable.
- Conectores.
- Puerto del switch.
- Tarjeta de red del dispositivo.
- Estado del dispositivo conectado.

### 6. LED de actividad (Activity)
Algunos switches utilizan el mismo LED para indicar también la actividad de la red. Cuando existe transmisión de datos, el LED puede **parpadear**.

Ejemplo:

```text
PC ───────── Switch
                │
                ▼
             🟢 ↔ ⚫
```

El parpadeo indica normalmente que se están transmitiendo o recibiendo datos. Por tanto:

```text
LED fijo
   ↓
Enlace establecido

LED parpadeando
   ↓
Enlace + actividad
```

### 7. LED de velocidad
Algunos switches disponen de indicadores que permiten conocer la **velocidad negociada** del puerto. Por ejemplo, un switch podría utilizar:

```text
🟢 → 1 Gbps
🟠 → 100 Mbps
```

Sin embargo, otro fabricante puede utilizar otros colores o combinaciones. Por este motivo:

> **No debemos asociar un color concreto a una velocidad sin consultar previamente la documentación del switch.**

### 8. LED de estado de los puertos
Dependiendo del dispositivo, los LED pueden proporcionar información adicional. Por ejemplo:

| Estado del LED | Posible significado |
|----------------|---------------------|
| Apagado | Sin enlace o puerto deshabilitado |
| Encendido | Enlace activo |
| Parpadeando | Actividad de red |
| Color diferente | Puede indicar otra velocidad o estado |

### 9. Modos de funcionamiento de los LED
Los indicadores pueden utilizar diferentes estados.

#### 9.1. LED apagado
Puede significar:

- No existe enlace.
- El dispositivo está desconectado.
- El puerto está deshabilitado.
- El switch está apagado.

No debemos asumir inmediatamente que existe una avería.

#### 9.2. LED encendido de forma fija
Normalmente indica:

- Enlace establecido.
- Dispositivo conectado.
- Estado operativo.

#### 9.3. LED parpadeando
Puede indicar:

- Transmisión de datos.
- Recepción de datos.
- Actividad del puerto.
- Algún proceso interno.

#### 9.4. Cambio de color
En determinados modelos, los colores permiten distinguir diferentes estados. Por ejemplo:

```text
Verde  → funcionamiento normal
Ámbar  → estado diferente o velocidad inferior
Rojo   → posible problema
```

Sin embargo, **estos significados no son universales**.

### 10. Diagnóstico utilizando los LED
Los LED permiten realizar una primera aproximación al diagnóstico de una incidencia. Por ejemplo:

```text
PC ─────── Switch
             │
             └── LED apagado
```

Antes de utilizar herramientas como `ping`, podemos realizar las siguientes comprobaciones:

1. ¿El switch está encendido?
2. ¿El cable está correctamente conectado?
3. ¿El LED del puerto está encendido?
4. ¿La tarjeta de red del ordenador está activa?
5. ¿El puerto del switch está habilitado?
6. ¿Existe algún problema con el cable?

### 11. Ejemplo de diagnóstico
Un ordenador conectado al puerto 5 de un switch no tiene conexión de red. Observamos:

```text
POWER → 🟢
Puerto 5 → ⚫
```

El switch está encendido, pero no detecta un enlace en el puerto 5. El administrador puede seguir esta secuencia:

```text
Comprobar cable
      ↓
Comprobar conectores
      ↓
Comprobar tarjeta de red
      ↓
Probar otro cable
      ↓
Probar otro puerto
      ↓
Comprobar configuración del switch
```

De esta forma se puede localizar progresivamente el origen del problema.

### 12. Los LED no sustituyen al diagnóstico por software
Los LED son muy útiles, pero proporcionan una información limitada. Por ejemplo, un LED puede indicar:

```text
🟢 Enlace activo
```

pero esto **no significa necesariamente que exista conectividad IP**. Podemos tener:

```text
PC ─────── Switch
     🟢
```

y, sin embargo, que el equipo tenga una configuración IP incorrecta. Por eso debemos diferenciar:

```text
LED
 ↓
Conectividad física

IP / ping
 ↓
Conectividad lógica
```

### 13. Relación con el modelo OSI
Los LED del switch proporcionan principalmente información relacionada con los niveles más bajos de la comunicación. Podemos simplificarlo de la siguiente manera:

```text
Aplicación
Presentación
Sesión
Transporte
Red
Enlace de datos   ← Switch
Física            ← Cable / señal / enlace
```

Los LED permiten comprobar principalmente aspectos relacionados con la **capa física** y, dependiendo del modelo, determinados estados de la interfaz de red.

### 14. Interpretación de un escenario completo
Supongamos que tenemos:

```text
          Switch

Puerto 1 → 🟢 ↔ ⚫
Puerto 2 → 🟢
Puerto 3 → ⚫
Puerto 4 → 🟢 ↔ ⚫
```

Una posible interpretación sería:

- **Puerto 1:** enlace activo y actividad.
- **Puerto 2:** enlace activo, sin actividad en ese instante.
- **Puerto 3:** no se detecta enlace.
- **Puerto 4:** enlace activo y actividad.

El administrador podría utilizar esta información para localizar rápidamente qué equipos tienen problemas de conexión física.

### 15. Buenas prácticas
Al interpretar los LED de un switch es recomendable:

- Consultar el manual del fabricante.
- Conocer el significado de cada color.
- Diferenciar LED fijo y parpadeante.
- Comprobar primero la alimentación.
- Revisar los LED de los puertos.
- Comprobar cables y conectores.
- No confundir enlace físico con conectividad IP.
- Complementar la información de los LED con herramientas de diagnóstico.

### 16. Caso práctico
Supongamos que tenemos:

```text
          Switch

Puerto 1 → 🟢 ↔ ⚫
Puerto 2 → 🟢
Puerto 3 → ⚫
Puerto 4 → 🟢 ↔ ⚫
Puerto 5 → 🟢 ↔ ⚫
Puerto 6 → ⚫
Puerto 7 → 🟢
Puerto 8 → 🟢
```

¿Qué pasos debemos seguir y qué podemos interpretar de cada puerto del switch?