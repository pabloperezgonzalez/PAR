---
title: 📡 UP2.5. Configuración de adaptadores de red - CE2.e)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| e) Se han configurado adaptadores de red cableados e inalámbricos bajo distintos sistemas operativos. | Práctico | 10 % | 

### 1. Introducción
Para que un ordenador pueda comunicarse con otros dispositivos de una red es necesario que disponga de un **adaptador de red** correctamente instalado y configurado. El adaptador de red constituye la interfaz entre el sistema operativo y el medio de transmisión, ya sea un cable Ethernet o una conexión inalámbrica Wi-Fi. Sin una configuración adecuada, el equipo no podrá intercambiar información con otros dispositivos ni acceder a los recursos compartidos o a Internet.

En este criterio aprenderemos qué son los adaptadores de red, cómo funcionan, cómo se configuran en distintos sistemas operativos y qué herramientas permiten verificar su correcto funcionamiento. La configuración de los adaptadores de red es una de las tareas más habituales de cualquier administrador de sistemas y redes.

### 2. ¿Qué es un adaptador de red?
Un **adaptador de red** o **tarjeta de red** (*Network Interface Card - NIC*) es el dispositivo que permite a un equipo conectarse a una red de comunicaciones. Su función consiste en transmitir y recibir información utilizando un determinado medio de transmisión. Puede estar integrado en la placa base o instalarse como un dispositivo independiente.

### 3. Funciones de un adaptador de red
Las principales funciones de un adaptador son:

- Conectar el equipo a la red.
- Enviar y recibir tramas de datos.
- Disponer de una dirección MAC única.
- Convertir la información del sistema operativo en señales adecuadas para el medio físico.
- Gestionar la velocidad y el modo de funcionamiento del enlace.

### 4. Tipos de adaptadores de red
Dependiendo del medio de transmisión utilizado, los adaptadores pueden clasificarse en dos grandes grupos.

#### 4.1. Adaptadores cableados
Utilizan un cable Ethernet para conectar el equipo a la red. Son los más utilizados en redes empresariales.

>💡 **Características:** Alta velocidad, baja latencia, gran estabilidad y menor susceptibilidad a interferencias.

#### 4.2. Adaptadores inalámbricos
Utilizan ondas de radio para comunicarse mediante redes Wi-Fi. Se utilizan habitualmente en ordenadores portátiles, tabletas y dispositivos móviles.

>💡 **Características:** Movilidad, instalación sencilla, no requieren cableado y mayor sensibilidad a interferencias.

### 5. Componentes de un adaptador de red
Todo adaptador dispone de varios elementos importantes.

- Dirección MAC.
- Controlador (Driver).
- Firmware.
- Configuración IP.
- Parámetros del enlace.

Todos ellos deben funcionar correctamente para **garantizar la comunicación**.

#### 5.1. La dirección MAC
Cada adaptador posee una **dirección MAC (Media Access Control)** única asignada por el fabricante. Ejemplo:

```text
00:1A:2B:3C:4D:5E
```

La dirección MAC identifica físicamente al dispositivo dentro de una red local. No debe confundirse con la dirección IP, que puede cambiar según la configuración de la red.

#### 5.2. El controlador (Driver)
El **driver** es el software que permite al sistema operativo comunicarse con el hardware del adaptador. Sin un controlador adecuado:

- El adaptador no será reconocido.
- No podrá utilizarse la red.
- Algunas funciones avanzadas estarán deshabilitadas.

Por este motivo, uno de los primeros pasos tras instalar un sistema operativo consiste en comprobar que todos los controladores están correctamente instalados.

#### 5.3. Modos de configuración IP
Un adaptador de red puede configurarse de dos formas principales.

##### Configuración automática (DHCP)
Es el método más utilizado en redes domésticas y empresariales. El equipo obtiene automáticamente:

- Dirección IP.
- Máscara de subred.
- Puerta de enlace.
- Servidores DNS.

##### Configuración manual (Estática)
El administrador configura todos los parámetros manualmente. Se utiliza normalmente en:

- Servidores.
- Impresoras de red.
- Equipos de administración.
- Dispositivos de infraestructura.

