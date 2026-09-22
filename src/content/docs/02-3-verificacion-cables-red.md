---
title: 📡 UP2.3. Verificación y certificación del cableado - CE2.c)
---

### RA2. Integra ordenadores y periféricos en redes cableadas e inalámbricas, evaluando su funcionamiento y prestaciones.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| c) Se han utilizado comprobadores para verificar la conectividad de distintos tipos de cables. | Práctico | 5 % | 

### 1. Introducción
Una vez fabricado un cable de red, **no debe utilizarse directamente en una instalación** sin comprobar previamente que funciona correctamente. Durante el proceso de montaje pueden producirse errores como un orden incorrecto de los conductores, conectores mal crimpados, cortes internos o cortocircuitos. Estos fallos pueden impedir completamente la comunicación o reducir considerablemente el rendimiento de la red.

Por este motivo, los técnicos utilizan **comprobadores de cableado** (*Cable Testers*), instrumentos que permiten verificar rápida y fácilmente que un cable cumple las especificaciones necesarias para su correcto funcionamiento. En este criterio aprenderemos a utilizar los comprobadores de cableado, interpretar sus resultados y detectar los fallos más habituales que pueden aparecer durante la fabricación de cables Ethernet.

### 2. ¿Qué es un comprobador de cableado?
Un **comprobador de cableado** (Cable Tester) es un dispositivo electrónico diseñado para verificar el correcto funcionamiento de un cable de comunicaciones. Su función principal consiste en comprobar que cada conductor del cable está conectado correctamente entre ambos extremos. Además, algunos modelos avanzados permiten detectar:

- Cortocircuitos.
- Conductores cortados.
- Conductores intercambiados.
- Pares invertidos.
- Longitud aproximada del cable.
- Calidad del enlace.
- Distancia hasta el punto donde se encuentra una avería.

### 3. ¿Por qué es importante comprobar un cable?
Un cable aparentemente bien construido puede presentar errores internos que no son visibles a simple vista. Comprobar el cable antes de instalarlo permite:

- Detectar errores de montaje.
- Evitar problemas de conectividad.
- Reducir tiempos de reparación.
- Garantizar el funcionamiento de la instalación.
- Asegurar el máximo rendimiento de la red.

En instalaciones profesionales, **todos los cables deben verificarse antes de ponerse en servicio**.

### 4. Tipos de comprobadores
Existen diferentes tipos de comprobadores según el nivel de precisión requerido.

#### 4.1. Comprobadores básicos
Son los más utilizados en los laboratorios de formación. Son económicos y fáciles de utilizar. Permiten comprobar:

- Continuidad.
- Orden de los conductores.
- Cortocircuitos.
- Circuitos abiertos.
- Cruces de pares.

#### 4.2. Certificadores de cableado
Se emplean en instalaciones profesionales. Además de comprobar la continuidad, verifican que el cable cumple las especificaciones exigidas por una determinada categoría (Cat 5e, Cat 6, Cat 6A, etc.). Analizan aspectos como:

- Atenuación.
- Diafonía (NEXT).
- Pérdidas de retorno.
- Impedancia.
- Longitud exacta.

Estos equipos permiten certificar una instalación conforme a las normas internacionales.

#### 4.3. Reflectómetros (TDR)
Los equipos **TDR (Time Domain Reflectometer)** permiten localizar averías dentro de un cable. Son muy utilizados en el mantenimiento de grandes instalaciones. Calculan la distancia aproximada hasta:

- Un corte.
- Un cortocircuito.
- Una mala conexión.

### 5. Partes de un comprobador básico
La mayoría de comprobadores Ethernet están formados por dos módulos.

<img
  src="/PAR/diagrams/tester.png"
  alt="Comprobador básico"
  class="diagram-img"
  style="display: block; margin: 0 auto;"
  loading="lazy"
/>

- **Unidad principal:** envía las señales de prueba.
- **Unidad remota:** recibe las señales y devuelve el resultado.

