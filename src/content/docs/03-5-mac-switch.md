---
title: 🔌 UP3.5. Administración de la tabla de direcciones MAC del conmutador - CE3.e)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| e) Se ha administrado la tabla de direcciones MAC del conmutador. | Práctico |  % |

### 1. Introducción
Una de las funciones fundamentales de un **conmutador (switch)** es aprender qué dispositivos están conectados a cada uno de sus puertos. Para ello, el switch utiliza las **direcciones MAC** de los dispositivos y construye una tabla que relaciona cada dirección MAC con el puerto por el que puede alcanzarse.

Esta información se conoce como **tabla de direcciones MAC**, **tabla CAM** o **MAC Address Table**. Por ejemplo:

```text
                SWITCH

        ┌─────────────────────┐
        │                     │
        │     Tabla MAC       │
        │                     │
        │ MAC          Puerto │
        │ AA:AA...     Fa0/1  │
        │ BB:BB...     Fa0/2  │
        │ CC:CC...     Fa0/3  │
        │                     │
        └─────────────────────┘
```

Gracias a esta tabla, el switch puede decidir por qué puerto debe enviar una trama Ethernet.

### 2. ¿Qué es una dirección MAC?
Una **dirección MAC (Media Access Control)** es un identificador asociado a una interfaz de red. Normalmente se representa mediante **48 bits**, expresados en hexadecimal. Por ejemplo:

```text
00:1A:2B:3C:4D:5E
```

### 3. ¿Para qué utiliza el switch las direcciones MAC?
Cuando una trama Ethernet llega a un puerto del switch, el dispositivo analiza principalmente la **dirección MAC de destino** para decidir dónde debe enviar la trama. Por ejemplo:

```text
PC1                         PC2
MAC: AA:AA...               MAC: BB:BB...
 │                              ▲
 │                              │
 └──────────► SWITCH ───────────┘
```

El switch necesita saber en qué puerto está conectada la MAC de PC2. Para ello utiliza su tabla MAC.

### 4. ¿Cómo aprende el switch las direcciones MAC?
El aprendizaje de direcciones MAC se realiza de forma automática. Supongamos que tenemos:

```text
          Switch
        ┌─────────┐
        │         │
       PC1       PC2
```

PC1 está conectado al puerto `Fa0/1`. Cuando PC1 envía una trama al switch, este observa la **MAC de origen**. Por ejemplo:

```text
MAC origen:
AA:AA:AA:AA:AA:AA
```

El switch aprende:

```text
AA:AA:AA:AA:AA:AA → Fa0/1
```

De esta forma construye progresivamente su tabla.

### 5. Proceso de aprendizaje
Podemos resumir el proceso de esta manera:

1. Llega una trama al switch
2. El switch observa la MAC de origen
3. Relaciona MAC + puerto de entrada
4. Guarda la información en la tabla MAC


### 6. Ejemplo de tabla MAC
Supongamos que tenemos:

```text
          SWITCH
        ┌─────────┐
        │         │
      PC1        PC2
      Fa0/1      Fa0/2
```

La tabla podría contener:

| Dirección MAC | Puerto |
|---------------|--------|
| AA:AA:AA:AA:AA:AA | Fa0/1 |
| BB:BB:BB:BB:BB:BB | Fa0/2 |

El switch ya sabe qué puerto debe utilizar para alcanzar cada dispositivo.

### 7. ¿Qué ocurre cuando llega una trama?
Supongamos que PC1 quiere comunicarse con PC2.

```text
PC1
 │
 │ Trama Ethernet
 │ Destino: BB:BB...
 ▼
Switch
 │
 │ Consulta tabla MAC
 ▼
Fa0/2
 │
 ▼
PC2
```

El switch consulta la tabla y descubre que la dirección:

```text
BB:BB:BB:BB:BB:BB
```

está asociada al puerto:

```text
Fa0/2
```

Por tanto, envía la trama por ese puerto.

### 8. ¿Qué ocurre si el switch no conoce la MAC de destino?
Si el switch recibe una trama cuya dirección MAC de destino no aparece en su tabla, no sabe inicialmente por qué puerto se encuentra ese dispositivo. En ese caso, puede realizar un **flooding** de la trama. De forma simplificada:

```text
             Switch
               │
        ┌──────┼──────┐
        │      │      │
       PC1    PC2    PC3
```

La trama se envía por los puertos correspondientes de la misma VLAN, excepto por el puerto por el que llegó. Cuando el dispositivo de destino responde, el switch puede aprender su dirección MAC.

### 9. Tabla MAC dinámica
Las direcciones aprendidas automáticamente se denominan normalmente **entradas dinámicas**. Estas entradas no permanecen indefinidamente. El switch utiliza un mecanismo denominado **aging** o envejecimiento. Si una dirección MAC no se utiliza durante un determinado período de tiempo, la entrada puede eliminarse de la tabla. Por ejemplo:

