---
title: 🔌 UP3.1. Conexión de conmutadores entre sí y con estaciones de trabajo - CE3.a)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| a) Se han conectado conmutadores entre sí y con las estaciones de trabajo. | Práctico |  % | 

### 1. Introducción
Un **conmutador de red (switch)** es un dispositivo que permite conectar diferentes equipos dentro de una red local (LAN), como ordenadores, servidores, impresoras, puntos de acceso u otros dispositivos de red.

Una de las primeras tareas que debe conocer un administrador de redes es la **conexión física de los dispositivos**, ya que una configuración correcta del switch no servirá de nada si los equipos no están correctamente conectados. En este criterio aprenderemos a conectar **estaciones de trabajo a un conmutador**, conectar **varios conmutadores entre sí** y comprobar que los enlaces funcionan correctamente.

### 2. ¿Qué es un conmutador?
Un **conmutador o switch** es un dispositivo de red que trabaja principalmente en la **capa 2 del modelo OSI**. Su función principal es recibir tramas Ethernet y enviarlas por el puerto correspondiente basándose en las **direcciones MAC** de los dispositivos. Por ejemplo:

```text
        PC1
         │
         │
      ┌───────┐
      │ Switch│
      └───────┘
         │
         │
        PC2
```

El switch permite que PC1 y PC2 puedan comunicarse dentro de la misma red local.

### 3. Puertos del conmutador
Los switches disponen de diferentes **puertos Ethernet** mediante los cuales se conectan los dispositivos. Dependiendo del modelo, podemos encontrar:

- Puertos **Fast Ethernet**: hasta 100 Mbps.
- Puertos **Gigabit Ethernet**: hasta 1 Gbps.
- Puertos **10 Gigabit Ethernet**: hasta 10 Gbps.
- Puertos de fibra óptica en determinados modelos.

Los puertos pueden utilizar conectores **RJ-45** cuando se emplea cable de cobre.

### 4. Conexión de una estación de trabajo
Una estación de trabajo, como un ordenador, se conecta normalmente a uno de los puertos Ethernet del switch mediante un cable de red.

```text
┌─────────────┐
│ Ordenador   │
│   PC1       │
└──────┬──────┘
       │
       │ Cable Ethernet
       │
┌───────────────┐
│    SWITCH     │
│               │
│  [1][2][3][4]│
└───────────────┘
```

El procedimiento básico es:

1. Conectar un extremo del cable a la tarjeta de red del ordenador.
2. Conectar el otro extremo a un puerto Ethernet del switch.
3. Comprobar que los conectores están correctamente insertados.
4. Comprobar los LED del puerto.
5. Verificar posteriormente la configuración de red.

### 5. Cable utilizado
En las instalaciones actuales se utiliza habitualmente **cable Ethernet de par trenzado** con conectores RJ-45. El cable más habitual es el **cable directo**.

```text
PC ───────────── Switch
       Cable
       Ethernet
```

Los dispositivos modernos suelen incorporar **Auto-MDI/MDIX**, por lo que pueden detectar automáticamente cómo deben utilizarse los pares de transmisión y recepción. Por este motivo, actualmente no es necesario seleccionar normalmente un cable cruzado para conectar dispositivos del mismo tipo.

### 6. Conexión de varios equipos
Un switch permite conectar múltiples dispositivos dentro de una misma red local. Por ejemplo:

```text
                  ┌──────────┐
                  │  Switch  │
                  └────┬─────┘
           ┌───────────┼───────────┐
           │           │           │
          PC1         PC2         PC3
```

Cada equipo utiliza un puerto independiente del switch. Esto permite que los dispositivos puedan comunicarse entre sí siempre que su configuración de red sea compatible.

### 7. Conexión de dos conmutadores
Cuando una red necesita conectar más dispositivos de los que permite un único switch, podemos utilizar varios conmutadores conectados entre sí.

```text
       Switch 1
    ┌─────────────┐
    │             │
    └──────┬──────┘
           │
           │ Enlace
           │
    ┌──────┴──────┐
    │             │
    └─────────────┘
       Switch 2
```

Los switches pueden utilizar un puerto Ethernet para establecer el enlace entre ellos.

### 8. Red formada por varios conmutadores
En una red real podemos encontrar una estructura similar a:

