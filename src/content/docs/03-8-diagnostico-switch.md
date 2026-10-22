---
title: 🔌 UP3.8. Comandos de diagnóstico y seguimiento de incidencias en el conmutador - CE3.h)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| h) Se han utilizado los comandos proporcionados por el sistema operativo del conmutador que permiten hacer el seguimiento de posibles incidencias. | Práctico | 10 % | 

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
Partiendo del escenario de la actividad del criterio CE3.g), utiliza la CLI de Cisco Packet Tracer para diagnosticar y resolver tres incidencias en la red de la empresa. En cada caso, deberás identificar el problema, utilizar los comandos adecuados, aplicar una solución y comprobar que la red vuelve a funcionar correctamente.

#### Paso 1. Recuperar el escenario anterior
Abre el archivo de la actividad anterior finalizada. Conserva los dispositivos y las conexiones de la actividad anterior:

- `SW-01` y `SW-02`.
- `PC01-NombreApellido` y `PC02-NombreApellido`.
- `LAP01-NombreApellido` y `LAP02-NombreApellido`.
- `SRV-TFTP`, si se añadió en la actividad anterior.
- Las direcciones IP y la configuración de seguridad de puertos de `SW-01`.

#### Paso 2. Preparar las herramientas de diagnóstico
Durante la actividad utilizarás los siguientes comandos:

| Comando | Utilidad |
|---|---|
| `show ip interface brief` | Consulta las direcciones IP y el estado de las interfaces. |
| `show interfaces status` | Muestra el estado de los puertos del switch. |
| `show interfaces` | Consulta información detallada y estadísticas de una interfaz. |
| `show mac address-table` | Muestra las direcciones MAC aprendidas. |
| `show running-config` | Permite revisar la configuración activa. |
| `show port-security` | Consulta el estado general de la seguridad de los puertos. |
| `show port-security interface fa0/1` | Consulta la seguridad de un puerto concreto. |
| `ping` | Comprueba la conectividad IP con otro dispositivo. |

No es necesario utilizar todos los comandos en cada incidencia. Selecciona los que te ayuden a encontrar el origen del problema.

#### Paso 3. Incidencia 1: un puerto está desactivado
El administrador informa de que `PC01-NombreApellido` no puede comunicarse con otros dispositivos de su red.

##### Tareas
1. Accede a la CLI de `SW-01`.
2. Ejecuta:

```text
enable
show interfaces status
```

3. Identifica el puerto al que está conectado `PC01-NombreApellido`.
4. Comprueba su estado y revisa la configuración de la interfaz.
5. Si el puerto está administrativamente desactivado, entra en la configuración de esa interfaz y actívala.

Ejemplo, suponiendo que el PC está conectado a `FastEthernet0/1`:

```text
configure terminal
interface fastEthernet 0/1
no shutdown
end
```

6. Vuelve a consultar el estado del puerto.
7. Comprueba si el problema se ha resuelto.

##### Registra los resultados
| Dato | Resultado |
|---|---|
| Dispositivo afectado | |
| Puerto | |
| Comando utilizado para localizar el problema | |
| Problema identificado | |
| Solución aplicada | |
| Resultado final | |

**Nota:** si el puerto ya estaba activo, no lo desactives innecesariamente. Explica qué has comprobado y pasa a la siguiente incidencia.

#### Paso 4. Incidencia 2: un puerto no aprende la dirección MAC esperada
El administrador sospecha que el switch no está aprendiendo correctamente la dirección MAC de uno de los equipos.

##### Tareas
1. Genera tráfico desde `PC02-NombreApellido`, por ejemplo mediante un `ping` a otro dispositivo de su red.
2. En `SW-01`, ejecuta:

```text
show mac address-table
```

3. Localiza la dirección MAC de `PC02-NombreApellido`.
4. Comprueba en qué puerto aparece aprendida.
5. Si no aparece, revisa el estado de la interfaz y la conexión física.
6. Genera tráfico de nuevo y vuelve a consultar la tabla MAC.

##### Registra los resultados
| Comprobación | Resultado |
|---|---|
| MAC esperada | |
| Puerto al que está conectado el PC | |
| ¿Aparece en la tabla MAC? | |
| Problema detectado, si existe | |
| Solución aplicada | |

##### Preguntas
1. ¿Por qué un switch aprende las direcciones MAC?
2. ¿Qué información aporta el puerto asociado a una dirección MAC?
3. ¿Por qué puede ser necesario generar tráfico antes de volver a consultar la tabla?

**Importante:** no borres la tabla MAC ni cambies la configuración de seguridad para forzar un resultado. Debes diagnosticar la situación antes de aplicar una solución.

#### Paso  5. Incidencia 3: infracción de seguridad de puerto
El administrador informa de que uno de los puertos de `SW-01` ha dejado de permitir tráfico después de conectar un dispositivo diferente al autorizado.

##### Tareas
1. Consulta el estado general de la seguridad:

```text
show port-security
```

2. Consulta el puerto afectado. Por ejemplo:

```text
show port-security interface fastEthernet 0/1
```

3. Comprueba si aparecen infracciones o si el puerto está en estado `secure-shutdown`.
4. Revisa la configuración del puerto:

```text
show running-config
```

5. Identifica la causa de la incidencia.
6. Restaura el dispositivo autorizado y, si el puerto está en estado de apagado por seguridad, recupera su funcionamiento siguiendo el procedimiento adecuado para el modo de infracción configurado.

Si se ha utilizado el modo predeterminado `shutdown`, puedes necesitar reactivar el puerto:

```text
configure terminal
interface fastEthernet 0/1
shutdown
no shutdown
end
```

7. Vuelve a comprobar el estado del puerto y realiza una prueba de conectividad.

##### Registra los resultados
| Dato | Resultado |
|---|---|
| Puerto afectado | |
| Número de infracciones | |
| Modo de seguridad configurado | |
| Causa de la incidencia | |
| Solución aplicada | |
| ¿Vuelve a funcionar el dispositivo autorizado? | |

**Precaución:** no elimines la seguridad del puerto como solución. El objetivo es resolver la incidencia manteniendo la protección configurada.

#### Paso 6. Verificación final
Cuando hayas resuelto las incidencias, comprueba que la red conserva su funcionamiento previsto.

1. Consulta el estado de los puertos de ambos switches.
2. Comprueba la tabla MAC de `SW-01`.
3. Revisa el estado de Port Security en los puertos protegidos.
4. Realiza un `ping` entre `PC01-NombreApellido` y `PC02-NombreApellido`.
5. Comprueba que los dispositivos autorizados vuelven a comunicarse.

Registra los resultados:

| Prueba | Resultado esperado | Resultado obtenido |
|---|---|---|
| Estado de los puertos | Puertos necesarios activos | |
| Tabla MAC | Direcciones aprendidas correctamente | |
| Port Security | Seguridad habilitada | |
| Ping entre los PCs | Respuesta satisfactoria | |

#### Paso 7. Informe de diagnóstico
Elabora un breve informe con las tres incidencias. Para cada una debes incluir:

- Síntoma observado.
- Comandos utilizados.
- Información obtenida.
- Causa identificada.
- Solución aplicada.
- Comprobación final.

Incluye capturas de pantalla que demuestren el diagnóstico y la resolución.

#### Paso 8. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules. El documento debe contener todas las capturas de pantalla necesarias para demostrar que se ha realizado el procedimiento correctamente. Recordad incluir:
- Tabla de resultados de las tres incidencias.
- Capturas de los comandos utilizados.
- Informe de diagnóstico y resolución.