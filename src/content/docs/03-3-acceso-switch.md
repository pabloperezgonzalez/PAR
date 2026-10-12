---
title: 🔌 UP3.3. Métodos para acceder al modo de configuración del conmutador - CE3.c)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| c) Se han utilizado distintos métodos para acceder al modo de configuración del conmutador. | Teórico |  % | 

### 1. Introducción
Para administrar un **conmutador de red (switch)** es necesario poder acceder a su sistema de administración y configuración. Los switches gestionables disponen de diferentes mecanismos para realizar esta tarea. Dependiendo del modelo, podemos acceder al dispositivo mediante:

- **Consola**.
- **SSH**.
- **Telnet**.
- **Interfaz web**.

Cada método tiene unas características y unas condiciones de utilización diferentes. En entornos profesionales, es especialmente importante conocer la diferencia entre estos métodos y saber **cuándo utilizar cada uno**, prestando especial atención a la seguridad.

### 2. ¿Qué significa acceder al modo de configuración?
Un switch gestionable dispone de un sistema operativo que permite consultar y modificar su funcionamiento. Por ejemplo, en un switch Cisco podemos encontrar diferentes modos de trabajo:

```text
Modo usuario
     │
     ▼
Modo privilegiado
     │
     ▼
Modo de configuración global
     │
     ├── Configuración de interfaces
     ├── Configuración de VLAN
     └── Configuración de otros parámetros
```

Para realizar determinadas tareas administrativas es necesario acceder al **modo de configuración**.

### 3. Acceso mediante consola
La **consola** es uno de los métodos fundamentales para administrar un switch. Permite acceder directamente al dispositivo mediante una conexión física, normalmente utilizando un **cable de consola** conectado entre un ordenador y el puerto de consola del switch.

```text
┌──────────────┐
│ Ordenador    │
│              │
└──────┬───────┘
       │
       │ Cable de consola
       │
┌──────────────┐
│    Switch    │
│              │
│   CONSOLE    │
└──────────────┘
```

Este método es especialmente importante durante la **configuración inicial** del dispositivo.

#### 3.1. ¿Cuándo se utiliza la consola?
La conexión por consola resulta especialmente útil cuando:

- El switch todavía no tiene configurada una dirección IP.
- No existe conectividad de red.
- Se está realizando la configuración inicial.
- Se ha perdido el acceso remoto.
- Es necesario realizar tareas de recuperación.

Una ventaja importante es que **no depende de la red IP**.

#### 3.2. Acceso desde un ordenador
Para conectarnos por consola necesitamos normalmente:

1. El switch.
2. Un cable de consola.
3. Un ordenador.
4. Un programa de terminal.

En sistemas Windows es habitual utilizar **PuTTY**.

### 4. Acceso mediante SSH
**SSH (Secure Shell)** permite administrar el switch de forma remota mediante una conexión segura. Para utilizar SSH, el switch debe estar previamente configurado con los parámetros necesarios, entre ellos una dirección IP de administración.

```text
┌──────────────┐
│ Administrador│
│     PC       │
└──────┬───────┘
       │
       │ SSH
       │
┌──────────────┐
│    Switch    │
│ 192.168.1.2  │
└──────────────┘
```

El administrador puede conectarse desde otro equipo de la red sin necesidad de estar físicamente junto al switch.

#### 4.1. Ventajas de SSH
SSH es actualmente uno de los métodos preferidos para la administración remota porque:

- Cifra la comunicación.
- Protege las credenciales.
- Permite administrar el dispositivo remotamente.
- Puede utilizarse desde diferentes sistemas operativos.

Por ejemplo:

```bash
ssh admin@192.168.1.2
```

### 5. Acceso mediante Telnet
**Telnet** también permite administrar remotamente un switch. El funcionamiento general es similar al de SSH:

```text
Administrador
      │
      │ Telnet
      │
    Switch
```

Sin embargo, Telnet presenta un problema importante: **La comunicación no está cifrada**. Las credenciales y la información intercambiada pueden viajar por la red sin protección. Por este motivo, **Telnet no se recomienda en redes reales** cuando existe la posibilidad de utilizar SSH.

#### 5.1. SSH vs Telnet

| Característica | SSH | Telnet |
|----------------|-----|--------|
| Acceso remoto | Sí | Sí |
| Cifrado | Sí | No |
| Seguridad | Alta | Baja |
| Uso recomendado | Sí | No, salvo entornos controlados |
| Puerto habitual | 22 | 23 |

### 6. Acceso mediante interfaz web
Algunos switches gestionables disponen de una **interfaz web** que permite administrarlos mediante un navegador.

```text
┌──────────────┐
│ Ordenador    │
│ Navegador    │
└──────┬───────┘
       │
       │ HTTP/HTTPS
       │
       │
┌──────────────┐
│    Switch    │
│ 192.168.1.2  │
└──────────────┘
```

El administrador introduce la dirección IP del switch en el navegador y accede a la interfaz de administración. Por ejemplo:

```text
https://192.168.1.2
```

