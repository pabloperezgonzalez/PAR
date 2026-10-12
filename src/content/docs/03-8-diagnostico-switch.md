---
title: 🔌 UP3.8. Comandos de diagnóstico y seguimiento de incidencias en el conmutador - CE3.h)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| h) Se han utilizado los comandos proporcionados por el sistema operativo del conmutador que permiten hacer el seguimiento de posibles incidencias. | Práctico |  % | 

### 1. Introducción
Un conmutador puede presentar diferentes problemas durante su funcionamiento:

- Un puerto puede estar desconectado.
- Una interfaz puede estar deshabilitada.
- Puede existir un problema de configuración.
- Un dispositivo puede no aparecer en la tabla MAC.
- Puede existir un problema de conectividad.
- Una VLAN puede estar configurada incorrectamente.
- Pueden producirse errores en una interfaz.
- Puede existir un problema relacionado con **Spanning Tree Protocol (STP)**.

Por este motivo, un administrador de redes necesita herramientas que le permitan **obtener información sobre el estado del switch y detectar posibles incidencias**. Los sistemas operativos de los switches proporcionan diferentes comandos para realizar estas tareas. 

En equipos Cisco, muchos de estos comandos comienzan por:

```text
show
```

Por ejemplo:

```text
show version
show interfaces
show vlan
show mac address-table
```

### 2. ¿Qué es el diagnóstico de un switch?
El **diagnóstico** consiste en recopilar información sobre el estado y funcionamiento del dispositivo para identificar posibles problemas. Podemos representarlo mediante el siguiente proceso:

```text
       INCIDENCIA
           │
           ▼
   Recopilar información
           │
           ▼
    Analizar resultados
           │
           ▼
    Identificar problema
           │
           ▼
    Aplicar solución
           │
           ▼
      Comprobar
       resultado
```

Por tanto, diagnosticar no consiste simplemente en ejecutar comandos, sino en **interpretar la información obtenida**.

### 3. Acceso a la línea de comandos
Para utilizar los comandos de diagnóstico debemos acceder a la interfaz de administración del switch. Por ejemplo:

```text
Switch>
```

Este es el modo EXEC de usuario. Para acceder al modo privilegiado:

```text
Switch> enable

Switch#
```

Desde este modo podemos ejecutar muchos de los comandos de diagnóstico. Por ejemplo:

```text
Switch# show version
```

### 4. Comandos `show`
Los comandos `show` permiten consultar información sobre diferentes elementos del switch. Algunos de los más importantes son:

| Comando | Información principal |
|---------|------------------------|
| `show version` | Versión del sistema operativo y características del equipo |
| `show running-config` | Configuración activa |
| `show startup-config` | Configuración almacenada para el arranque |
| `show interfaces` | Estado y estadísticas de las interfaces |
| `show interfaces status` | Estado resumido de los puertos |
| `show vlan brief` | VLAN configuradas y puertos asociados |
| `show mac address-table` | Direcciones MAC aprendidas |
| `show ip interface brief` | Estado resumido de las interfaces con IP |
| `show spanning-tree` | Información sobre STP |
| `show port-security` | Información sobre seguridad de puertos |

Estos comandos permiten obtener una visión general del funcionamiento del dispositivo.

### 5. Consultar la versión del sistema operativo
El comando:

```text
show version
```

proporciona información sobre el sistema operativo y el hardware. Por ejemplo:

```text
Switch# show version
```

Podemos obtener información como:
- Versión del IOS.
- Modelo del switch.
- Memoria disponible.
- Tiempo desde el último reinicio.
- Imagen utilizada.
- Información del hardware.

### 6. Consultar la configuración actual
El comando:

```text
show running-config
```

permite consultar la **configuración que está utilizando actualmente el switch**. Por ejemplo:

```text
Switch# show running-config
```

Podemos encontrar información relacionada con:

