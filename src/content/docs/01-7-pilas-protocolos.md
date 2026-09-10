---
title: 🌐 UP1.7. Funcionamiento de las pilas de protocolos en las distintas arquitecturas de red - CE1.f)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| f) Se ha descrito el funcionamiento de las pilas de protocolos en las distintas arquitecturas de red. | Teórico | 20 % | 

### 1. Introducción
En el criterio anterior hemos estudiado que un **protocolo de comunicación** es un conjunto de normas que permite el intercambio de información entre dispositivos. Sin embargo, una comunicación en una red no depende de un único protocolo, sino de la colaboración de varios protocolos que trabajan de forma coordinada.

Este conjunto organizado de protocolos recibe el nombre de **pila de protocolos** (*protocol stack*). Cada protocolo desempeña una función concreta y se sitúa en una determinada capa de la arquitectura de red. La combinación de todos ellos permite que aplicaciones desarrolladas por distintos fabricantes puedan comunicarse de forma transparente a través de cualquier red.

Comprender el funcionamiento de las pilas de protocolos resulta fundamental para cualquier administrador de redes, ya que facilita el diagnóstico de incidencias, la configuración de dispositivos y el análisis del tráfico de red.

### 2. ¿Qué es una pila de protocolos?
Una **pila de protocolos** es el conjunto de protocolos organizados en diferentes capas que colaboran para hacer posible una comunicación entre dispositivos. Cada protocolo realiza una tarea específica y utiliza los servicios proporcionados por la capa inferior mientras ofrece servicios a la capa superior.

Cuando una aplicación envía información, los datos atraviesan todas las capas de la pila hasta llegar al medio físico. En el equipo receptor ocurre el proceso inverso.

### 3. ¿Por qué se utilizan pilas de protocolos?
Dividir la comunicación en capas aporta numerosas ventajas.

Entre ellas destacan:

- Facilita el diseño de nuevos protocolos.
- Permite sustituir tecnologías sin modificar toda la red.
- Simplifica la resolución de problemas.
- Favorece la interoperabilidad entre fabricantes.
- Hace posible la evolución independiente de cada capa.

Por ejemplo, una empresa puede sustituir el cableado de cobre por fibra óptica sin necesidad de modificar el navegador web ni el servidor de correo electrónico.

### 4. El principio de comunicación entre capas
Cada capa de la arquitectura únicamente se comunica con:

- La capa inmediatamente superior.
- La capa inmediatamente inferior.
- Su capa equivalente en el equipo remoto.

<img
  src="/PAR/diagrams/pila-protocolos.jpg"
  alt="Pila de protocolos"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

Aunque físicamente los datos atraviesan todas las capas, cada protocolo interpreta únicamente la información correspondiente a su propio nivel.

### 5. El proceso de encapsulamiento
Cuando una aplicación envía información, cada capa añade información de control necesaria para realizar su función. Este proceso recibe el nombre de **encapsulamiento**.

#### Paso 1. La aplicación genera los datos
Supongamos que un usuario accede a una página web. La aplicación genera el mensaje que desea enviar.

```text
Datos
```

#### Paso 2. La capa de transporte añade su cabecera
Protocolos como TCP o UDP incorporan información relacionada con:

- Puertos.
- Control de errores.
- Orden de los datos.

```text
Cabecera TCP
      +
    Datos
```

El resultado recibe el nombre de **segmento** (en TCP).

#### Paso 3. La capa de red añade una nueva cabecera
El protocolo IP incorpora:

- Dirección IP origen.
- Dirección IP destino.

```text
Cabecera IP
      +
Cabecera TCP
      +
    Datos
```

Ahora la información constituye un **paquete IP**.

#### Paso 4. La capa de enlace crea una trama
Ethernet o Wi-Fi añaden:

- Dirección MAC origen.
- Dirección MAC destino.
- Información para detectar errores.

```text
Cabecera Ethernet
        +
Cabecera IP
        +
Cabecera TCP
        +
      Datos
```

El resultado recibe el nombre de **trama**.

#### Paso 5. La capa física transmite los bits
Finalmente, la trama se convierte en una secuencia de bits.

```text
101010101001001001010...
```

Estos bits viajan por:

- Cable UTP.
- Fibra óptica.
- Wi-Fi.

### 6. El proceso de desencapsulamiento
Cuando la información llega al dispositivo de destino, ocurre el proceso contrario. Cada capa elimina la información que había añadido su equivalente en el equipo emisor.

```text
Bits
 ↓
Trama Ethernet
 ↓
Paquete IP
 ↓
Segmento TCP
 ↓
Datos de la aplicación
```

Este proceso recibe el nombre de **desencapsulamiento** (*decapsulation*).

### 7. Un ejemplo completo
Supongamos que un alumno abre el navegador y accede a:

```text
https://portal.edu.gva.es/aules
```

Durante esta operación intervienen numerosos protocolos.

| Capa | Protocolo | Función |
|-------|-----------|---------|
| Aplicación | HTTPS | Solicita la página web. |
| Transporte | TCP | Garantiza la entrega correcta. |
| Red | IP | Envía los paquetes hasta el servidor. |
| Enlace | Ethernet o Wi-Fi | Transmite las tramas dentro de la red local. |
| Física | Cable o radio | Envía los bits. |

El usuario únicamente observa la página web, pero realmente están colaborando varios protocolos simultáneamente.

### 8. Relación entre ambas pilas

| Modelo OSI | Modelo TCP/IP | Ejemplos |
|-------------|---------------|----------|
| Aplicación | Aplicación | HTTP, HTTPS, FTP, DNS |
| Presentación | Aplicación | Cifrado, codificación |
| Sesión | Aplicación | Gestión de sesiones |
| Transporte | Transporte | TCP, UDP |
| Red | Internet | IP, ICMP |
| Enlace | Acceso a la red | Ethernet, Wi-Fi |
| Física | Acceso a la red | Cable, fibra, radio |

El modelo TCP/IP agrupa varias funciones del modelo OSI en una misma capa.

### 9. Unidad de datos en cada capa
Cada capa trabaja con una unidad de información diferente.

| Capa | Unidad de datos |
|-------|-----------------|
| Aplicación | Datos |
| Transporte | Segmento (TCP) o datagrama (UDP) |
| Red | Paquete |
| Enlace | Trama |
| Física | Bits |

Conocer esta terminología resulta muy útil al analizar capturas de tráfico o utilizar herramientas como **Wireshark**.

### 10. Caso práctico
Una empresa detecta que los usuarios no pueden acceder a una aplicación web alojada en un servidor remoto.

Durante el proceso de diagnóstico se comprueba que el cableado funciona correctamente, los switches están operativos y existe conectividad entre las distintas redes. Sin embargo, el navegador continúa mostrando un error al intentar acceder al servicio. El administrador de redes debe analizar el recorrido que sigue la información a través de la pila de protocolos para localizar en qué capa puede encontrarse el problema y determinar qué protocolos intervienen durante la comunicación.

> **Analiza el funcionamiento de la pila de protocolos durante el acceso a la aplicación web e identifica cómo participa cada capa en el proceso de encapsulamiento y desencapsulamiento de la información.**