---
title: 🌐 UP1.2. Tipos de red y topologías - CE1.c)
---

### RA1. Reconoce la estructura de las redes de datos identificando sus elementos y principios de funcionamiento.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| c) Se han reconocido los distintos tipos de red y sus topologías. | Teórico | 15 % | 

### 1. Introducción
Las **redes de datos** pueden clasificarse de diferentes formas según su tamaño, el ámbito geográfico que abarcan, la tecnología empleada o la forma en que se conectan sus dispositivos. Conocer los distintos tipos de red y las topologías más utilizadas resulta fundamental para cualquier administrador de sistemas y redes, ya que cada una presenta características, ventajas e inconvenientes que la hacen más adecuada para determinados escenarios.

En este criterio, aprenderás a distinguir los principales tipos de redes y las topologías empleadas para interconectar los dispositivos que las componen.

### 2. ¿Qué es un tipo de red?
Un **tipo de red** es una clasificación que permite agrupar las redes según determinadas características, siendo la más habitual el **alcance geográfico**.

Dependiendo del tamaño del área que cubra una red, las tecnologías utilizadas, la velocidad de transmisión o los dispositivos necesarios pueden variar considerablemente. Por ejemplo, no requiere la misma infraestructura una red doméstica que conecta varios ordenadores que la red utilizada para comunicar las sedes de una empresa repartidas por varios países.

### 3. Clasificación de las redes según su alcance

#### 3.1. PAN (Personal Area Network)
Una **PAN** (*Personal Area Network*) es una red de muy pequeño alcance diseñada para conectar los dispositivos personales de un usuario Normalmente cubre una distancia inferior a los 10 metros.

>💡 **Características:** Muy corto alcance, bajo consumo energético, generalmente inalámbrica y de fácil configuración.

>💻 **Tecnologías habituales:** Bluetooth, NFC, USB y Zigbee (en algunos dispositivos).

>👉 **Ejemplos:** Un teléfono móvil conectado a unos auriculares Bluetooth, un smartwatch sincronizado con un smartphone o un ordenador conectado a un teclado y un ratón inalámbricos.

#### 3.2. LAN (Local Area Network)
Una **LAN** (*Local Area Network*) conecta dispositivos dentro de un área reducida, como una vivienda, una oficina, un laboratorio o un centro educativo. Es el tipo de red más habitual en empresas y organizaciones.

>💡 **Características:** Alta velocidad de transmisión, baja latencia, administración propia y coste relativamente bajo.

>💻 **Tecnologías habituales:** Ethernet y Wi-Fi.

>👉 **Ejemplos:** La red informática de un instituto, la red de una oficina o la red doméstica de una vivienda.

#### 3.3. MAN (Metropolitan Area Network)
Una **MAN** (*Metropolitan Area Network*) conecta redes distribuidas dentro de una misma ciudad o área metropolitana. Suelen ser gestionadas por operadores de telecomunicaciones o grandes organizaciones.

>👉 **Ejemplos:** La red municipal de un ayuntamiento, la red que conecta los distintos edificios de una universidad repartidos por una ciudad o la infraestructura de fibra óptica de un operador local.

#### 3.4. WAN (Wide Area Network)
Una **WAN** (*Wide Area Network*) conecta redes situadas en diferentes ciudades, países o incluso continentes. Utiliza enlaces de larga distancia proporcionados normalmente por operadores de telecomunicaciones.

>💡 **Características:** Gran cobertura geográfica, elevado número de dispositivos, coste superior al de una LAN y mayor complejidad de administración.

>👉 **Ejemplos:** La red corporativa de una empresa multinacional, la red bancaria que conecta todas sus oficinas o Internet.

### 4. Comparativa de los tipos de red

| Tipo | Alcance | Ejemplo |
|------|----------|----------|
| PAN | Persona (1-10 m) | Smartphone y auriculares Bluetooth |
| LAN | Edificio | Instituto, empresa, vivienda |
| MAN | Ciudad | Red municipal |
| WAN | País, continente o mundo | Empresa multinacional |

### 5. Clasificación según el medio de transmisión
Las redes también pueden clasificarse según cómo viaja la información.

#### 5.1. Redes cableadas
Utilizan un medio físico para transmitir los datos. Los más habituales son:

- Cable de par trenzado.
- Fibra óptica.
- Cable coaxial.

>✅ **Ventajas:** Mayor velocidad, menor interferencia, mayor estabilidad y mayor seguridad física.

>❌ **Inconvenientes:** Instalación más compleja y menor movilidad.

#### 5.2. Redes inalámbricas
Transmiten la información mediante ondas electromagnéticas. Las tecnologías más utilizadas son:

- Wi-Fi
- Bluetooth
- Redes móviles (4G y 5G)
- Enlaces por radio

>✅ **Ventajas:** Gran movilidad, instalación sencilla y flexibilidad.

>❌ **Inconvenientes:** Posibles interferencias, menor velocidad en determinadas situaciones y mayor exposición a ataques si no se protegen adecuadamente.

### 6. Clasificación según la arquitectura

#### 6.1. Redes cliente-servidor
En este modelo existen uno o varios **servidores** que ofrecen servicios al resto de equipos.

Los clientes solicitan dichos servicios cuando los necesitan, como, por ejemplo:
- Servidor web.
- Servidor de archivos.
- Servidor DNS.
- Servidor DHCP.
- Servidor de bases de datos.
- Servidor de correo electrónico.