#### 5.4. Parámetros de configuración
Los principales parámetros que deben configurarse son:

| Parámetro | Función |
|-----------|---------|
| Dirección IP | Identifica al equipo en la red. |
| Máscara de subred | Determina la red a la que pertenece. |
| Puerta de enlace | Permite acceder a otras redes. |
| Servidor DNS | Traduce nombres de dominio en direcciones IP. |

Estos conceptos fueron estudiados en el RA1 y se desarrollarán con mayor profundidad en el criterio dedicado al direccionamiento IP.

### 6. Configuración en Microsoft Windows
Windows permite configurar los adaptadores desde la interfaz gráfica o mediante línea de comandos.

#### 6.1. Configuración gráfica
Ruta habitual:

```text
Configuración → Red e Internet → Ethernet o Wi-Fi → Cambiar opciones del adaptador → Propiedades → Protocolo IPv4
```

Desde esta ventana es posible:

- Activar DHCP.
- Configurar una dirección IP fija.
- Modificar la máscara.
- Cambiar la puerta de enlace.
- Configurar servidores DNS.

#### 6.2. Herramientas de línea de comandos
Windows incorpora varias herramientas para consultar la configuración de red.

##### ipconfig
Muestra la configuración IP.

```cmd
ipconfig
```

Información mostrada:

- Dirección IP.
- Máscara.
- Puerta de enlace.

##### ipconfig /all
Proporciona información ampliada.

```cmd
ipconfig /all
```

Incluye:

- Dirección MAC.
- DHCP.
- DNS.
- Estado del adaptador.
- Tiempo de concesión DHCP.

##### ping
Comprueba la conectividad con otro dispositivo.

```cmd
ping 192.168.1.1
```

##### tracert
Muestra el recorrido seguido por los paquetes.

```cmd
tracert www.google.es
```

### 7. Configuración en GNU/Linux
Las distribuciones Linux permiten configurar los adaptadores tanto mediante interfaz gráfica como desde la terminal.

#### 7.1. Herramienta ip
Actualmente es la herramienta recomendada. 

Mostrar interfaces:

```bash
ip link
```

Mostrar direcciones IP:

```bash
ip addr
```

Mostrar rutas:

```bash
ip route
```

#### 7.2. Comando hostname
Permite consultar el nombre del equipo.

```bash
hostname
```

#### 7.3. NetworkManager
La mayoría de distribuciones actuales utilizan **NetworkManager** para gestionar las conexiones de red. Permite:

- Activar o desactivar interfaces.
- Configurar IP estática.
- Configurar DHCP.
- Gestionar conexiones Wi-Fi.

#### 7.4. nmcli
Es la herramienta en modo texto de NetworkManager.

Mostrar dispositivos:

```bash
nmcli device status
```

Mostrar conexiones:

```bash
nmcli connection show
```

### 8. Configuración de redes Wi-Fi
En un adaptador inalámbrico es necesario configurar algunos parámetros adicionales. Entre ellos destacan:

- Nombre de la red (SSID).
- Sistema de seguridad.
- Contraseña.
- Banda de frecuencia.
- Dirección IP.

#### 8.1. Parámetros de una red inalámbrica

| Parámetro | Descripción |
|------------|-------------|
| SSID | Nombre de la red Wi-Fi. |
| Seguridad | WPA2 o WPA3. |
| Contraseña | Clave de acceso. |
| Banda | 2,4 GHz, 5 GHz o 6 GHz. |
| Canal | Frecuencia utilizada. |

#### 8.2. Comprobación de la configuración
Una vez configurado el adaptador conviene verificar que todo funciona correctamente. Las comprobaciones más habituales son:

- El adaptador aparece correctamente reconocido.
- Dispone de dirección IP.
- Puede acceder a la puerta de enlace.
- Resuelve nombres mediante DNS.
- Tiene acceso a Internet.

#### 8.3. Diagnóstico de incidencias
Cuando un equipo no dispone de conectividad conviene seguir un procedimiento ordenado.

###### Paso 1
Comprobar que el adaptador está habilitado.

##### Paso 2
Verificar el controlador.