- Nombre del dispositivo.
- Interfaces.
- VLAN.
- Direccionamiento IP.
- Seguridad.
- Contraseñas.
- Protocolos.
- Configuración de puertos.

### 7. Configuración actual frente a configuración guardada
Es importante diferenciar:

```text
running-config ➜ Es la configuración que está utilizando actualmente el switch.
```

de:

```text
startup-config ➜ Es la configuración almacenada para utilizarla durante el próximo arranque.
```

Podemos consultar la configuración almacenada mediante:

```text
show startup-config
```

Por tanto:

```text
              SWITCH
                 │
        ┌────────┴────────┐
        │                 │
        ▼                 ▼
running-config      startup-config
        │                 │
        ▼                 ▼
Configuración       Configuración
actual              guardada
```

### 8. Consultar el estado de los puertos
Uno de los primeros elementos que debemos comprobar ante un problema de conectividad es el estado de las interfaces. Podemos utilizar:

```text
show interfaces status
```

Este comando proporciona una visión resumida de los puertos. Por ejemplo:

```text
Port      Name      Status       
Fa0/1      1        connected    
Fa0/2      2        notconnect   
Fa0/3      3        connected   
```

Podemos interpretar como un puerto que tiene un enlace activo:

```text
connected
```

Mientras que este indica que no existe un enlace activo en ese momento:

```text
notconnect
```

### 9. Consultar información detallada de una interfaz
Para obtener información más completa podemos utilizar:

```text
show interfaces fastEthernet 0/1
```

Este comando puede proporcionar información sobre:
- Estado de la interfaz.
- Estado del protocolo.
- Número de paquetes enviados.
- Número de paquetes recibidos.
- Errores.
- Colisiones.
- Descartes.
- Velocidad.
- Dúplex.
- Estadísticas de tráfico.

Por ejemplo:

```text
Switch# show interfaces fastEthernet 0/1
```

### 10. Estado de una interfaz
Una información importante es el estado del puerto. Podemos encontrar situaciones como:

```text
up
```

o:

```text
down
```

De forma simplificada:

```text
Puerto
  │
  ├── up → enlace funcionando
  └── down → enlace no disponible
```

### 11. Errores en las interfaces
El comando siguiente permite consultar estadísticas relacionadas con errores:

```text
show interfaces
```

Podemos encontrar información sobre:
- Paquetes con errores.
- Errores de entrada.
- Errores de salida.
- Paquetes descartados.
- Problemas de transmisión.
- Otros contadores relacionados con la interfaz.

Por ejemplo:

```text
Input errors
Output errors
CRC
Drops
```

### 12. Errores CRC
Los errores **CRC (Cyclic Redundancy Check)** pueden indicar problemas en la recepción de tramas. Un número elevado de errores CRC puede estar relacionado, entre otras causas, con:

- Cableado defectuoso.
- Problemas físicos.
- Interferencias.
- Problemas en una interfaz.
- Configuraciones incorrectas en determinados escenarios.

Por tanto:

```text
show interfaces
       │
       ▼
¿Hay errores CRC?
       │
       ▼
Investigar posible problema
físico o de enlace
```

### 13. Consultar las direcciones MAC
El comando siguiente permite consultar la tabla de direcciones MAC:

```text
show mac address-table
```
Por ejemplo:

```text
Vlan    Mac Address       Type       Ports
----    -----------       ----       -----
10      aaaa.aaaa.aaaa    DYNAMIC    Fa0/1
10      bbbb.bbbb.bbbb    DYNAMIC    Fa0/2
20      cccc.cccc.cccc    DYNAMIC    Fa0/3
```

Esta información permite comprobar si el switch está aprendiendo las direcciones MAC de los dispositivos.

### 14. Consultar las interfaces con IP
El comando siguiente permite obtener una visión resumida del estado de las interfaces que utilizan direccionamiento IP:

```text
show ip interface brief
```

Por ejemplo:

```text
Interface        IP-Address      Status      Protocol
Vlan1            192.168.1.2     up          up
Vlan10           192.168.10.2    up          up
```

Este comando es especialmente útil para comprobar rápidamente:
- Dirección IP.
- Estado de la interfaz.
- Estado del protocolo.

### 15. Comprobar la seguridad del puerto
Si hemos configurado **Port Security**, podemos utilizar:

```text
show port-security
```

También podemos consultar una interfaz concreta:

```text
show port-security interface fastEthernet 0/1
```

Podemos obtener información sobre:
- Si Port Security está activado.
- Número máximo de MAC permitidas.
- Direcciones MAC seguras.
- Número de violaciones.
- Estado de seguridad del puerto.

### 16. Comprobar Spanning Tree
El protocolo **Spanning Tree Protocol (STP)** evita determinados bucles de capa 2. Podemos consultar su funcionamiento mediante:

```text
show spanning-tree
```

Este comando permite obtener información sobre:
- Bridge ID.
- Root Bridge.
- Puertos en forwarding.
- Puertos en blocking.
- Costes.
- Roles de los puertos.

Por ejemplo:

```text
Switch# show spanning-tree
```

### 17. Probar la conectividad
Aunque los comandos `show` proporcionan mucha información, también podemos realizar pruebas activas. Una herramienta fundamental es:

```text
ping
```

Por ejemplo:

```text
Switch# ping 192.168.1.1
```

El objetivo es comprobar si existe conectividad IP con otro dispositivo. Podemos representar el proceso:

```text
Switch
  │
  │ ping
  ▼
Router
  │
  ├── Responde → conectividad
  │
  └── No responde → investigar
```

### 18. Diferencia entre `show` y `ping`
Es importante entender que no realizan la misma función.

##### 18.1. `show`
Permite consultar información. Por ejemplo:

```text
show interfaces
```

#### 18.2.  `ping`
Permite comprobar la conectividad. Por ejemplo:

```text
ping 192.168.1.1
```

### 19. Utilizar la ayuda del sistema operativo
Los sistemas operativos de los switches proporcionan mecanismos de ayuda.

Mostrar los comandos disponibles en ese modo:
```text
Switch# ?
```

Consultar las opciones disponibles después de `show`:
```text
Switch# show ?
```

Por ejemplo:
```text
Switch# show interfaces ?
```

### 20. Completado de comandos
En Cisco IOS también podemos utilizar la tecla **TAB** para completar comandos. Por ejemplo:

```text
Switch# show inter
```

y utilizar `TAB` para completar:

```text
show interfaces
```

### 21. Seguimiento de incidencias
El diagnóstico debe realizarse de forma ordenada. Por ejemplo, ante un problema de conectividad de un ordenador:

```text
1. Comprobar cable y enlace físico
              ↓
2. Comprobar estado del puerto
              ↓
3. Comprobar tabla MAC
              ↓
4. Comprobar configuración
              ↓
5. Comprobar conectividad
              ↓
6. Analizar errores
```

### 22. Metodología básica de diagnóstico
Para resolver incidencias en un switch es recomendable seguir una metodología.

#### 22.1. Identificar el problema
Preguntar:

```text
¿Qué dispositivo tiene problemas?
¿Qué puerto utiliza?
¿Qué servicio no funciona?
¿Cuándo comenzó el problema?
```

#### 22.2. Recopilar información
Utilizar comandos como:

```text
show interfaces status
show vlan brief
show mac address-table
show running-config
```

#### 22.3. Analizar
Comparar la información obtenida con la configuración esperada.

#### 22.4. Aplicar una solución
Modificar únicamente aquello que sea necesario.

#### 22.5. Comprobar
Verificar que la incidencia ha desaparecido.

### 23. Actividad UP3.8. Comandos de diagnóstico y seguimiento de incidencias en el conmutador - CE3.h)