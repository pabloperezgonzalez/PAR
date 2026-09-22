---
title: 📡 UP2.2. Montaje de cables de red Ethernet y consola - CE2.b)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| b) Se han montado cables directos, cruzados y de consola. | Práctico |  10 % | 

### 1. Introducción

Aunque las redes inalámbricas han adquirido una gran importancia en los últimos años, **la mayoría de las infraestructuras profesionales siguen utilizando redes cableadas** debido a su mayor velocidad, estabilidad y seguridad. Para que una red Ethernet funcione correctamente, no basta con disponer de ordenadores, switches o routers. También es imprescindible que el **cableado esté correctamente fabricado**, respetando el orden de los conductores y los estándares establecidos.

En este criterio aprenderemos a identificar los diferentes tipos de cables utilizados en redes Ethernet, conoceremos su utilidad y aprenderemos a montarlos siguiendo las normas **TIA/EIA-568A** y **TIA/EIA-568B**. Esta competencia es fundamental para cualquier administrador de redes, ya que permite instalar, ampliar y reparar infraestructuras de comunicaciones.

### 2. Objetivos del montaje de cables

El montaje correcto del cableado permite:

- Garantizar la comunicación entre dispositivos.
- Reducir errores y pérdidas de transmisión.
- Facilitar el mantenimiento de la red.
- Cumplir los estándares internacionales.
- Obtener el máximo rendimiento de la infraestructura.

### 3. Material necesario

Para fabricar un cable Ethernet se necesitan los siguientes materiales:

- Cable de par trenzado UTP, FTP o STP.
- Conectores RJ-45.
- Crimpadora para RJ-45.
- Pelacables.
- Tijeras o alicates de corte.
- Comprobador (tester) de cableado.

> En el siguiente criterio se estudiará el uso del comprobador de cables para verificar el montaje realizado.

### 4. El cable de par trenzado

El medio más utilizado en redes LAN es el **cable de par trenzado**. Está formado por **8 hilos de cobre**, agrupados en **4 pares trenzados**.

<img
  src="/PAR/diagrams/par-trenzado.jpg"
  alt="Estructura del cable de par trenzado"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

El trenzado de los pares reduce las interferencias electromagnéticas y mejora la calidad de la transmisión.

### 5. Categorías del cable

Las categorías indican las prestaciones del cable.

| Categoría | Velocidad máxima | Uso habitual |
|-----------|-----------------:|--------------|
| Cat 5e | 1 Gbps | Redes domésticas y pequeñas empresas |
| Cat 6 | 1 Gbps (10 Gbps hasta 55 m) | Redes empresariales |
| Cat 6A | 10 Gbps | Empresas y centros de datos |
| Cat 7 | Más de 10 Gbps | Instalaciones especiales |

Actualmente, las instalaciones nuevas suelen realizarse con **Cat 6 o Cat 6A**.

### 6. El conector RJ-45

Las redes Ethernet utilizan el conector **RJ-45**, formado por ocho contactos metálicos.

<img
  src="/PAR/diagrams/conector-rj45.webp"
  alt="Conector RJ-45"
  class="diagram-img"
  style="width:350px; height:auto;"
  loading="lazy"
/>

Cada uno de los ocho pines corresponde a un conductor del cable. El orden de estos conductores debe respetar un estándar.

### 7. Estándares de cableado

Existen dos normas internacionales para ordenar los hilos del cable.

- TIA/EIA-568A
- TIA/EIA-568B

Ambas funcionan exactamente igual. La única diferencia es el orden de algunos pares de cables.

<img
  src="/PAR/diagrams/estandar-rj45.webp"
  alt="Estándares conector RJ-45"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

La norma **568B** es la más utilizada actualmente.

### 8. Tipos de cables Ethernet

Dependiendo del orden de los conductores en sus extremos, los cables Ethernet pueden ser:

- Cable de consola.
- Cable directo.
- Cable cruzado.

Cada uno está diseñado para una finalidad diferente.

#### 8.1. Cable de consola

El **cable de consola** no transporta tráfico de red entre equipos. Su finalidad consiste en permitir la configuración de dispositivos de red mediante un puerto de administración.

<img
  src="/PAR/diagrams/cable-consola.png"
  alt="Cable de consola"
  class="diagram-img"
  style="width:350px; height:auto;"
  loading="lazy"
/>

El cable de consola se **utiliza** para:

- Configurar un router por primera vez.
- Acceder a un switch sin dirección IP.
- Recuperar configuraciones.
- Resolver incidencias.

Dependiendo del fabricante, pueden utilizarse distintos **conectores**. Los más habituales son:

