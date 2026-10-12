---
title: 🔌 UP3.6. Configuración de la seguridad del puerto del conmutador - CE3.f)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| f) Se ha configurado la seguridad del puerto. | Práctico |  % | 

### 1. Introducción
Los puertos de un conmutador permiten conectar diferentes dispositivos de red, como ordenadores, impresoras, teléfonos IP o puntos de acceso inalámbricos. Sin embargo, no siempre queremos que **cualquier dispositivo pueda conectarse a cualquier puerto**. Por ejemplo, en un aula podemos establecer que:

```text
Puerto Fa0/1 → PC del profesor
Puerto Fa0/2 → PC del alumno 1
Puerto Fa0/3 → PC del alumno 2
```

Si alguien desconecta el ordenador de un puerto y conecta otro dispositivo, podríamos querer que el switch detectase esta situación y actuase según una política de seguridad. Para controlar este tipo de situaciones, muchos switches gestionables incorporan mecanismos de **seguridad de puertos**, conocidos habitualmente como **Port Security**.

### 2. ¿Qué es la seguridad de puerto?
La **seguridad de puerto** permite controlar qué direcciones MAC pueden utilizar determinados puertos del switch. La idea básica es:

```text
Puerto del switch
       │
       ▼
Direcciones MAC permitidas
       │
       ▼
¿La MAC está autorizada?
       │
   ┌───┴───┐
   │       │
   SÍ      NO
   │       │
   ▼       ▼
Permitir   Aplicar
tráfico    política
```

### 3. Relación con la tabla MAC
La seguridad de puertos está directamente relacionada con el criterio anterior. En la UP anterior, hemos visto que el switch mantiene una tabla que relaciona:

```text
MAC + VLAN + Puerto
```

Port Security utiliza esta información para determinar qué dispositivos están autorizados a utilizar un puerto. Por ejemplo:

```text
Fa0/1
   │
   └── MAC permitida:
       AA:AA:AA:AA:AA:AA
```

Si aparece otra dirección MAC:

```text
Fa0/1
   │
   └── MAC detectada:
       BB:BB:BB:BB:BB:BB
```

el switch puede considerar que se ha producido una **violación de seguridad**.

### 4. ¿Para qué sirve Port Security?
La seguridad de puertos puede utilizarse para:

- Evitar conexiones no autorizadas.
- Limitar el número de dispositivos conectados a un puerto.
- Asociar determinadas direcciones MAC a determinados puertos.
- Detectar cambios inesperados de dispositivos.
- Reducir determinados riesgos de acceso a la red.
- Controlar los dispositivos conectados físicamente al switch.

### 5. Tipos de direcciones MAC utilizadas
Dependiendo del switch y de su configuración, podemos trabajar con diferentes formas de determinar las direcciones permitidas.

#### 5.1. MAC configurada manualmente
El administrador especifica directamente la dirección MAC permitida. Por ejemplo:

```text
Fa0/1
   │
   └── MAC permitida:
       AA:AA:AA:AA:AA:AA
```

Es una opción muy controlada, aunque requiere conocer y configurar previamente las direcciones MAC.

#### 5.2. MAC aprendida dinámicamente
El switch puede aprender la dirección MAC del dispositivo conectado. Por ejemplo:

```text
PC
 │
 ▼
Fa0/1
 │
 ▼
Switch
 │
 └── Aprende MAC
```

Esta opción facilita la configuración, ya que el administrador no tiene que introducir manualmente todas las direcciones. En determinados equipos Cisco existe el concepto de **sticky MAC**, mediante el cual las direcciones aprendidas pueden asociarse a la configuración del puerto.

### 6. Número máximo de direcciones MAC
También podemos establecer cuántas direcciones MAC pueden utilizar un puerto.

Por ejemplo:

```text
Fa0/1
Máximo de MAC permitidas: 1
```

Esto significa que esperamos encontrar un único dispositivo en ese puerto. Si posteriormente aparece una segunda dirección MAC, el switch puede considerar que se ha producido una violación. También podríamos configurar:

```text
Fa0/2
Máximo de MAC permitidas: 2
```

Esto podría ser útil en determinadas situaciones donde esperamos más de un dispositivo.
> El número adecuado depende del diseño de la red y del tipo de dispositivo conectado.

### 7. Violación de seguridad
Una **violación de seguridad** se produce cuando el tráfico recibido no cumple las condiciones configuradas para el puerto. Por ejemplo:

```text
Fa0/1
MAC permitida:
AA:AA:AA:AA:AA:AA

        ↓

Se recibe:
BB:BB:BB:BB:BB:BB

        ↓

VIOLACIÓN DE SEGURIDAD
```

El switch debe decidir qué hacer con ese tráfico. En dispositivos Cisco podemos configurar diferentes modos de actuación.

### 8. Modos de actuación ante una violación de seguridad
En switches Cisco podemos encontrar principalmente:

#### 8.1. Modo Protect
En modo **protect**, el switch descarta las tramas procedentes de direcciones MAC no autorizadas. De forma simplificada:

