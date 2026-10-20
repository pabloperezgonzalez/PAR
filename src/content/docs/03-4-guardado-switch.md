---
title: 🔌 UP3.4. Archivos que guardan la configuración del conmutador - CE3.d)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| d) Se han identificado los archivos que guardan la configuración del conmutador. | Teórico | 10 % |  

### 1. Introducción
Un **conmutador gestionable** dispone de diferentes parámetros que determinan su funcionamiento. Por ejemplo:

- Nombre del dispositivo.
- Direcciones IP de administración.
- Contraseñas y usuarios.
- Configuración de los puertos.
- VLAN.
- Seguridad de los puertos.
- Protocolos de red.

Toda esta información debe almacenarse de alguna forma para que el switch pueda utilizarla.

En los switches Cisco, la configuración se almacena principalmente en dos ubicaciones:

- **Running-config**: configuración que está utilizando actualmente el switch.
- **Startup-config**: configuración guardada que se utilizará después de reiniciar el dispositivo.

Comprender la diferencia entre ambas es fundamental para administrar correctamente un conmutador.

### 2. Configuración activa y configuración guardada
Podemos imaginar que el switch dispone de dos configuraciones:

```text
       CONFIGURACIÓN DEL SWITCH

       ┌─────────────────────┐
       │   Running-config    │
       │ Configuración activa│
       └──────────┬──────────┘
                  │
                guardar
                  │
                  ▼
       ┌─────────────────────┐
       │   Startup-config    │
       │ Configuración guardada│
       └─────────────────────┘
```

La **running-config** contiene la configuración que el switch está utilizando en ese momento.
La **startup-config** contiene la configuración que se cargará cuando el dispositivo se reinicie.

### 3. Running-config
La **running-config** es la configuración que está actualmente activa en la memoria del switch. Cuando realizamos un cambio mediante la CLI, normalmente estamos modificando la configuración activa.

Por ejemplo:

```text
Switch(config)# hostname SW-AULA
```

El nombre del dispositivo cambia inmediatamente. La configuración modificada se encuentra en la **running-config** y podemos consultar esta configuración mediante:

```text
Switch# show running-config
```

Este comando muestra la configuración que el switch está utilizando actualmente.

### 3. Startup-config
La **startup-config** es la configuración guardada en la memoria no volátil del dispositivo. Su principal característica es que **permanece almacenada cuando el switch se apaga o se reinicia**. Podemos consultarla mediante:

```text
Switch# show startup-config
```

Esta configuración será utilizada durante el proceso de arranque del switch.

### 4. Diferencia entre Running-config y Startup-config
La diferencia fundamental es:

| Característica | Running-config | Startup-config |
|---|---|---|
| Configuración | Activa | Guardada |
| Se utiliza actualmente | Sí | No directamente |
| Se encuentra en | RAM | NVRAM |
| Se pierde al reiniciar si no se guarda | Sí | No |
| Comando de consulta | `show running-config` | `show startup-config` |

Una forma sencilla de recordarlo es:

```text
RUNNING
   ↓
Lo que está funcionando AHORA

STARTUP
   ↓
Lo que se utilizará al ARRANCAR
```

### 5. ¿Qué ocurre cuando modificamos la configuración?
Supongamos que tenemos un switch cuyo nombre es:

```text
Switch
```

Accedemos al modo de configuración:

```text
Switch# configure terminal
Switch(config)# hostname SW-01
```

Ahora el nombre cambia:

```text
SW-01(config)#
```

El cambio se ha realizado en la **running-config**, pero todavía no hemos guardado la configuración. Podemos representarlo así:

```text
Running-config
      │
      │ Cambio realizado
      ▼
   SW-01

Startup-config
      │
      ▼
   Switch
```

En este momento las dos configuraciones pueden ser diferentes.

### 6. Guardar la configuración
Si queremos conservar los cambios después de reiniciar el switch, debemos guardar la configuración activa. En dispositivos Cisco podemos utilizar:

```text
Switch# copy running-config startup-config
```

También podemos encontrar la forma abreviada:

```text
Switch# write memory
```

Después de guardar:

```text
Running-config
      │
      │ guardar
      ▼
Startup-config
```

Las dos configuraciones contienen ahora los cambios realizados.

### 7. ¿Por qué es importante guardar la configuración?
Imaginemos que un administrador realiza varios cambios:

```text
Configura una VLAN
       ↓
Configura una dirección IP
       ↓
Modifica un puerto
       ↓
Configura seguridad
```

Si los cambios solamente están en la **running-config** y el switch se reinicia antes de guardarlos, esos cambios pueden perderse. Por tanto:

> **Una configuración modificada no debe considerarse permanentemente almacenada hasta que se haya guardado en la startup-config.**

### 8. ¿Qué ocurre al reiniciar?
Cuando el switch se reinicia, necesita cargar una configuración para comenzar a funcionar. El proceso simplificado es:

```text
        Reinicio
           │
           ▼
     Startup-config
           │
           │ cargar
           ▼
     Running-config
           │
           ▼
   Switch funcionando
```

Por tanto, la configuración guardada en la startup-config se carga para convertirse en la configuración activa.

### 9. ¿Qué ocurre si no existe Startup-config?
Si el switch no tiene una configuración guardada, puede arrancar con una configuración inicial o mostrar un proceso de configuración inicial, dependiendo del dispositivo. Esto puede ocurrir, por ejemplo, cuando:

- El switch es nuevo.
- Se ha borrado la configuración.
- Se ha realizado un restablecimiento de fábrica.
- Nunca se ha guardado la configuración.

### 10. Memoria RAM y NVRAM
En los switches Cisco tradicionales, las configuraciones se almacenan en diferentes tipos de memoria.

#### 10.1. RAM
La **RAM** contiene la configuración activa:

```text
RAM
 │
 └── Running-config
```

La RAM es una memoria volátil. Esto significa que su contenido se pierde cuando el dispositivo pierde alimentación.

#### 10.2. NVRAM
La **NVRAM (Non-Volatile RAM)** se utiliza tradicionalmente para almacenar la configuración de inicio:

```text
NVRAM
 │
 └── Startup-config
```

A diferencia de la RAM, la información almacenada en NVRAM se conserva después de apagar o reiniciar el dispositivo.

> **Nota:** la organización exacta de los archivos y memorias puede variar según el modelo y la versión del sistema operativo del switch. En este nivel trabajaremos con el modelo clásico de dispositivos Cisco.

### 11. IOS y archivos del switch
Además de los archivos de configuración, un switch Cisco dispone de otros elementos almacenados en su sistema de archivos. Uno de los más importantes es el **IOS (Internetwork Operating System)**, que constituye el sistema operativo del dispositivo. De forma simplificada:

```text
             SWITCH

        ┌───────────────┐
        │     IOS       │
        │ Sistema       │
        │ operativo     │
        └───────┬───────┘
                │
                │ utiliza
                ▼
        ┌───────────────┐
        │ Configuración │
        │               │
        │ Running       │
        │ Startup       │
        └───────────────┘
```

### 12. Sistema de archivos del switch
Los switches Cisco pueden disponer de diferentes sistemas de almacenamiento. Uno de ellos es la **flash**, que normalmente contiene el sistema operativo IOS. Podemos consultar información relacionada con el almacenamiento mediante comandos como:

```text
Switch# show flash:
```

### 13. Configuración y sistema operativo
Es importante diferenciar:

```text
IOS
 ↓
Sistema operativo del switch

Running-config
 ↓
Configuración que está utilizando

Startup-config
 ↓
Configuración que utilizará al arrancar
```

Por tanto, **IOS y configuración no son lo mismo**. El IOS proporciona el funcionamiento del dispositivo, mientras que los archivos de configuración determinan cómo está configurado.

### 14. Comandos importantes
Por lo tanto, resulta indispensable conocer los comandos previamente explicados:

- Consultar configuración activa ➜ show running-config
- Consultar configuración guardada ➜ show startup-config
- Guardar la configuración ➜ copy running-config startup-config
- Consultar la memoria flash ➜ show flash:

### 15. Buenas prácticas
Al administrar los archivos de configuración de un switch es recomendable:

- Guardar los cambios después de realizar modificaciones importantes.
- Comprobar la configuración antes de guardarla.
- Realizar copias de seguridad periódicas.
- Mantener una copia externa de la configuración.
- Documentar los cambios realizados.
- Evitar modificar la configuración sin comprobar previamente el estado actual.
- Verificar la configuración después de reiniciar el dispositivo

### 16. Caso práctico
Un administrador configura un switch y realiza los siguientes cambios:

```text
Switch# configure terminal
Switch(config)# hostname SW-AULA
```

A continuación comprueba:

```text
Switch# show running-config
```

y observa que el nombre `SW-AULA` aparece en la configuración activa. Sin embargo, antes de apagar el switch no ejecuta:

```text
copy running-config startup-config
```

Al reiniciar el dispositivo, el cambio puede perderse porque solamente se había modificado la configuración activa.

> **Analiza la situación planteada y explica qué diferencia existe entre `running-config` y `startup-config`. Indica qué comando utilizarías para guardar permanentemente los cambios realizados y qué podría ocurrir si el switch se reinicia antes de guardar la configuración.**