```text
MAC aprendida
     │
     ▼
Se utiliza
     │
     ▼
Se mantiene en la tabla
     │
     ▼
Deja de utilizarse
     │
     ▼
Transcurre el tiempo de aging
     │
     ▼
Se elimina
```

Esto permite que el switch actualice su información cuando los dispositivos cambian de puerto.

### 10. Entradas estáticas
Además de las entradas aprendidas automáticamente, algunos switches permiten configurar **entradas MAC estáticas**. Una entrada estática establece manualmente una relación entre una dirección MAC y un puerto. Por ejemplo:

```text
MAC: AA:AA:AA:AA:AA:AA
Puerto: Fa0/5
```

El administrador puede utilizar esta configuración cuando necesita controlar de forma específica cómo debe tratarse una determinada dirección MAC. Las entradas estáticas no dependen del aprendizaje automático de la misma manera que las entradas dinámicas.

### 11. Consultar la tabla MAC
En switches Cisco podemos utilizar:

```text
show mac address-table
```

Este comando permite consultar las direcciones MAC que el switch ha aprendido. La información puede aparecer de forma similar a:

```text
          Mac Address Table

Vlan    Mac Address       Type       Ports
----    -----------       ----       -----
  1     aaaa.aaaa.aaaa    DYNAMIC    Fa0/1
  1     bbbb.bbbb.bbbb    DYNAMIC    Fa0/2
  1     cccc.cccc.cccc    DYNAMIC    Fa0/3
```

### 12. Información de la tabla MAC
En la tabla podemos encontrar diferentes datos.

| Campo | Significado |
|-------|-------------|
| **VLAN** | VLAN asociada a la entrada |
| **MAC Address** | Dirección MAC aprendida |
| **Type** | Tipo de entrada |
| **Ports** | Puerto asociado a la dirección |

Esta información resulta muy útil para localizar dispositivos dentro de la red.

### 13. Consultar las MAC de un puerto
También podemos consultar información más específica.

Por ejemplo:

```text
show mac address-table interface fastEthernet 0/1
```

Este comando permite consultar las direcciones MAC asociadas a una determinada interfaz. También podemos filtrar información de la tabla según diferentes criterios.

### 14. Borrar la tabla MAC
En determinadas situaciones puede ser necesario eliminar las entradas dinámicas aprendidas por el switch. Por ejemplo, después de realizar cambios importantes en la infraestructura. En Cisco podemos utilizar:

```text
clear mac address-table dynamic
```

Al borrar las entradas dinámicas, el switch tendrá que volver a aprender las direcciones MAC a medida que reciba nuevas tramas.
> **Importante:** los comandos disponibles pueden variar según el modelo y la versión del sistema operativo del switch.

### 15. ¿Por qué puede ser necesario borrar la tabla?
Imaginemos que un ordenador estaba conectado:

```text
PC1 ─── Fa0/1
```

y posteriormente lo conectamos a:

```text
PC1 ─── Fa0/10
```

El switch tendrá que actualizar la información sobre dónde se encuentra esa MAC. Normalmente lo hará automáticamente cuando reciba nuevas tramas. La eliminación de entradas dinámicas también puede utilizarse durante determinadas tareas de diagnóstico.

### 16. Movimiento de una dirección MAC
Un dispositivo puede cambiar de puerto. Por ejemplo:

```text
Antes:

PC1 → Fa0/1
```

Después:

```text
PC1 → Fa0/10
```

El switch detectará que la dirección MAC aparece ahora por otro puerto y actualizará su tabla. Esto demuestra que la tabla MAC es **dinámica** y se adapta a los cambios de la red.

### 17. Tabla MAC vs tabla ARP
Es importante no confundir estos dos conceptos:
- Tabla MAC ➜ Se utiliza principalmente en la **capa 2** y relaciona **MAC → Puerto del switch**.
- Tabla ARP ➜ Se utiliza para resolver direcciones IP en direcciones MAC dentro de una red local y relaciona **IP → MAC**.

### 18. Herramientas para administrar la tabla MAC
Algunos comandos útiles en switches Cisco son los siguientes:

Consultar la tabla completa:
```text
show mac address-table
```

Consultar las entradas dinámicas:
```text
show mac address-table dynamic
```

Consultar las MAC asociadas a una interfaz:
```text
show mac address-table interface fastEthernet 0/1
```

Eliminar entradas dinámicas:
```text
clear mac address-table dynamic
```

### 19. Actividad UP3.5. Administración de la tabla de direcciones MAC del conmutador - CE3.e)