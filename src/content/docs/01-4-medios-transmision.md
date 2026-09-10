---
title: 🌐 UP1.4. Medios de transmisión - CE1.b)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| b) Se han diferenciado los distintos medios de transmisión utilizados en las redes. | Teórico |  10 % | 

### 1. Introducción
Para que dos dispositivos puedan intercambiar información es necesario que exista un **medio de transmisión**, es decir, un canal por el que viajen las señales que contienen los datos.

El medio de transmisión constituye uno de los elementos fundamentales de cualquier red, ya que condiciona aspectos tan importantes como la velocidad de transmisión, la distancia máxima entre dispositivos, el coste de la instalación, la seguridad o la resistencia frente a interferencias. Elegir el medio de transmisión adecuado es una de las decisiones más importantes durante el diseño de una infraestructura de red.

### 2. ¿Qué es un medio de transmisión?
Un **medio de transmisión** es el soporte físico o el canal por el que se transmiten los datos desde un dispositivo emisor hasta otro receptor. Dependiendo del tipo de red y de las necesidades de comunicación, la información puede viajar:

- A través de un cable.
- Mediante impulsos luminosos.
- Utilizando ondas electromagnéticas.

Todos los medios de transmisión tienen el mismo objetivo: transportar la información de forma rápida, fiable y segura.

### 3. Clasificación de los medios de transmisión
Los medios de transmisión pueden clasificarse en dos grandes grupos:

```text
                              Medios de transmisión
                                      │
                        ┌─────────────┴─────────────┐
                        │                           │
                        ▼                           ▼
                Medios guiados              Medios no guiados
                 (Cableados)                 (Inalámbricos)
```

### 4. Medios guiados
Los **medios guiados** utilizan un soporte físico para transportar la información. Las señales permanecen confinadas dentro del cable, lo que proporciona una mayor estabilidad y protección frente a interferencias externas. Son los medios más utilizados en redes empresariales y centros de datos.

### 4.1. Cable de par trenzado
Es el medio de transmisión más utilizado en las redes Ethernet actuales. Está formado por varios pares de hilos de cobre trenzados entre sí. El trenzado reduce las interferencias electromagnéticas y mejora la calidad de la transmisión. Existen diferentes tipos de cable de par trenzado:

#####   a) UTP (Unshielded Twisted Pair)
No dispone de apantallamiento. Es el cable más utilizado en redes LAN.

#####   b) STP (Shielded Twisted Pair)
Incluye una malla metálica que protege frente a interferencias. Se utiliza en entornos industriales o con elevada contaminación electromagnética.

#####   c) FTP (Foiled Twisted Pair)
Dispone de una lámina metálica que envuelve el conjunto de pares. Ofrece una protección intermedia entre UTP y STP.

#####   d) SFTP (Shielded Foiled Twisted Pair) 
Protege la señal de interferencias externas usando una malla metálica global y una lámina de aluminio por cada par de cables. Combina la protección de STP y FTP.

<img
  src="/PAR/diagrams/cables_ethernet.jpg"
  alt="Comparativa entre diferentes cables de Ethernet"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

##### Categorías del cable de par trenzado
La velocidad máxima depende de la categoría del cable.

| Categoría | Velocidad máxima | Frecuencia |
|-----------|-----------------:|-----------:|
| Cat 5e | 1 Gbps | 100 MHz |
| Cat 6 | 1 Gbps (10 Gbps hasta 55 m) | 250 MHz |
| Cat 6A | 10 Gbps | 500 MHz |
| Cat 7 | 10 Gbps | 600 MHz |
| Cat 8 | 25-40 Gbps | 2000 MHz |

>✅ **Ventajas:** Bajo coste, fácil instalación, gran disponibilidad y compatible con la mayoría de equipos de red.

>❌ **Inconvenientes:** Distancia limitada (100 metros en Ethernet), sensible a interferencias y menor velocidad que la fibra óptica.

### 4.2. Fibra óptica
La fibra óptica transmite la información mediante **impulsos de luz**, en lugar de señales eléctricas. Está formada por un núcleo de vidrio o plástico extremadamente fino por el que viajan los haces de luz. Actualmente constituye el medio de transmisión de mayor capacidad. Existen diferentes tipos de fibra óptica:

#####   a) Fibra multimodo (MMF)
Permite que varios haces de luz recorran simultáneamente el núcleo. Se utiliza principalmente en:

- Edificios.
- Campus universitarios.
- Centros de datos.

#####   b) Fibra monomodo (SMF)
Permite que un único haz de luz recorra la fibra. Presenta:

- Mayor alcance.
- Mayor velocidad.
- Menor atenuación.

Es la utilizada por los operadores de telecomunicaciones.

>✅ **Ventajas:** Muy alta velocidad, grandes distancias, inmune a interferencias electromagnéticas, mayor seguridad y baja atenuación.

>❌ **Inconvenientes:** Mayor coste, instalación más compleja y requiere herramientas especializadas.

<img
  src="/PAR/diagrams/cables_fibra.jpg"
  alt="Comparativa entre diferentes cables de fibra óptica"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

### 4.3. Cable coaxial
Fue uno de los primeros medios utilizados en redes locales. Está formado por:

- Un conductor central.
- Un aislante.
- Una malla metálica.
- Una cubierta exterior.

Actualmente apenas se utiliza en redes Ethernet, aunque sigue presente en:

- Redes de televisión.
- Instalaciones de cable.
- Sistemas de videovigilancia.

>✅ **Ventajas:** Buena protección frente a interferencias y mayor alcance que el par trenzado.

