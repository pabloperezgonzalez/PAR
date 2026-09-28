---
title: 📡 UP2.4. Direccionamiento IPv4 e IPv6 - CE2.d)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| d) Se ha utilizado el sistema de direccionamiento lógico IP para asignar direcciones de red y máscaras de subred. | Teórico |  20 % | 

### 1. Introducción
En una red de datos, todos los dispositivos deben poder identificarse de forma única para intercambiar información correctamente. Para ello se utiliza el **direccionamiento IP (Internet Protocol)**, un sistema de identificación lógica que permite localizar cada equipo dentro de una red y establecer comunicaciones entre dispositivos situados tanto en la misma red local como en Internet.

A diferencia de la **dirección MAC**, que identifica físicamente la tarjeta de red y viene asignada por el fabricante, la **dirección IP** puede configurarse y modificarse según las necesidades de la red. En este criterio aprenderemos qué es una dirección IP, cómo está formada, qué función desempeña la máscara de subred y cómo se asignan correctamente las direcciones a los dispositivos de una red.

### 2. ¿Qué es una dirección IP?
Una **dirección IP** es un identificador lógico asignado a un dispositivo conectado a una red. Su función es permitir que los datos lleguen al equipo correcto.

Ejemplos:

```text
192.168.1.25
10.0.0.15
172.16.20.8
```

Cada dirección IP debe ser **única dentro de una misma red**. Si dos equipos tienen la misma dirección IP se produce un **conflicto de direcciones**, impidiendo la comunicación.

### 3. IPv4 e IPv6
Actualmente existen dos versiones del protocolo IP.

| Protocolo | Características |
|------------|-----------------|
| **IPv4** | Utiliza direcciones de 32 bits. Es el más utilizado actualmente. |
| **IPv6** | Utiliza direcciones de 128 bits. Diseñado para sustituir a IPv4. |

En este criterio, trabajaremos principalmente con **IPv4**, ya que continúa siendo el protocolo predominante en la mayoría de las redes.

### 4. Estructura de una dirección IPv4
Una dirección IPv4 está formada por **32 bits**, divididos en **cuatro octetos** de 8 bits.

Ejemplo:

```text
192.168.1.25
```

Representación binaria:

```text
11000000.10101000.00000001.00011001
```

Cada octeto puede tomar valores entre **0 y 255**.

### 5. Partes de una dirección IP
Toda dirección IP está formada por dos partes:

- **Identificador de red (Network ID).**
- **Identificador de host (Host ID).**

```text
192.168.1.25
Red ------ Host
```

La separación entre ambas partes viene determinada por la **máscara de subred**.

### 6. ¿Qué es una máscara de subred?
La **máscara de subred** indica qué parte de la dirección IP corresponde a la red y qué parte identifica al dispositivo.

Ejemplo:

```text
IP:       192.168.1.25
Máscara: 255.255.255.0
```

En este caso:

- **192.168.1** identifica la red.
- **25** identifica el equipo.

Todos los dispositivos pertenecientes a la misma red deben compartir la misma parte de red.

### 7. Representación de la máscara
La máscara puede expresarse de dos formas.

#### 7.1. Notación decimal

```text
255.255.255.0
```

#### 7.2. Notación CIDR

```text
/24
```

Otros ejemplos:

| Máscara | CIDR |
|----------|------|
| 255.0.0.0 | /8 |
| 255.255.0.0 | /16 |
| 255.255.255.0 | /24 |
| 255.255.255.128 | /25 |

Actualmente la notación **CIDR** es la más utilizada.

### 8. Clases IPv4 (visión histórica)
Originalmente las direcciones IPv4 se organizaban en clases.

| Clase | Primer octeto | Máscara |
|--------|---------------|----------|
| A | 1 - 126 | /8 |
| B | 128 - 191 | /16 |
| C | 192 - 223 | /24 |

Hoy en día este sistema prácticamente ha desaparecido gracias al uso de **CIDR**, aunque sigue siendo útil conocerlo para comprender la evolución de las redes.

### 9. Direcciones públicas y privadas
Las direcciones IP pueden clasificarse en dos grupos.

#### 9.1. Direcciones públicas
Son únicas en todo Internet. Permiten la comunicación entre redes de todo el mundo. Son asignadas por los proveedores de acceso a Internet.

