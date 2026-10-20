---
title: 🔌 UP3.10. Modificación de los parámetros que determinan la selección del puente raíz - CE3.j)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| j) Se han modificado los parámetros que determinan el proceso de selección del puente raíz. | Práctico | 15 % | 

### 1. Introducción
En una red con varios conmutadores, **Spanning Tree Protocol (STP)** necesita seleccionar un conmutador que actúe como **puente raíz o Root Bridge**. El Root Bridge sirve como referencia para que los demás switches calculen los mejores caminos dentro de la topología. Por ejemplo:

```text
              ┌─────────┐
              │  SW1    │
              │  ROOT   │
              └────┬────┘
                   │
             ┌─────┴─────┐
             │           │
         ┌───┴───┐   ┌───┴───┐
         │  SW2  │───│  SW3  │
         └───────┘   └───────┘
```

STP selecciona automáticamente el Root Bridge, pero el administrador de red puede **modificar determinados parámetros para controlar qué switch será elegido como raíz**. Esto es importante porque no siempre interesa que la elección se realice únicamente de forma automática.

### 2. ¿Por qué queremos elegir el Root Bridge?
En una red real, podemos tener varios switches:

```text
SW1
SW2
SW3
SW4
```

Todos podrían participar en STP, pero normalmente queremos que el Root Bridge sea un switch que tenga unas características adecuadas, por ejemplo:
- Estar situado en una posición central de la red.
- Tener enlaces de buena capacidad.
- Disponer de una alta disponibilidad.
- Ser un switch diseñado para desempeñar una función central.
- Facilitar una topología eficiente.

Por tanto:
> **El administrador puede modificar los parámetros de STP para controlar qué switch debe actuar como Root Bridge.**

### 3. ¿Cómo se selecciona el Root Bridge?
STP utiliza el **Bridge ID** para seleccionar el Root Bridge. De forma simplificada:

```text
Bridge ID
   │
   ├── Prioridad
   │
   └── Dirección MAC
```

El switch que tenga el **Bridge ID más bajo** será elegido como Root Bridge. Por tanto:

```text
Bridge ID más bajo
        ↓
    Root Bridge
```

La prioridad es el parámetro que normalmente utilizaremos para influir en esta elección.

### 4. La prioridad del switch
La **prioridad** es uno de los principales parámetros utilizados por STP para seleccionar el Root Bridge. Podemos imaginar tres switches:

```text
SW1 → prioridad 32768
SW2 → prioridad 32768
SW3 → prioridad 32768
```

Si todos tienen la misma prioridad, será necesario utilizar otro criterio para decidir cuál será el Root Bridge. En este caso interviene la dirección MAC.

### 5. Modificar la prioridad
Si queremos que un determinado switch tenga más posibilidades de convertirse en Root Bridge, podemos asignarle una **prioridad menor**. Por ejemplo:

```text
SW1 → 32768
SW2 → 24576
SW3 → 32768
```

El resultado sería:

```text
        SW2
       ROOT
      /    \
    SW1    SW3
```

porque SW2 tiene una prioridad inferior. La idea fundamental que debemos recordar es:
> **En STP, una prioridad numéricamente menor tiene preferencia en la elección del Root Bridge.**

### 6. Importante: menor prioridad = mayor preferencia
Este concepto puede resultar inicialmente poco intuitivo. No debemos pensar:

```text
Mayor prioridad
      ↓
Mejor candidato
```

En STP ocurre lo contrario:

```text
Menor prioridad
      ↓
Mejor candidato para Root Bridge
```

Por ejemplo:

| Switch | Prioridad | Preferencia |
|---|---:|---|
| SW1 | 32768 | Menor |
| SW2 | 24576 | Mayor |
| SW3 | 28672 | Intermedia |

En este ejemplo:

```text
SW2
 ↓
Mayor preferencia
 ↓
Root Bridge
```

### 7. La dirección MAC como criterio de desempate
Si dos switches tienen la misma prioridad, STP utiliza la dirección MAC como parte del proceso de selección. Por ejemplo:

```text
SW1
Prioridad: 32768
MAC: 0011.2233.4455

SW2
Prioridad: 32768
MAC: 0011.2233.4456
```

Como la prioridad es igual, se compara la MAC. La dirección MAC menor tendrá preferencia. Por tanto, podemos resumir el proceso de esta forma:

```text
¿Misma prioridad?
       │
       SÍ
       │
       ▼
Comparar dirección MAC
       │
       ▼
  MAC menor
       │
       ▼
   Root Bridge
```

Por este motivo, si queremos controlar de forma explícita qué switch será Root Bridge, es preferible **modificar la prioridad** en lugar de depender de la dirección MAC.

### 8. Bridge ID y selección del Root Bridge
Podemos resumir el proceso:

```text
             BRIDGE ID
                 │
        ┌────────┴────────┐
        │                 │
   Prioridad          Dirección MAC
        │                 │
        └────────┬────────┘
                 ▼
       Comparación entre
          los switches
                 │
                 ▼
        Bridge ID menor
                 │
                 ▼
          ROOT BRIDGE
```

La prioridad es, por tanto, el principal parámetro que utilizaremos para influir en la elección.

### 9. Comprobar el Root Bridge actual
Antes de modificar cualquier parámetro de STP debemos comprobar cuál es la situación actual. En un switch Cisco podemos utilizar:

```text
show spanning-tree
```

Por ejemplo:

```text
Switch# show spanning-tree
```

La salida mostrará información sobre:
- Root ID.
- Bridge ID.
- Prioridad.
- Dirección MAC.
- Roles de los puertos.
- Estados de los puertos.

### 10. Identificar el Root Bridge
Al ejecutar:

```text
show spanning-tree
```

podemos encontrar información similar a:

```text
Root ID
  Priority    32768
  Address     0011.2233.4455
```

Esto nos permite saber qué switch está actuando como Root Bridge. Podemos representarlo:

```text
             ROOT BRIDGE
                  │
                  ▼
                SW1
              /     \
             /       \
           SW2       SW3
```

---

### 11. Ejemplo práctico
Supongamos que tenemos tres switches:

```text
             SW1
            /   \
           /     \
         SW2─────SW3
```

Inicialmente:

```text
SW1 → prioridad 32768
SW2 → prioridad 32768
SW3 → prioridad 32768
```

En este caso, la elección dependerá también de la dirección MAC. Supongamos que STP selecciona:

```text
SW2 → Root Bridge
```

Pero el administrador considera que **SW1** es una ubicación más adecuada para actuar como raíz. Podemos modificar la prioridad de SW1.

#### 11.1. Modificar la prioridad para elegir el Root Bridge
La idea sería:

```text
Antes:

SW1 → 32768
SW2 → 32768
SW3 → 32768

Root → SW2
```

Después:

```text
SW1 → 24576
SW2 → 32768
SW3 → 32768

Root → SW1
```

El cambio de prioridad provoca que SW1 tenga preferencia en la elección.

#### 11.2. Configuración mediante Cisco IOS
En un switch Cisco podemos acceder al modo de configuración:

```text
Switch> enable
Switch# configure terminal
```

Después podemos seleccionar la VLAN correspondiente:

```text
Switch(config)# spanning-tree vlan 1
```

Y modificar la prioridad:

```text
Switch(config-vlan)# priority 24576
```

La sintaxis exacta puede variar según el modelo, el sistema operativo y el modo de STP utilizado. Por ello, en una práctica real siempre debemos comprobar la documentación y la sintaxis disponible en el dispositivo.

### 12. Actividad UP3.10. Modificación de los parámetros que determinan la selección del puente raíz - CE3.j)