La interfaz puede permitir configurar:
- Interfaces.
- VLAN.
- Seguridad.
- Direccionamiento IP.
- Usuarios.
- Monitorización.
- Otros parámetros del dispositivo.

#### 6.1. HTTP vs HTTPS
Cuando el switch permite utilizar una interfaz web, es preferible utilizar **HTTPS**.

```text
HTTP
 ↓
Comunicación sin cifrado

HTTPS
 ↓
Comunicación cifrada
```

Por tanto, igual que ocurre con SSH frente a Telnet, debemos priorizar las opciones que proporcionan **comunicaciones seguras**.

#### 7. Comparación de los métodos de acceso

| Método | Acceso físico necesario | Acceso remoto | Seguridad | Uso habitual |
|--------|--------------------------|---------------|-----------|--------------|
| **Consola** | Sí | No | Alta | Configuración inicial y recuperación |
| **SSH** | No | Sí | Alta | Administración remota |
| **Telnet** | No | Sí | Baja | Equipos antiguos o laboratorios |
| **Web/HTTPS** | No | Sí | Alta con HTTPS | Administración mediante navegador |

### 8. Modos de configuración en un switch Cisco
Si trabajamos con switches Cisco, el acceso mediante consola o SSH nos lleva normalmente a una interfaz de línea de comandos denominada **CLI (Command Line Interface)**. Podemos encontrar diferentes niveles.

#### 8.1. User EXEC
Es el modo inicial.

```text
Switch>
```

Permite realizar determinadas consultas, pero tiene un acceso limitado a las funciones administrativas.

#### 8.2. Privileged EXEC
Se accede mediante:

```text
Switch> enable
Switch#
```

El símbolo `#` indica que hemos accedido al modo privilegiado. Desde aquí podemos ejecutar comandos administrativos y acceder al modo de configuración.

#### 8.3. Global Configuration
Para acceder:

```text
Switch# configure terminal
Switch(config)#
```

Este es el modo utilizado para realizar la configuración general del switch. Desde aquí podemos acceder a otros modos específicos.

Por ejemplo:

```text
Switch(config)# interface gigabitEthernet 0/1
Switch(config-if)#
```

En este caso estamos configurando una interfaz concreta.

### 9. Esquema de acceso a la configuración

```text
                ACCESO AL SWITCH
                       │
          ┌────────────┼────────────┐
          │            │            │
       Consola        SSH         Web/HTTPS
          │            │            │
          └────────────┼────────────┘
                       ▼
                    CLI / GUI
                       │
                       ▼
                  Usuario EXEC
                       │
                    enable
                       │
                       ▼
               Privileged EXEC
                       │
              configure terminal
                       │
                       ▼
             Global Configuration
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
          Interface   VLAN      Otros
```

### 10. ¿Qué método utilizar?
La elección del método depende de la situación.

- Configuración inicial ➜ Utilizaremos normalmente **consola** porque el switch puede no disponer todavía de configuración IP.
- Administración habitual ➜ Utilizaremos preferentemente **SSH** porque permite administrar el dispositivo remotamente de forma segura.
- Administración mediante navegador ➜ Podemos utilizar **HTTPS** si el switch dispone de interfaz web.
- Equipos antiguos ➜ Podemos encontrar **Telnet**, aunque debe evitarse en redes reales debido a la falta de cifrado.

### 11. Importancia de la seguridad
El acceso al sistema de administración de un switch debe estar protegido. Un atacante que consiga acceder al modo de configuración podría:

- Cambiar la configuración.
- Deshabilitar puertos.
- Modificar VLAN.
- Cambiar parámetros de red.
- Interrumpir las comunicaciones.
- Crear nuevas cuentas administrativas.

Por ello, debemos utilizar:

- Contraseñas seguras.
- Usuarios individuales.
- SSH en lugar de Telnet.
- HTTPS en lugar de HTTP.
- Control de acceso.
- Actualizaciones del sistema operativo.

### 12. Buenas prácticas
Al administrar un switch se recomienda:

- Utilizar la **consola** para la configuración inicial cuando sea necesario.
- Configurar una dirección IP de administración.
- Habilitar **SSH** para la administración remota.
- Evitar Telnet en redes de producción.
- Utilizar HTTPS en caso de administrar el dispositivo mediante web.
- Proteger el acceso con contraseñas seguras.
- Crear cuentas de administración adecuadas.
- Limitar quién puede acceder al dispositivo.
- Registrar y documentar los métodos de acceso utilizados.

### 13. Caso práctico
Un switch acaba de instalarse en un aula y todavía no tiene configurada ninguna dirección IP. El administrador necesita acceder al dispositivo para realizar la configuración inicial. Una vez configurada la dirección IP de administración, quiere poder administrar el switch desde su ordenador sin tener que desplazarse físicamente hasta él.

> **Analiza la situación planteada e indica qué método de acceso utilizarías inicialmente y qué método utilizarías posteriormente para la administración remota. Explica las ventajas de cada uno y justifica por qué no utilizarías Telnet en una red real.**