```text
                    Router
                      │
                      │
                ┌─────┴─────┐
                │  Switch 1 │
                └─────┬─────┘
             ┌────────┼────────┐
             │        │        │
            PC1      PC2    Switch 2
                              │
                       ┌──────┼──────┐
                       │      │      │
                      PC3    PC4    PC5
```

El **Switch 1** actúa como punto de conexión con el router y con el **Switch 2**. El Switch 2 permite ampliar el número de dispositivos conectados a la red.

### 9. Enlace entre switches
El enlace entre dos switches se denomina habitualmente **enlace entre conmutadores** o *switch-to-switch link*.

```text
Switch 1
   │
   │
   │ Enlace Ethernet
   │
   ▼
Switch 2
```

Este enlace debe tener una capacidad suficiente para transportar el tráfico generado por los dispositivos conectados al segundo switch. Por ejemplo, si varios ordenadores están conectados al Switch 2, todo su tráfico que deba pasar por el Switch 1 utilizará el enlace entre ambos.

### 10. Velocidad de los enlaces
Es importante comprobar la velocidad soportada por los puertos. Por ejemplo:

```text
PC ──── 1 Gbps ──── Switch
```

o:

```text
Switch 1 ──── 1 Gbps ──── Switch 2
```

Una conexión puede funcionar correctamente aunque los dispositivos negocien una velocidad inferior a la esperada. Por ello, el administrador debe comprobar tanto la **conectividad** como la **velocidad negociada**.

### 11. Comprobación de la configuración IP
Una conexión física correcta no garantiza que exista comunicación entre los dispositivos. También debemos comprobar la configuración lógica.

Por ejemplo:

```text
PC1
IP:      192.168.1.10
Máscara: 255.255.255.0

PC2
IP:      192.168.1.20
Máscara: 255.255.255.0
```

Ambos equipos pertenecen a la misma red:

```text
192.168.1.0/24
```

Por tanto, deberían poder comunicarse directamente a través del switch.

### 12. Comprobación mediante `ping`
Una de las primeras pruebas que podemos realizar es utilizar el comando `ping`. Desde PC1:

```bash
ping 192.168.1.20
```

Si recibimos respuestas, existe conectividad entre ambos equipos.

```text
Respuesta desde 192.168.1.20
Tiempo < 1 ms
```

Si no recibimos respuesta, será necesario investigar la causa.

### 13. Posibles problemas de conexión
Cuando un equipo no consigue comunicarse, debemos realizar un diagnóstico ordenado.

| Problema | Posible causa |
|----------|---------------|
| No se enciende el LED | Cable desconectado o defectuoso |
| No hay enlace | Puerto deshabilitado o problema físico |
| Velocidad inferior | Cable o negociación de velocidad |
| No responde al ping | Configuración IP incorrecta |
| Equipos en redes diferentes | Dirección IP o máscara incorrecta |
| Un switch no comunica | Problema en el enlace entre switches |

### 14. Conexión física y conexión lógica
Es importante diferenciar ambos conceptos.

#### 14.1. Conexión física
Hace referencia a los elementos materiales:

- Cables.
- Conectores.
- Puertos.
- Switches.
- Tarjetas de red.

#### 14.2. Conexión lógica
Hace referencia a la configuración que permite la comunicación:

- Dirección IP.
- Máscara de subred.
- Puerta de enlace.
- VLAN.
- Rutas.

Podemos tener una conexión física correcta pero una configuración lógica incorrecta.

```text
Cable conectado
      │
      ▼
LED encendido
      │
      ▼
Configuración IP correcta
      │
      ▼
Ping correcto
      │
      ▼
Comunicación
```

### 15. Buenas prácticas
Al conectar switches y estaciones de trabajo es recomendable:

- Identificar previamente cada dispositivo.
- Utilizar cables adecuados y en buen estado.
- Etiquetar los cables.
- Documentar qué dispositivo está conectado a cada puerto.
- Comprobar los LED después de realizar la conexión.
- Comprobar la velocidad negociada.
- Verificar la configuración IP.
- Realizar pruebas de conectividad.
- Documentar las incidencias encontradas.

En instalaciones profesionales, la **documentación y el etiquetado** son tan importantes como realizar correctamente la conexión.

### 16. Actividad UP3.1. Conexión de conmutadores entre sí y con estaciones de trabajo - CE3.a)