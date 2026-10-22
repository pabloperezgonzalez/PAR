---
title: 🔌 UP3.9. Verificación del funcionamiento del Spanning Tree Protocol (STP) - CE3.i)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| i) Se ha verificado el funcionamiento del Spanning Tree Protocol en un conmutador. | Práctico | 10 % | 

### 1. Introducción
En una red con varios conmutadores es habitual disponer de **enlaces redundantes** para evitar que una única avería provoque la pérdida de conectividad. Por ejemplo:

```text
        ┌───────────┐
        │  Switch 1 │
        └───┬───┬───┘
            │   │
            │   │
        ┌───┴───┴───┐
        │  Switch 2 │
        └───────────┘
```

La existencia de dos enlaces entre los switches proporciona redundancia, pero también puede provocar un problema:
> **Los bucles de capa 2.**
Para evitar estos bucles se utiliza **Spanning Tree Protocol (STP)**.

### 1. ¿Qué problema resuelve STP?
Los switches trabajan principalmente en la **capa 2 del modelo OSI** y utilizan direcciones MAC para tomar decisiones sobre el envío de tramas. A diferencia de los routers, las tramas Ethernet no tienen un mecanismo equivalente al TTL de los paquetes IP que permita detener indefinidamente una trama que circula por un bucle. Por ello, un bucle de capa 2 puede provocar problemas importantes. Por ejemplo:

```text
       ┌─────────┐
       │ Switch1 │
       └───┬─┬───┘
           │ │
           │ │
       ┌───┴─┴───┐
       │ Switch2 │
       └─────────┘
```

Una trama puede circular continuamente entre ambos switches. Esto puede provocar:

- **Tormentas de broadcast**.
- Inestabilidad en las tablas MAC.
- Tráfico innecesario.
- Degradación del rendimiento.
- Pérdida de conectividad.

STP permite mantener la redundancia física pero **evitando que todos los enlaces redundantes estén activos simultáneamente para el reenvío de tramas**.

### 3. Idea fundamental de STP
La idea básica de STP es construir una topología lógica sin bucles. Podemos tener:

```text
Topología física:

       ┌─────────┐
       │ Switch1 │
       └──┬───┬──┘
          │   │
          │   │
       ┌──┴───┴──┐
       │ Switch2 │
       └─────────┘
```

Pero STP puede decidir que uno de los enlaces quede bloqueado:

```text
       ┌─────────┐
       │ Switch1 │
       └──┬───┬──┘
          │   X
          │   │
       ┌──┴───┴──┐
       │ Switch2 │
       └─────────┘
```

La conexión física continúa existiendo, pero el enlace bloqueado no se utiliza para el reenvío normal de tramas. Si el enlace activo falla:

```text
       ┌─────────┐
       │ Switch1 │
       └──┬───┬──┘
          │   │
          │   │
       ┌──┴───┴──┐
       │ Switch2 │
       └─────────┘
```

STP puede permitir que el enlace alternativo pase a utilizarse. De esta forma:
> **STP proporciona redundancia física evitando bucles lógicos.**

### 4. ¿Qué es un árbol de expansión?
STP construye una estructura lógica denominada **árbol de expansión** (*Spanning Tree*). La red puede tener muchos enlaces físicos:

```text
       Switch1
       /      \
      /        \
 Switch2──────Switch3
      \        /
       \      /
        Switch4
```

STP selecciona determinados caminos para formar una estructura sin bucles. De forma simplificada:

```text
       Switch1
       /      \
      /        \
 Switch2      Switch3
      \        /
       X      X
        \    /
        Switch4
```

Algunos enlaces pueden quedar bloqueados para evitar los bucles.

### 5. Conceptos fundamentales de STP
Para comprender el funcionamiento de STP debemos conocer varios conceptos:

#### 5.1. Root Bridge
El **Root Bridge** es el switch que STP selecciona como referencia para construir el árbol de expansión. Podemos representarlo:

```text
             ROOT BRIDGE
                 │
        ┌────────┴────────┐
        │                 │
     Switch2           Switch3
        │                 │
        └────────┬────────┘
                 │
              Switch4
```

Todos los demás switches calculan el mejor camino hacia el Root Bridge. Por tanto:
> **El Root Bridge es el punto de referencia de la topología STP.**

#### 5.2. Bridge ID
Para seleccionar el Root Bridge, STP utiliza un identificador denominado **Bridge ID**. De forma simplificada, el Bridge ID está relacionado con:

```text
Bridge ID
   │
   ├── Prioridad
   │
   └── Dirección MAC
```

En la elección del Root Bridge:
> **El switch con el Bridge ID más bajo es seleccionado como Root Bridge.**
La prioridad tiene un papel fundamental en esta elección. Si dos switches tienen la misma prioridad, la dirección MAC se utiliza como criterio de desempate.

#### 5.3. Root Port
Cada switch que **no es Root Bridge** selecciona un puerto que proporciona el mejor camino hacia el Root Bridge. Ese puerto se denomina: **Root Port (RP)**. Por ejemplo:

```text
             Root Bridge
                 │
                 │
              Switch2
                 │
             Root Port
```

Un switch no raíz normalmente tiene un Root Port. El Root Bridge no necesita seleccionar un Root Port porque él mismo es la raíz.

#### 5.4. Designated Port
STP también selecciona **Designated Ports (DP)**. El Designated Port es el puerto seleccionado para proporcionar el mejor camino hacia el Root Bridge en un determinado segmento. De forma simplificada:

```text
        Root Bridge
        │       │
        │       │
        ▼       ▼
      DP        DP
      │         │
   Switch2    Switch3
```

Los puertos designados participan en el reenvío de tráfico.

#### 5.5. Puerto bloqueado
Cuando existen varios caminos redundantes, STP puede determinar que uno de ellos no debe utilizarse para el reenvío normal. Por ejemplo:

```text
       Switch1
       /      \
      /        \
 Switch2──────Switch3
```

STP puede bloquear uno de los caminos:

```text
       Switch1
       /      \
      /        \
 Switch2────X─Switch3
```

Esto evita que exista un bucle. El puerto bloqueado puede volver a utilizarse si la topología cambia y STP determina que es necesario.

#### 5.5. Coste del camino
STP utiliza un **coste de camino** para determinar cuál es la mejor ruta hacia el Root Bridge. De forma simplificada:

```text
              Root
             /    \
         coste    coste
           10       20
          /          \
      Switch2      Switch3
```

El switch seleccionará normalmente el camino con menor coste. El coste está relacionado con las características de los enlaces. Por tanto:

```text
Menor coste
     ↓
Mejor camino hacia Root Bridge
```

#### 5.6. Estados de los puertos en STP
En el funcionamiento tradicional de **802.1D STP**, los puertos pueden pasar por diferentes estados:
- Blocking: El puerto no reenvía tramas de datos, pero participa en el proceso de STP.
- Listening: El switch participa en el cálculo de la topología, pero todavía no aprende direcciones MAC.
- Learning: El puerto comienza a aprender direcciones MAC, pero todavía no reenvía tráfico de usuario.
- Forwarding: El puerto puede aprender direcciones MAC y reenviar tramas.

### 6. STP y BPDUs
Los switches utilizan mensajes denominados **BPDU (Bridge Protocol Data Units)** para intercambiar información relacionada con STP. Estos mensajes permiten a los switches conocer información como:

- Qué switch consideran Root Bridge.
- Costes de los caminos.
- Identificadores de los switches.
- Información sobre la topología.

Podemos representarlo:

```text
Switch1
   │
   │ BPDU
   ▼
Switch2
   │
   │ BPDU
   ▼
Switch3
```