Este sistema permite comprobar cables instalados entre diferentes habitaciones o armarios de comunicaciones.

### 6. Funcionamiento del comprobador
El comprobador envía una señal eléctrica por cada uno de los ocho conductores del cable. 
Si todos los conductores llegan correctamente al otro extremo, el equipo indica que el cable es correcto.
En caso contrario, el comprobador mostrará el tipo de error detectado.

#### 6.1. Comprobación de un cable directo

En un cable directo, ambos extremos siguen el mismo estándar. 
El comprobador mostrará una correspondencia directa entre los ocho pines.

```text
1 → 1
2 → 2
3 → 3
4 → 4
5 → 5
6 → 6
7 → 7
8 → 8
```
#### 6.2. Comprobación de un cable cruzado

En un cable cruzado, algunos conductores aparecen intercambiados de forma intencionada.
El comprobador mostrará una secuencia similar a la siguiente.

```text
1 → 3
2 → 6
3 → 1
6 → 2
4 → 4
5 → 5
7 → 7
8 → 8
```

### 7. Errores más frecuentes
Durante el montaje de un cable pueden producirse diversos errores.

#### 7.1. Circuito abierto
Uno de los conductores está roto o no llega al conector.

```text
1 → 1
2 → 2
3 → X
```
>👉**Consecuencias:** El cable no funciona correctamente y puede impedir completamente la comunicación.

#### 7.2. Cortocircuito
Dos conductores entran en contacto.

```text
2 ↔ 3
```
>👉**Consecuencias:** La comunicación falla y puede provocar errores intermitentes.

#### 7.3. Conductores intercambiados
Suele producirse por un error al ordenar los colores antes del crimpado. Dos hilos están conectados en posiciones incorrectas.

```text
1 → 2
2 → 1
```
>👉**Consecuencias:** La comunicación no funciona.

#### 7.4. Pares invertidos

Los conductores mantienen la continuidad pero los pares están mal organizados. 

>👉**Consecuencias:** Este error puede permitir cierta conectividad, pero reduce el rendimiento de la red y aumenta las interferencias.

#### 7.5. Mala crimpación
El conector RJ-45 no hace buen contacto con alguno de los conductores. 

>👉**Consecuencias:** Cortes intermitentes, reducción de velocidad y desconexiones.

### 8. Procedimiento para comprobar un cable
La comprobación de un cable Ethernet debe seguir una secuencia ordenada.

#### 8.1. Inspección visual
Antes de utilizar el comprobador conviene revisar:

- Estado del cable.
- Conectores.
- Orden de los colores.
- Posibles daños físicos.

#### 8.2. Conectar el cable
Un extremo del cable se conecta a la unidad principal y el otro a la unidad remota.

```text
Tester ───────── Cable ───────── Remoto
```

#### 8.3. Iniciar la prueba
Se pulsa el botón de comprobación. El comprobador enviará automáticamente las señales de prueba.

#### 8.4. Interpretar el resultado
Se comprueba que todos los pines aparecen correctamente conectados. Si existe algún error, deberá corregirse antes de utilizar el cable.

#### 8.5. Interpretación de resultados

| Resultado | Interpretación |
|------------|----------------|
| 1→1, 2→2...8→8 | Cable directo correcto. |
| 1→3, 2→6... | Cable cruzado correcto. |
| X | Conductor abierto. |
| Dos pines iguales | Cortocircuito. |
| Orden incorrecto | Conductores intercambiados. |

### 9. Actividad UP2.3. Verificación y certificación del cableado - CE2.c)
En esta actividad aprenderás a utilizar un **comprobador de cables de red** para verificar el correcto funcionamiento de cables Ethernet. Deberás comprobar individualmente:

* Tu **cable directo**.
* Tu **cable cruzado**.

Además, tendrás que interpretar la información proporcionada por el comprobador y detectar posibles errores en el cableado.