- USB ↔ RJ-45.
- USB ↔ USB-C.
- Serie DB9 ↔ RJ-45 (equipos antiguos).
- USB ↔ Micro USB.

#### 8.2. Cable directo (Straight Through)

Un **cable directo** utiliza el mismo estándar en ambos extremos. Puede ser 568A - 568A ó 568B - 568B.

<img
  src="/PAR/diagrams/cable-directo-rj45.png"
  alt="Cable directo RJ-45"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

El **cable directo** es el cable Ethernet utilizado actualmente en prácticamente todas las instalaciones de red. Tradicionalmente se empleaba para conectar dispositivos diferentes (como un ordenador y un switch), aunque gracias a la tecnología Auto-MDI/MDIX también puede utilizarse para conectar dispositivos del mismo tipo.

#### 8.3. El cable cruzado (Crossover)

Un **cable cruzado** utiliza un estándar diferente en cada extremo. Puede ser 568A - 568B o viceversa.

<img
  src="/PAR/diagrams/cable-cruzado-rj45.jpeg"
  alt="Cable cruzado RJ-45"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

El **cable cruzado** fue necesario durante muchos años para conectar directamente dispositivos del mismo tipo. Actualmente su uso es muy poco frecuente, ya que la mayoría de equipos incorporan la función Auto-MDI/MDIX, que realiza el cruce de señales de forma automática.

##### Comparativa entre cable directo y cable cruzado

| Característica | Cable directo | Cable cruzado |
|----------------|---------------|---------------|
| Estándares en ambos extremos | Igual (T568A-T568A o T568B-T568B) | Diferente (T568A-T568B) |
| Conecta dispositivos | Distintos | Del mismo tipo (tradicionalmente) |
| Uso actual | Muy frecuente | Poco habitual |
| Compatible con Auto-MDI/MDIX | Sí | Sí |

>📝 **Nota:** Aunque en la actualidad casi todas las conexiones Ethernet utilizan cables directos gracias a la tecnología Auto-MDI/MDIX, es importante conocer el funcionamiento del cable cruzado porque sigue formando parte de los fundamentos de las redes Ethernet, aparece en documentación técnica, en certificaciones profesionales (como Cisco CCNA) y puede encontrarse en equipos antiguos.

### 9. Procedimiento para fabricar un cable Ethernet
La fabricación de un cable Ethernet debe seguir siempre una secuencia ordenada.

<iframe width="600" height="800" src="https://www.youtube.com/embed/QMpWkkqX1eM?si=VRQpBYeBW6djTphF" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

#### Paso 1. Cortar el cable
Se corta el cable con la longitud necesaria. Debe dejarse un pequeño margen para facilitar el montaje.

#### Paso 2. Retirar la cubierta exterior
Con ayuda de un pelacables se eliminan aproximadamente **2 o 3 cm** de la cubierta. Es importante no dañar los conductores interiores.

#### Paso 3. Separar los pares
Se desenrollan cuidadosamente los cuatro pares. Debe mantenerse el trenzado lo máximo posible para evitar pérdidas de calidad.

#### Paso 4. Ordenar los conductores

Los hilos se colocan siguiendo la norma elegida. Por ejemplo, el estándar T-568B.

<img
  src="/PAR/diagrams/rj45-pinout.jpg"
  alt="Pinout RJ-45"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

#### Paso 5. Igualar la longitud
 Se cortan todos los conductores para que tengan exactamente la misma longitud.

#### Paso 6. Introducir el conector
Los ocho conductores deben llegar hasta el fondo del RJ-45. La cubierta exterior también debe entrar ligeramente en el conector para mejorar la resistencia mecánica.

#### Paso 7. Crimpar
Se utiliza la crimpadora para fijar definitivamente el conector. Los contactos metálicos perforan el aislamiento y establecen la conexión eléctrica.

#### Paso 8. Verificar el cable
Finalmente se comprueba el funcionamiento mediante un comprobador de cableado. Este procedimiento será estudiado en el siguiente criterio de evaluación.

#### Buenas prácticas durante el montaje

Para obtener un cable de calidad conviene seguir estas recomendaciones:

- No desenrollar excesivamente los pares.
- No doblar el cable de forma brusca.
- No aplastar el cable.
- Utilizar conectores de calidad.
- Respetar el estándar de cableado.
- Verificar siempre el resultado con un tester.

#### Errores habituales

Los errores más frecuentes, que pueden provocar pérdidas de conectividad o limitar la velocidad de la red, durante el montaje son:

- Orden incorrecto de los conductores.
- Pines mal introducidos.
- Longitud desigual de los hilos.
- Cubierta exterior fuera del conector.
- Conductores dañados durante el pelado.
- Mala crimpación.