### 7. Verificar STP en un switch
Una de las tareas fundamentales de este criterio es aprender a **comprobar si STP está funcionando correctamente**. En equipos Cisco podemos utilizar:

```text
show spanning-tree
```

Este comando proporciona información sobre el funcionamiento de STP. Por ejemplo:

```text
Switch# show spanning-tree
```

#### 7.1. Información proporcionada por `show spanning-tree`
El comando puede mostrar información relacionada con:

- Root Bridge.
- Bridge ID.
- Prioridad.
- Dirección MAC.
- Costes.
- Root Port.
- Designated Ports.
- Estado de los puertos.
- VLAN.
- Temporizadores.

#### 7.2. Ejemplo simplificado
Supongamos que tenemos:

```text
Switch1
   │
   ├──────── Switch2
   │
   └──────── Switch3
```

Al ejecutar:

```text
show spanning-tree
```

podríamos encontrar información similar a:

```text
Root ID
  Priority    32768
  Address     0011.2233.4455

Bridge ID
  Priority    32768
  Address     0066.7788.9900

Interface        Role     State
Fa0/1            Root     FWD
Fa0/2            Desg     FWD
Fa0/3            Altn     BLK
```

#### 7.3. Interpretar Root ID y Bridge ID
Al ejecutar:

```text
show spanning-tree
```

podemos encontrar dos conceptos importantes:
- Root ID: Identifica al switch que el dispositivo considera actualmente como **Root Bridge**.
- Bridge ID: Identifica al propio switch.

Por ejemplo:

```text
Root ID
   └── Switch1

Bridge ID
   └── Switch2
```

Esto significa que:

```text
Switch1 → Root Bridge
Switch2 → Switch no raíz
```

#### 7.4. Identificar el Root Port
En la salida de:

```text
show spanning-tree
```

podemos localizar el puerto que aparece con el rol:

```text
Root
```

Por ejemplo:

```text
Interface    Role    State
Fa0/1        Root    FWD
```

Esto indica que:

```text
Fa0/1
  │
  └── Root Port
```

Es el puerto que proporciona el mejor camino hacia el Root Bridge.

#### 7.5. Identificar puertos Designated
Podemos encontrar información como:

```text
Interface    Role    State
Fa0/1        Root    FWD
Fa0/2        Desg    FWD
```

En este caso:

```text
Fa0/1 → Root Port
Fa0/2 → Designated Port
```

Ambos participan en el reenvío de tráfico.

#### 7.6. Identificar un puerto bloqueado
También podemos encontrar:

```text
Interface    Role    State
Fa0/3        Altn    BLK
```

Esto indica que el puerto tiene un papel alternativo y se encuentra bloqueado para evitar un bucle. Podemos representarlo:

```text
Switch1
   │
   │
 Switch2
   │
   X──── Switch3
        Fa0/3
```

El enlace físico existe, pero STP evita que se utilice para el reenvío normal.

### 8. ¿Cómo comprobar que STP funciona?
Podemos realizar una práctica sencilla con varios switches. Por ejemplo:

```text
          Switch1
         /       \
        /         \
    Switch2──────Switch3
```

Los tres switches forman un triángulo.Sin STP existiría un bucle. Después de conectar los switches podemos ejecutar:

```text
show spanning-tree
```

y comprobar:
1. Qué switch es el Root Bridge.
2. Qué puerto es Root Port en cada switch no raíz.
3. Qué puertos son Designated.
4. Si existe algún puerto bloqueado.
5. Qué coste tienen los caminos.

#### 8.1. Comprobar el Root Bridge
El primer paso de la práctica será comprobar qué switch ha sido elegido como Root Bridge. Ejecutamos:

```text
show spanning-tree
```

en los tres switches. Podemos obtener:

```text
Switch1 → Root
Switch2 → No root
Switch3 → No root
```

Por tanto:

```text
        Switch1
       ROOT BRIDGE
```

#### 8.2. Comprobar los Root Ports
En los switches que no son Root Bridge debemos identificar el Root Port. Por ejemplo:

```text
Switch2
Fa0/1 → Root Port

Switch3
Fa0/1 → Root Port
```

Podemos representarlo:

```text
          Switch1
          ROOT
         /    \
       RP      RP
       /        \
 Switch2       Switch3
```

#### 8.3. Comprobar el puerto bloqueado
En una topología triangular, uno de los enlaces puede quedar bloqueado. Por ejemplo:

```text
          Switch1
          ROOT
         /    \
        /      \
    Switch2────Switch3
              X
```

El puerto bloqueado evita que exista un camino circular activo. Para comprobarlo debemos revisar la información obtenida mediante:

```text
show spanning-tree
```

---

#### 8.4. ¿Qué ocurre si falla un enlace?
Una de las ventajas de STP es que proporciona **redundancia**. Supongamos:

```text
          Switch1
          ROOT
         /    \
        /      \
    Switch2────Switch3
              X
```

El enlace entre Switch2 y Switch3 está bloqueado. Si falla el enlace entre Switch1 y Switch3:

```text
          Switch1
          ROOT
         /
        /
    Switch2────Switch3
```

STP puede modificar la topología y permitir que el enlace que estaba bloqueado pase a utilizarse. De esta forma se recupera la conectividad.

### 9. Actividad UP3.9. Verificación del funcionamiento del Spanning Tree Protocol (STP) - CE3.i)
Partiendo de la red de la actividad del criterio C3.h), amplía la topología incorporando un tercer switch y conexiones redundantes. Utiliza Cisco Packet Tracer para comprobar cómo STP evita los bucles de capa 2, identificar el switch raíz y verificar qué puertos reenvían tráfico y cuáles quedan bloqueados.

#### Paso 1. Recuperar el escenario anterior
Abre el archivo de la actividad anterior finalizada. Conserva:
- `SW-01` y `SW-02`.
- Los dos PCs y los dos portátiles con sus nombres.
- Las direcciones IP configuradas.
- La configuración de seguridad de puertos de `SW-01`.
- El servidor TFTP, si forma parte de tu escenario.

Antes de continuar, comprueba que los dispositivos finales están conectados a sus switches y que la red funciona correctamente.

#### Paso 2. Ampliar la topología
Añade un tercer switch Cisco 2960 y llámalo `SW-03`. Conecta los tres switches formando un triángulo:

```text
                 ┌────────┐
                 │ SW-01  │
                 └───┬────┘
                    / \
                   /   \
                  /     \
          ┌───────┐───────┐
          │ SW-02 │       │
          └───┬───┘       │
              │        ┌──┴───┐
              └────────│ SW-03│
                       └──────┘
```

Conecta los switches mediante enlaces Ethernet. Cada enlace entre dos switches debe utilizar puertos distintos. La topología debe tener tres enlaces entre switches:
- `SW-01` ↔ `SW-02`
- `SW-02` ↔ `SW-03`
- `SW-03` ↔ `SW-01`

No elimines las conexiones existentes de los dispositivos finales.

**Importante:** los enlaces redundantes forman un bucle de capa 2. STP debe intervenir para evitar que todos los enlaces reenvíen tráfico simultáneamente.

#### Paso 3. Consultar el estado inicial de STP
Accede a la CLI de cada switch y ejecuta:

```text
enable
show spanning-tree
```

Si el comando no muestra la información esperada, prueba:

```text
show spanning-tree vlan 1
```

Registra los resultados de los tres switches.

| Switch | ¿Es el Root Bridge? | Root ID | Root Port | Puertos en forwarding | Puertos bloqueados |
|---|:---:|---|---|---|---|
| SW-01 | | | | | |
| SW-02 | | | | | |
| SW-03 | | | | | |