#### Organización
* El alumnado trabajará en **parejas o grupos de 3 personas**.
* Los grupos compartirán el material disponible.
* **La realización de las comprobaciones será individual.**
* Cada alumno/a deberá comprobar personalmente los dos cables y registrar sus resultados.
* El material compartido deberá utilizarse de forma ordenada y responsable.

> **Importante:** trabajar en grupo significa compartir herramientas, pero no que un compañero/a realice las comprobaciones por los demás.

#### Registro de resultados
Cada alumno/a deberá completar individualmente la siguiente tabla:

| Cable   | Resultado del comprobador | ¿Correcto? | Incidencias detectadas |
| :------ | :------------------------ | :--------: | :--------------------- |
| Directo |                           |            |                        |
| Cruzado |                           |            |                        |

#### Cuestiones finales
Responde individualmente:

1. ¿Para qué sirve un comprobador de cables de red?
2. ¿Qué diferencia existe entre el resultado de comprobar un cable directo y uno cruzado?
3. ¿Qué significa que uno de los pines no presente continuidad?
4. ¿Qué indica que dos pines aparezcan intercambiados?
5. ¿Por qué es importante comprobar un cable antes de utilizarlo en una red?

#### Rúbrica de evaluación
| Criterio                           |                   0                  |                        2                        |                     4                     |                          6                          |                              8                             |                                                         10                                                         |
| :--------------------------------- | :----------------------------------: | :---------------------------------------------: | :---------------------------------------: | :-------------------------------------------------: | :--------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------: |
| **Uso del comprobador**            |          No sabe utilizarlo.         | Necesita realizar prácticamente todo con ayuda. |   Lo utiliza con bastantes indicaciones.  |      Lo utiliza correctamente con alguna ayuda.     |          Lo utiliza correctamente y con autonomía.         |                                     Lo utiliza con total autonomía y precisión.                                    |
| **Comprobación del cable directo** |         No realiza la prueba.        |        Realiza la prueba incorrectamente.       | Realiza parte de la prueba correctamente. |  Realiza correctamente la prueba con alguna ayuda.  | Realiza la prueba correctamente e interpreta el resultado. |                                 Realiza e interpreta la prueba con total autonomía.                                |
| **Comprobación del cable cruzado** |         No realiza la prueba.        |        Realiza la prueba incorrectamente.       | Realiza parte de la prueba correctamente. |  Realiza correctamente la prueba con alguna ayuda.  |      Realiza e interpreta correctamente el resultado.      |                                 Realiza e interpreta la prueba con total autonomía.                                |
| **Interpretación de resultados**   |     No interpreta los resultados.    |        No identifica los errores básicos.       |   Identifica algún resultado con ayuda.   | Interpreta correctamente los resultados habituales. |   Identifica e interpreta correctamente las incidencias.   |                       Interpreta con precisión los resultados y explica las posibles causas.                       |
| **Detección de errores**           |          No detecta errores.         |        No consigue localizar el problema.       |     Detecta el error con mucha ayuda.     |     Detecta errores habituales con alguna ayuda.    |        Detecta y explica correctamente los errores.        |                             Detecta, explica y propone una solución de forma autónoma.                             |
| **Registro de resultados**         |      No registra los resultados.     |          El registro es muy incompleto.         |     Registra parte de los resultados.     |          Registra correctamente la mayoría.         |                Registro completo y ordenado.               |                               Registro completo, preciso y perfectamente organizado.                               |
| **Autonomía individual**           |       No realiza las acciones.       |    Depende constantemente de sus compañeros.    |         Necesita ayuda frecuente.         |            Trabaja con cierta autonomía.            |        Realiza las comprobaciones de forma autónoma.       | Trabaja de forma completamente autónoma y ayuda a organizar el trabajo del grupo sin realizar las tareas de otros. |
| **Uso y cuidado del material**     | Utiliza incorrectamente el material. |         Necesita supervisión constante.         |   Comete algunos errores de utilización.  |          Utiliza correctamente el material.         |  Utiliza el material correctamente y lo conserva ordenado. |                             Utiliza, cuida y organiza el material de forma responsable.                            |