>✅ **Ventajas:** Administración centralizada, mayor seguridad, copias de seguridad más sencillas y mejor control de usuarios.

Es el modelo utilizado en prácticamente todas las empresas.

#### 6.2. Redes entre iguales (Peer to Peer)
Todos los equipos pueden actuar simultáneamente como clientes y servidores. No existe un servidor central.

>✅ **Ventajas:** Configuración sencilla y bajo coste.

>❌ **Inconvenientes:** Difícil administración, menor seguridad y escasa escalabilidad.

Actualmente se utilizan principalmente en pequeñas redes domésticas o para aplicaciones específicas.

### 7. ¿Qué es una topología de red?
La **topología** describe la forma en que los dispositivos se conectan entre sí. Es importante distinguir entre:

- **Topología física**, que representa la disposición real del cableado y los dispositivos.
- **Topología lógica**, que describe el recorrido que siguen los datos independientemente de la disposición física.

En este apartado nos centraremos principalmente en las topologías físicas.

### 8. Principales topologías
#### 8.1. Topología en bus 

<figure class="diagram-figure">
  <img src="/PAR/diagrams/topologia-bus.svg" alt="Topología en bus con cable coaxial compartido por 4 PCs" class="diagram-img" style="width:1000px; height:auto;" loading="lazy" />
  <figcaption class="diagram-caption">Todos los PCs comparten el mismo cable, denominado bus. Una rotura en cualquier punto deja toda la red fuera de servicio.</figcaption>
</figure>

>✅ **Ventajas:** Poco cableado, instalación sencilla y bajo coste.

>❌ **Inconvenientes:** Si el cable principal falla, toda la red deja de funcionar, difícil localizar averías y bajo rendimiento cuando aumenta el tráfico.

Actualmente apenas se utiliza.

#### 8.2. Topología en anillo 

<figure class="diagram-figure">
  <img src="/PAR/diagrams/topologia-anillo.svg" alt="Topología en anillo con 4 PCs conectados en círculo" class="diagram-img" style="width:auto; height:750px;" loading="lazy" />
  <figcaption class="diagram-caption">Cada PC se conecta a sus dos vecinos. Los datos viajan en una dirección (o dos en anillos duales).</figcaption>
</figure>

Los datos recorren el anillo hasta llegar a su destino.

>✅ **Ventajas:** Acceso ordenado al medio y ausencia de colisiones en determinadas implementaciones. 

>❌ **Inconvenientes:** Una avería puede afectar a toda la red y escasa flexibilidad.

Hoy en día tiene un uso muy reducido.

#### 8.3. Topología en estrella 

<figure class="diagram-figure">
  <img src="/PAR/diagrams/topologia-estrella.svg" alt="Topología en estrella con switch central y 4 PCs" class="diagram-img" style="width:1000px; height:auto;" loading="lazy" />
  <figcaption class="diagram-caption">Cada PC se conecta directamente al switch. Si un cable falla, solo ese PC pierde conexión.</figcaption>
</figure>

>✅ **Ventajas:** Fácil ampliación, fácil mantenimiento, las averías de un equipo no afectan al resto y alto rendimiento.

>❌ **Inconvenientes:** Dependencia del dispositivo central.

Es la topología utilizada en prácticamente todas las redes LAN modernas.

#### 8.4. Topología en malla 

<figure class="diagram-figure">
  <img src="/PAR/diagrams/topologia-malla.svg" alt="Topología en malla con 4 PCs conectados entre sí" class="diagram-img" style="width:auto; height:750px;" loading="lazy" />
  <figcaption class="diagram-caption">Cada PC tiene conexión directa con todos los demás.</figcaption>
</figure>

>✅ **Ventajas:** Muy alta disponibilidad, gran tolerancia a fallos y redundancia.

>❌ **Inconvenientes:** Elevado coste y configuración compleja.

Se utiliza en redes críticas y en el núcleo de Internet.

### 9. Comparativa de topologías

| Topología | Coste | Tolerancia a fallos | Escalabilidad | Uso actual |
|:-----------:|:------:|:--------------------:|:--------------:|:-----------:|
| Bus | Bajo | Baja | Baja | Muy reducido |
| Anillo | Medio | Baja | Media | Muy reducido |
| Estrella | Medio | Alta | Alta | Muy frecuente |
| Árbol | Medio-Alto | Alta | Muy alta | Muy frecuente |
| Malla | Muy alto | Muy alta | Alta | Redes críticas |

### 10. ¿Qué topologías encontramos actualmente?
En las redes modernas predominan dos topologías:

- **Estrella**, en redes LAN.
- **Malla**, cuando existen varios switches distribuidos por un edificio o campus.

Las topologías en bus y en anillo tienen hoy un interés principalmente histórico, mientras que las topologías en malla se utilizan cuando se requiere una elevada disponibilidad del servicio.

### 11. Caso práctico
Un instituto dispone de:

- Tres aulas de informática.
- Una biblioteca.
- Un departamento de administración.
- Una sala de profesores.
- Un CPD (Centro de Procesamiento de Datos) donde se encuentran los servidores.

Cada aula dispone de un switch conectado mediante fibra óptica al switch principal situado en el CPD.

#### Reflexiona
1. ¿Qué tipo de red utiliza el instituto?
2. ¿Qué topología presenta la red?
3. ¿Qué ocurriría si fallara uno de los switches de un aula?
4. ¿Qué consecuencias tendría la avería del switch principal?