La elección del switch raíz depende del **Bridge ID**, formado por la prioridad y la dirección MAC del switch. Si todos tienen la misma prioridad, normalmente gana el que tenga la dirección MAC más baja.

#### Paso 4. Identificar el switch raíz
En cada switch, ejecuta:

```text
show spanning-tree
```

Busca la información del `Root ID` y del `Bridge ID`. Responde:
1. ¿Qué switch ha sido elegido Root Bridge?
2. ¿Qué información permite identificarlo?
3. ¿Coincide el Root ID de los switches no raíz con el Bridge ID del switch raíz?
4. ¿Qué función desempeña el Root Bridge en STP?

Realiza una captura de pantalla de la salida de comandos que justifique tu respuesta.

#### Paso 5. Identificar los roles y estados de los puertos
En cada switch, vuelve a ejecutar:

```text
show spanning-tree vlan 1
```

Identifica los roles y estados de los puertos. Recuerda:

- **Root Port:** mejor camino de un switch no raíz hacia el Root Bridge.
- **Designated Port:** puerto seleccionado para reenviar tráfico en un segmento.
- **Forwarding:** el puerto puede reenviar tramas.
- **Blocking/Alternate:** puerto que no reenvía tráfico de usuario porque STP evita el bucle.

Completa la tabla:

| Switch | Puerto | Conectado a | Rol STP | Estado STP |
|---|---|---|---|---|
| SW-01 | | | | |
| SW-01 | | | | |
| SW-02 | | | | |
| SW-02 | | | | |
| SW-03 | | | | |
| SW-03 | | | | |

Los nombres de los puertos y los estados exactos pueden variar según la elección del Root Bridge y la convergencia de STP.

#### Paso 6. Comprobar que STP evita el bucle
Abre el modo **Simulation** de Packet Tracer.
1. Genera tráfico entre dos dispositivos finales.
2. Observa cómo circulan las tramas por la red.
3. Comprueba que STP mantiene uno de los caminos redundantes sin reenviar tráfico de usuario.
4. Vuelve a la CLI y consulta el estado de los puertos mediante `show spanning-tree vlan 1`.

Responde:
1. ¿Por qué no deben reenviar tráfico todos los enlaces del triángulo al mismo tiempo?
2. ¿Qué problema podría producirse si STP no evitara el bucle?
3. ¿Cómo contribuye el puerto bloqueado o alternativo a prevenir ese problema?

Guarda una captura del modo Simulation y otra de la salida de STP.

#### Paso 7. Comprobar la recuperación ante un fallo
Con STP funcionando correctamente:
1. Identifica un enlace que forme parte del camino activo entre los switches.
2. Desconecta temporalmente ese enlace en Packet Tracer.
3. Espera a que STP recalcule la topología.
4. Consulta de nuevo `show spanning-tree vlan 1` en los switches afectados.
5. Comprueba si un enlace que estaba bloqueado pasa a reenviar tráfico.
6. Realiza un `ping` entre dos dispositivos finales para verificar si se recupera la comunicación.

Después, vuelve a conectar el enlace desconectado y espera a que STP converja.

**Importante:** durante la convergencia puede haber una interrupción temporal de la conectividad. No modifiques las prioridades de los switches ni fuerces la elección del Root Bridge; eso corresponde al criterio j).

#### Paso 8. Informe final
Elabora un breve informe que incluya:
- Topología inicial y ampliada.
- Switch elegido como Root Bridge.
- Tabla con los roles y estados de los puertos.
- Evidencias de los comandos `show spanning-tree`.
- Explicación de cómo STP evita el bucle.
- Resultado de la prueba de desconexión y recuperación del enlace.

#### Paso 9. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules. El documento debe contener todas las capturas de pantalla necesarias para demostrar que se ha realizado el procedimiento correctamente. Recordad incluir:
- Archivo `.pkt` con la topología de tres switches.
- Tabla de roles y estados STP.
- Capturas de las comprobaciones.
- Informe final.