### 10. Comparativa de los distintos cables

| Tipo de cable | Estándares | Uso principal |
|---------------|------------|---------------|
| Directo | 568A-568A o 568B-568B | Conectar dispositivos diferentes. |
| Cruzado | 568A-568B | Conectar dispositivos iguales (principalmente en equipos antiguos). |
| Consola | Específico del fabricante | Configuración y administración de dispositivos de red. |

### 11. Actividad UP2.2. Montaje de cables de red Ethernet y consola - CE2.b)
En esta actividad aprenderás a **fabricar cables de red Ethernet siguiendo correctamente los estándares de cableado estructurado**. El alumnado deberá realizar individualmente:

- Un **cable de red directo**.
- Un **cable de red cruzado**.

Además, deberá comprobar que ambos cables están correctamente montados.

#### Organización
La actividad se realizará en **parejas o grupos de 3 alumnos/as**. La agrupación permitirá compartir:

- Bobina de cable de red.
- Conectores RJ-45.
- Pelacables o cortadora.
- Crimpadora.

Sin embargo, cada alumno/a deberá realizar de forma individual:
- La identificación de los cables.
- El montaje del cable directo.
- El montaje del cable cruzado.

> **Importante:** aunque el trabajo se realizará por parejas o grupos de 3 para compartir herramientas y material, **la construcción de los cables será individual**. Cada alumno/a deberá entregar y comprobar sus propios cables.

#### Cuestiones finales
Responde individualmente:
1. ¿Qué diferencia existe entre un cable directo y un cable cruzado?
2. ¿Qué normas se utilizan en cada extremo de un cable directo?
3. ¿Qué normas se utilizan en cada extremo de un cable cruzado?
4. ¿Qué conductores se intercambian en un cable cruzado Ethernet tradicional?
5. ¿Qué función tiene el comprobador de cables?
6. ¿Qué problemas puede provocar un orden incorrecto de los conductores?

#### Rúbrica de evaluación
| Criterio                      | 0 puntos                                        | 2 puntos                                          | 4 puntos                                                          | 6 puntos                                                   | 8 puntos                                          | 10 puntos                                                                                   |
| ----------------------------- | ----------------------------------------------- | ------------------------------------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **Montaje del cable directo** | No realiza el cable o el montaje es incorrecto. | Realiza el montaje con numerosos errores.         | Realiza el cable con algunos errores que debe corregir.           | Realiza correctamente el cable con pequeñas imprecisiones. | Realiza correctamente el cable y los conectores.  | Realiza el cable correctamente, con precisión y autonomía.                                  |
| **Montaje del cable cruzado** | No realiza el cable o el montaje es incorrecto. | Confunde las normas o presenta numerosos errores. | Realiza el cable con algunos errores que debe corregir.           | Realiza correctamente el cable con pequeñas imprecisiones. | Aplica correctamente T568A y T568B.               | Realiza el cable correctamente, con precisión y autonomía.                                  |
| **Aplicación de T568A/T568B** | No conoce las normas.                           | Presenta numerosos errores en la distribución.    | Conoce las normas pero necesita ayuda para aplicarlas.            | Aplica correctamente las normas con alguna consulta.       | Aplica correctamente ambas normas.                | Las aplica con total precisión y comprende su finalidad.                                    |
| **Uso de herramientas**       | Utiliza incorrectamente las herramientas.       | Necesita ayuda constante.                         | Utiliza las herramientas con algunas dificultades.                | Utiliza correctamente las herramientas.                    | Trabaja correctamente y con seguridad.            | Utiliza las herramientas con precisión, autonomía y seguridad.                              |
| **Crimpado de conectores**    | Los conectores no funcionan.                    | Presenta varios errores de crimpado.              | Consigue crimpar los conectores después de realizar correcciones. | Los conectores funcionan correctamente.                    | Realiza un crimpado limpio y correcto.            | Realiza un crimpado preciso y profesional.                                                  |
| **Corrección de errores**     | No identifica los errores.                      | Necesita ayuda para localizar el problema.        | Identifica algunos errores.                                       | Identifica y corrige los errores principales.              | Localiza y corrige los errores de forma autónoma. | Diagnostica rápidamente el problema y explica su causa.                                     |
| **Trabajo y organización**    | No respeta las instrucciones.                   | Necesita supervisión constante.                   | Trabaja con cierta organización.                                  | Trabaja correctamente y respeta el material.               | Se organiza bien y coopera con el grupo.          | Trabaja con autonomía, orden y responsabilidad, facilitando el uso compartido del material. |