>❌ **Inconvenientes:** Poco flexible, instalación más compleja y menor velocidad que la fibra.

<img
  src="/PAR/diagrams/cable_coaxial.jpg"
  alt="Estructura del cable coaxial"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

### 4.4. Comparativa de medios guiados

| Medio | Velocidad | Distancia | Coste | Interferencias |
|--------|----------:|----------:|-------:|---------------|
| Par trenzado | Alta | Hasta 100 m | Bajo | Media |
| Fibra óptica | Muy alta | Varios kilómetros | Alto | Muy baja |
| Coaxial | Media | Cientos de metros | Medio | Baja |

### 5. Medios no guiados
Los **medios no guiados** transmiten la información mediante ondas electromagnéticas. No requieren un cable físico entre el emisor y el receptor. Su principal ventaja es la movilidad.

#### 5.1. Wi-Fi
Es la tecnología inalámbrica más utilizada en redes locales. Permite conectar dispositivos mediante un punto de acceso (Access Point). Actualmente las versiones más utilizadas son:

- Wi-Fi 5 (802.11ac)
- Wi-Fi 6 (802.11ax)
- Wi-Fi 6E
- Wi-Fi 7 (802.11be)


>✅ **Ventajas:** Gran movilidad, instalación sencilla, no requiere cableado y fácil ampliación.

>❌ **Inconvenientes:** Sensible a interferencias, menor velocidad que una conexión cableada y mayor riesgo de accesos no autorizados si no se configura correctamente.

#### 5.2. Bluetooth
Bluetooth está diseñado para comunicaciones de corto alcance entre dispositivos personales. Se utiliza principalmente para conectar:

- Auriculares.
- Ratones.
- Teclados.
- Smartphones.
- Smartwatches.

Su consumo energético es muy reducido.

#### 5.3. Redes móviles
Las tecnologías móviles permiten transmitir información a través de la infraestructura de los operadores de telecomunicaciones. Las generaciones más importantes son:

| Generación | Características |
|------------|----------------|
| 3G | Acceso básico a Internet. |
| 4G | Banda ancha móvil. |
| 5G | Muy alta velocidad y baja latencia. |

Las redes 5G están impulsando el desarrollo del Internet de las Cosas y de los vehículos conectados.

#### 5.4. Radio y microondas
Se utilizan para establecer enlaces inalámbricos de larga distancia. Son habituales en:

- Comunicaciones entre edificios.
- Enlaces rurales.
- Redes de operadores.
- Antenas de telefonía móvil.

En muchos casos requieren visión directa entre los puntos de comunicación.

#### 5.5. Satélite
Las comunicaciones por satélite permiten ofrecer conectividad en lugares donde no existe infraestructura terrestre. Su principal aplicación es:

- Zonas rurales.
- Comunicaciones marítimas.
- Aviación.
- Expediciones científicas.

Su principal inconveniente es la elevada latencia.

### 5.6. Comparativa de medios no guiados

| Medio | Alcance | Movilidad | Velocidad |
|--------|---------|-----------|-----------|
| Wi-Fi | Edificio | Alta | Alta |
| Bluetooth | Muy corto | Muy alta | Baja |
| 5G | Muy amplio | Muy alta | Muy alta |
| Radio | Kilómetros | Baja | Alta |
| Satélite | Mundial | Muy alta | Media |

### 6. Conceptos importantes

#### 6.1. Ancho de banda
Es la cantidad máxima de información que puede transmitirse por un medio en un determinado tiempo. Se mide habitualmente en:

- Mbps (Megabits por segundo)
- Gbps (Gigabits por segundo)

Cuanto mayor sea el ancho de banda, mayor cantidad de información podrá transmitirse simultáneamente.

#### 6.2. Latencia
La **latencia** es el tiempo que tarda un dato en viajar desde el origen hasta el destino. Se mide en milisegundos (ms). Una baja latencia resulta esencial para:

- Videojuegos en línea.
- Videoconferencias.
- Aplicaciones industriales.
- Vehículos autónomos.

#### 6.3. Atenuación
La señal pierde intensidad a medida que aumenta la distancia recorrida. Este fenómeno recibe el nombre de **atenuación**. Cada medio presenta una atenuación diferente.La fibra óptica presenta una atenuación mucho menor que el cable de cobre.

#### 6.4. Interferencias
Las señales eléctricas pueden verse afectadas por campos electromagnéticos generados por otros dispositivos. Las interferencias pueden provocar:

- Errores de transmisión.
- Disminución de velocidad.
- Pérdida de paquetes.

Por este motivo el cableado debe instalarse siguiendo determinadas normas de seguridad.

### 7. ¿Qué medio elegir?
La elección depende de diversos factores.

| Necesidad | Medio recomendado |
|-----------|-------------------|
| Oficina | Par trenzado |
| Centro de datos | Fibra óptica |
| Hogar | Wi-Fi + Ethernet |
| Universidad | Fibra + Ethernet |
| Comunicación entre ciudades | Fibra óptica |
| Dispositivos móviles | Wi-Fi o 5G |
| Auriculares inalámbricos | Bluetooth |

No existe un medio perfecto. Cada uno ofrece ventajas para determinadas situaciones.

### 8. Actividad
Indica qué medio de transmisión utilizarías en cada uno de los siguientes casos y justifica tu respuesta.

| Situación | Medio recomendado | Justificación |
|-----------|-------------------|---------------|
| Conexión entre switches de diferentes plantas | | |
| Ordenadores de sobremesa | | |
| Portátiles de los empleados | | |
| Cámaras IP del aparcamiento | | |
| Smartphone de un visitante | | |