```text
MAC autorizada
      │
      ▼
   Tráfico
      │
      ▼
   PERMITIDO


MAC no autorizada
      │
      ▼
   Tráfico
      │
      ▼
  DESCARTADO
```

El puerto continúa funcionando. Este modo permite bloquear el tráfico no autorizado sin deshabilitar completamente la interfaz.

### 8.2. Modo Restrict
El modo **restrict** tiene un comportamiento similar al anterior respecto al tráfico no autorizado, pero además permite generar información de diagnóstico. Por ejemplo, puede:

- Contabilizar violaciones.
- Registrar información.
- Generar mensajes de registro.

De forma simplificada:

```text
MAC no autorizada
       │
       ▼
    Tráfico
       │
       ├──────► DESCARTAR
       │
       └──────► REGISTRAR
```

Esto permite al administrador detectar que se están produciendo intentos de acceso no autorizados.

### 8.3. Modo Shutdown
El modo **shutdown** es el comportamiento más restrictivo. Cuando se produce una violación de seguridad, el puerto puede pasar a un estado de error y quedar deshabilitado. Por ejemplo:

```text
MAC no autorizada
       │
       ▼
   VIOLACIÓN
       │
       ▼
     Puerto
    deshabilitado
```

Posteriormente será necesario realizar las acciones correspondientes para recuperar el puerto. Este modo proporciona una respuesta más contundente ante una violación de seguridad del switch.

#### 8.4. Comparación de los modos

| Modo | Tráfico no autorizado | Registro/contador | Puerto |
|------|------------------------|-------------------|--------|
| **Protect** | Se descarta | Limitado | Continúa activo |
| **Restrict** | Se descarta | Sí | Continúa activo |
| **Shutdown** | Se descarta | Sí | Puede quedar deshabilitado |

### 9. Configuración básica en Cisco IOS
La configuración de Port Security se realiza normalmente sobre una interfaz. Por ejemplo:

```text
Switch# configure terminal
Switch(config)# interface fastEthernet 0/1
```

A continuación podemos convertir el puerto en un puerto de acceso:

```text
Switch(config-if)# switchport mode access
```

Después habilitamos Port Security:

```text
Switch(config-if)# switchport port-security
```

A partir de aquí podemos establecer diferentes parámetros.

#### 9.1. Limitar el número de MAC
Por ejemplo:

```text
Switch(config-if)# switchport port-security maximum 1
```

Estamos indicando que el puerto admite como máximo una dirección MAC segura. Podemos representarlo:

```text
Fa0/1
 │
 └── Máximo:
       1 MAC
```

#### 9.2. Configurar una MAC manualmente
También podemos indicar qué dirección MAC está autorizada. Por ejemplo:

```text
Switch(config-if)# switchport port-security mac-address aaaa.bbbb.cccc
```

De esta forma:

```text
Fa0/1
 │
 └── MAC autorizada:
     AAAA.BBBB.CCCC
```

Si otro dispositivo intenta utilizar el puerto, se producirá una violación según la política configurada.

#### 9.3. Sticky MAC
Otra posibilidad es utilizar **sticky MAC**. Por ejemplo:

```text
Switch(config-if)# switchport port-security mac-address sticky
```

El switch puede aprender automáticamente la dirección MAC del dispositivo conectado y asociarla a la configuración de seguridad del puerto. La idea es:

```text
Dispositivo conectado
        │
        ▼
Switch aprende MAC
        │
        ▼
MAC asociada al puerto
        │
        ▼
Se utiliza como MAC segura
```

Este mecanismo facilita la configuración cuando conocemos qué dispositivo debe utilizar inicialmente el puerto.

#### 9.4. Configurar el modo de violación de seguridad
Por ejemplo:

```text
Switch(config-if)# switchport port-security violation restrict
```

También podemos encontrar:

```text
protect
```

o:

```text
shutdown
```

Por ejemplo:

```text
Switch(config-if)# switchport port-security violation shutdown
```

#### 9.5. Comprobar la configuración
Después de configurar la seguridad del puerto debemos comprobar que funciona correctamente. En Cisco podemos utilizar:

```text
show port-security
```

También podemos consultar información de una interfaz concreta:

```text
show port-security interface fastEthernet 0/1
```

Estos comandos permiten comprobar información como:

- Si Port Security está habilitado.
- Número máximo de MAC permitidas.
- Número de MAC seguras aprendidas.
- Número de violaciones.
- Estado del puerto.

### 10. Limitaciones de Port Security
Port Security es una herramienta útil, pero no debe considerarse una solución de seguridad completa. Por ejemplo:

- Una dirección MAC puede ser modificada mediante software.
- Un dispositivo autorizado puede verse comprometido.
- No protege por sí solo frente a todos los ataques de red.
- Debe combinarse con otras medidas de seguridad.

Por tanto:
> **Port Security debe entenderse como una medida de control de acceso a nivel de puerto, no como un sistema de seguridad completo.**

### 11. Actividad UP3.6. Configuración de la seguridad del puerto del conmutador - CE3.f)