##### Paso 3
Comprobar la dirección IP.

##### Paso 4
Realizar un ping a la puerta de enlace.

##### Paso 5
Comprobar la resolución DNS.

##### Paso 6
Acceder a Internet. Este procedimiento permite localizar rápidamente la mayoría de los problemas de configuración.

### 9. Problemas habituales

| Problema | Posible causa |
|-----------|---------------|
| Sin dirección IP | DHCP no disponible. |
| Dirección APIPA (169.254.x.x) | No se ha obtenido dirección del servidor DHCP. |
| Sin acceso a Internet | Puerta de enlace incorrecta. |
| No resuelve nombres | DNS mal configurado. |
| Adaptador deshabilitado | Configuración incorrecta o fallo del controlador. |
| Velocidad reducida | Cable o negociación del enlace incorrectos. |

### 10. Buenas prácticas
Al configurar adaptadores de red es recomendable:

- Mantener actualizados los controladores.
- Utilizar DHCP cuando sea posible.
- Reservar direcciones estáticas para servidores.
- Utilizar WPA3 o WPA2 en redes inalámbricas.
- Documentar cualquier cambio realizado.
- Verificar la conectividad tras la configuración.

### 11. Actividad UP2.5. Configuración de adaptadores de red - CE2.e)
Crea una cuenta en **Cisco Networking Academy (NetAcad)** para poder descargar e instalar **Cisco Packet Tracer**.
Una vez instalado, crea una pequeña topología formada por **dos ordenadores**. Configura manualmente el adaptador de red de cada equipo asignándole una dirección IPv4 y comprueba que los parámetros se han aplicado correctamente.

> **Importante:** en esta actividad no se evaluará la conectividad entre los equipos. La comprobación de la comunicación entre dispositivos se trabajará posteriormente en otros criterios del RA2.

##### Paso 1. Crear la cuenta de Cisco NetAcad

* Accede a [Cisco Networking Academy](https://www.netacad.com/es).
* Crea una cuenta personal.
* Inicia sesión.
* Descarga e instala **Cisco Packet Tracer** (si no lo tienes instalado en tu ordenador).

##### Paso 2. Crear la topología
En Packet Tracer:

* Añade **dos dispositivos PC** al área de trabajo.
* Identifícalos como `PC1` y `PC2`.
* Conecta cada PC mediante su interfaz de red correspondiente.

##### Paso 3. Configurar el adaptador de red de PC1
Accede a: **PC1 → Desktop → IP Configuration** y configura manualmente:

| Parámetro         | Valor           |
| :---------------- | :-------------- |
| Dirección IPv4    | `192.168.10.10` |
| Máscara de subred | `255.255.255.0` |

No es necesario configurar una puerta de enlace ni servidores DNS para esta actividad.

##### Paso 4. Configurar el adaptador de red de PC2
Realiza el mismo procedimiento en `PC2`:

| Parámetro         | Valor           |
| :---------------- | :-------------- |
| Dirección IPv4    | `192.168.10.20` |
| Máscara de subred | `255.255.255.0` |

##### Paso 5. Comprobar la configuración
Desde cada ordenador, accede a: **Desktop → Command Prompt**

Ejecuta:

```text
ipconfig
```

Comprueba que la dirección IPv4 y la máscara de subred coinciden con los valores configurados anteriormente.

##### Paso 6. Registra los resultados:
| Equipo | IPv4 configurada | IPv4 comprobada | Máscara comprobada |
| :----- | :--------------: | :-------------: | :----------------: |
| PC1    |  `192.168.10.10` |                 |                    |
| PC2    |  `192.168.10.20` |                 |                    |

##### Paso 7. Cuestiones finales
Responde brevemente:

1. ¿Qué función tiene el adaptador de red de un ordenador?
2. ¿Qué diferencia existe entre una dirección IPv4 y una máscara de subred?
3. ¿Qué ocurre si se introduce una dirección IP diferente de la que se pretendía configurar?
4. ¿Por qué es importante comprobar la configuración después de realizarla?
5. ¿Qué comando has utilizado para comprobar la configuración IP del equipo?

##### Paso 8. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules.