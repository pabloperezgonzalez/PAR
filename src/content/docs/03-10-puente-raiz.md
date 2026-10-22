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
Partiendo de la topología de tres switches desarrollada en la actividad del criterio CE3.i), modifica los parámetros de prioridad de STP para controlar qué switch se convierte en Root Bridge. Comprueba los cambios en la topología, identifica los puertos afectados y verifica que la red continúa funcionando correctamente. El objetivo es comprender cómo se puede controlar la elección del switch raíz en una red con enlaces redundantes.

#### Paso 1. Recuperar el escenario anterior
Abre el archivo de la actividad anterior finalizada. Conserva todos los elementos de la actividad anterior:

- Los switches `SW-01`, `SW-02` y `SW-03`.
- Los dos PCs y los dos portátiles.
- El servidor TFTP, si forma parte de tu escenario.
- Los enlaces entre los switches formando un triángulo.
- Las direcciones IP y la configuración de seguridad de puertos.
- La configuración STP existente.

Comprueba que los tres switches están conectados y que STP funciona correctamente.

#### Paso 2. Analizar la elección actual del Root Bridge
Accede a la CLI de cada switch y ejecuta:

```text
enable
show spanning-tree vlan 1
```

Anota los datos que aparecen en `Root ID` y `Bridge ID`. Completa la tabla:

| Switch | Prioridad actual | Dirección MAC del Bridge ID | ¿Es Root Bridge? |
|---|---:|---|:---:|
| SW-01 | | | |
| SW-02 | | | |
| SW-03 | | | |

Responde:
1. ¿Qué switch es actualmente el Root Bridge?
2. ¿Qué prioridad tiene?
3. Si todos los switches tienen la misma prioridad, ¿qué otro dato interviene en la elección?
4. ¿Por qué no conviene dejar la elección del Root Bridge al azar en una red empresarial?

#### Paso 3. Comprender el parámetro de prioridad
STP utiliza el Bridge ID para elegir el switch raíz. Este identificador incluye la prioridad y la dirección MAC del switch, junto con la información de extensión de sistema que corresponda. En los switches Cisco compatibles, la prioridad de STP se configura en la interfaz de configuración global mediante el comando `spanning-tree vlan`. Para VLAN 1, una configuración habitual es:

```text
configure terminal
spanning-tree vlan 1 priority 4096
end
```

La prioridad STP tradicional utiliza valores en incrementos de 4096, desde 0 hasta 61440. **Cuanto menor es la prioridad, mayor es la preferencia para convertirse en Root Bridge.** También puede utilizarse el comando de conveniencia `spanning-tree vlan 1 root primary` en equipos compatibles, pero en esta actividad se utilizará la prioridad explícita para comprender el parámetro que controla la elección.

#### Paso 4. Convertir SW-02 en Root Bridge
Configura `SW-02` para que tenga una prioridad inferior a la de los otros switches. En la CLI de `SW-02`, ejecuta:

```text
enable
configure terminal
spanning-tree vlan 1 priority 4096
end
```

Comprueba el resultado:

```text
show spanning-tree vlan 1
```

A continuación, ejecuta el mismo comando en `SW-01` y `SW-03` para verificar el Root ID. Completa:

| Switch | Prioridad configurada | ¿Es Root Bridge? |
|---|---:|:---:|
| SW-01 | | |
| SW-02 | 4096 | |
| SW-03 | | |

Responde:
1. ¿Se ha convertido `SW-02` en Root Bridge?
2. ¿Cómo puedes comprobarlo en la salida del comando?
3. ¿Qué cambios observas en los roles de los puertos de los otros switches?

#### Paso 5. Convertir SW-03 en Root Bridge
Ahora modifica la prioridad para que `SW-03` tenga preferencia sobre los demás. En la CLI de `SW-03`, ejecuta:

```text
enable
configure terminal
spanning-tree vlan 1 priority 0
end
```

Consulta el estado STP en los tres switches:

```text
show spanning-tree vlan 1
```

Comprueba si `SW-03` se ha convertido en el nuevo Root Bridge. Completa:

| Switch | Prioridad configurada | ¿Es Root Bridge? |
|---|---:|:---:|
| SW-01 | | |
| SW-02 | 4096 | |
| SW-03 | 0 | |

Responde:
1. ¿Qué switch es ahora el Root Bridge?
2. ¿Por qué la prioridad 0 tiene preferencia sobre la prioridad 4096?
3. ¿Qué cambios se han producido en los Root Ports y en los puertos designados?
4. ¿Ha cambiado la topología física o únicamente la lógica?

#### Paso 6. Analizar los cambios en STP
En los tres switches, ejecuta:

```text
show spanning-tree vlan 1
```

Compara los resultados obtenidos cuando `SW-02` era el Root Bridge y cuando lo era `SW-03`. Registra los cambios:

| Elemento | Root Bridge SW-02 | Root Bridge SW-03 |
|---|---|---|
| Switch raíz | | |
| Root Port de SW-01 | | |
| Root Port de SW-02 | | |
| Root Port de SW-03 | | |
| Puerto alternativo o bloqueado | | |
| Enlace que no reenvía tráfico de usuario | | |

Los puertos concretos que desempeñan cada función dependen de las conexiones utilizadas, los costes de los enlaces y los identificadores de los puertos. Debes anotar los resultados reales de tu simulación. Explica por qué STP puede cambiar los roles y estados de los puertos al cambiar el Root Bridge, aunque los cables permanezcan en la misma posición.

#### Paso 7. Verificar la conectividad
Con `SW-03` como Root Bridge:

1. Comprueba que los enlaces entre switches han terminado de converger.
2. Realiza un `ping` entre `PC01` y `PC02`.
3. Realiza un `ping` entre `LAP01` y `LAP02`.
4. Si el servidor TFTP forma parte de la red y está correctamente configurado, comprueba también su conectividad desde un equipo de la misma subred.
5. Consulta de nuevo `show spanning-tree vlan 1`.

Anota los resultados de las pruebas.
| Prueba | Resultado | Evidencia |
|---|---|---|
| Ping PC01 → PC02 | | |
| Ping LAP01 → LAP02 | | |
| Ping a SRV-TFTP, si procede | | |
| STP estable en los tres switches | | |

Explica por qué la red debe seguir evitando bucles y manteniendo la conectividad después de cambiar el Root Bridge.

#### Paso 8. Guardar la configuración y preparar la entrega
Guarda la configuración de los switches:

```text
copy running-config startup-config
```

Ejecuta el comando en cada switch al que hayas modificado la prioridad.

#### Paso 9. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules. El documento debe contener todas las capturas de pantalla necesarias para demostrar que se ha realizado el procedimiento correctamente. Recordad incluir:
- Tabla comparativa de prioridades y Root Bridge.
- Tabla con los roles y estados de los puertos antes y después de los cambios.
- Capturas de `show spanning-tree vlan 1` de los tres switches.
- Evidencias de las pruebas de conectividad.
- Breve conclusión explicando cómo se controla la elección del Root Bridge.