#### 9.2. Direcciones privadas
Se utilizan únicamente dentro de redes locales. No pueden utilizarse directamente en Internet. Los rangos privados son:

| Rango |
|--------|
| 10.0.0.0/8 |
| 172.16.0.0/12 |
| 192.168.0.0/16 |

La mayoría de hogares y empresas utilizan direcciones privadas.

#### 9.3. Direcciones especiales
Existen algunas direcciones con funciones específicas.

| Dirección | Función |
|------------|---------|
| 127.0.0.1 | Loopback (equipo local). |
| 255.255.255.255 | Broadcast limitado. |
| 169.254.x.x | APIPA (configuración automática cuando falla DHCP). |
| Dirección de red | Identifica una red. |
| Dirección de broadcast | Envía datos a todos los equipos de una red. |

Estas direcciones no pueden asignarse libremente a un equipo.

### 10. Asignación de direcciones IP
Las direcciones IP pueden asignarse de dos formas.

#### 10.1. Configuración estática
El administrador introduce manualmente:

- Dirección IP.
- Máscara.
- Puerta de enlace.
- Servidor DNS.

Se utiliza principalmente en:

- Servidores.
- Routers.
- Switches gestionables.
- Impresoras de red.

#### 10.2. Configuración dinámica (DHCP)
El servidor DHCP asigna automáticamente la configuración IP.

>✅**Ventajas:** Evita errores, simplifica la administración y reduce el tiempo de configuración.

Es el sistema más utilizado en redes empresariales y domésticas.

### 11. Parámetros de configuración IP
Para configurar correctamente un dispositivo suelen definirse los siguientes parámetros.

| Parámetro | Función |
|------------|----------|
| Dirección IP | Identifica el dispositivo. |
| Máscara | Define la red. |
| Puerta de enlace | Permite acceder a otras redes. |
| DNS | Traduce nombres en direcciones IP. |

### 12. Ejemplo de configuración

```text
Dirección IP → 192.168.1.25
Máscara → 255.255.255.0
Puerta de enlace → 192.168.1.1
DNS → 8.8.8.8
```

Con esta configuración el equipo podrá comunicarse con el resto de dispositivos de su red y acceder a Internet.

### 13. Identificación de la red

Supongamos la siguiente configuración.

```text
IP → 192.168.10.35
Máscara → 255.255.255.0
```

La red será:

```text
192.168.10.0
```

Y el equipo será el host número:

```text
35
```

Todos los dispositivos cuya dirección comience por **192.168.10** pertenecerán a la misma red.

### 13. Errores habituales
Los problemas más frecuentes relacionados con el direccionamiento IP son:

- Dos equipos con la misma dirección IP.
- Máscara incorrecta.
- Puerta de enlace mal configurada.
- Servidor DNS incorrecto.
- Dirección IP fuera del rango de la red.
- Configuración DHCP incorrecta.

### 14. Buenas prácticas
Al configurar una red es recomendable:

- Utilizar un plan de direccionamiento.
- Evitar direcciones duplicadas.
- Reservar direcciones estáticas para servidores.
- Utilizar DHCP para equipos cliente.
- Documentar todas las configuraciones.
- Verificar la conectividad tras cada cambio.

### 15. Actividades de repaso
Haciendo todos los cálculos necesarios **a mano**, extrae la siguiente información en cada uno de los casos presentados, indicando:

- La porción de red y la porción de host mediante la notación en binario.
- La dirección de red (binario y decimal).
- La dirección de difusión (binario y decimal).
- El rango de direcciones de host válidas (decimal).
- Cantidad de hosts que puede albergar la red.

|   Nº  | Dirección IP     | Máscara CIDR |
| :---: | :--------------- | :----------: |
| **1** | `192.168.1.75`   |     `/24`    |
| **2** | `192.168.10.125` |     `/25`    |
| **3** | `192.168.20.100` |     `/26`    |
| **4** | `192.168.30.200` |     `/27`    |
| **5** | `192.168.40.150` |     `/28`    |
| **6** | `10.0.15.200`    |     `/20`    |
| **7** | `172.16.45.130`  |     `/22`    |
| **8** | `172.20.100.200` |     `/23`    |
| **9** | `192.168.100.130`|     `/29`    |
| **10** | `10.10.50.70`   |     `/30`    |