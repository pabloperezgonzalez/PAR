---
title: 🔌 UP3.7. Actualización del sistema operativo del conmutador - CE3.g)
---

### RA3. Administra conmutadores estableciendo opciones de configuración para su integración en la red.

| Criterio de evaluación | Tipo | Ponderación |
|:-----------|:-----:|:-----:|
| g) Se ha actualizado el sistema operativo del conmutador. | Práctico | 10 % | 

### 1. Introducción
Los conmutadores gestionables disponen de un **sistema operativo** que permite controlar y configurar las diferentes funciones del dispositivo. En los equipos Cisco, este sistema operativo se conoce habitualmente como **Cisco IOS (Internetwork Operating System)**. El sistema operativo proporciona:

- Los comandos de administración.
- Las funciones de switching.
- Las opciones de configuración.
- Los mecanismos de seguridad.
- Las herramientas de diagnóstico.
- El soporte para diferentes protocolos y tecnologías.

Al igual que ocurre con otros sistemas operativos, el software de un switch puede necesitar ser **actualizado a una versión más reciente**.

### 2. ¿Por qué se actualiza el sistema operativo?
La actualización del sistema operativo de un switch puede ser necesaria por diferentes motivos. Entre los más importantes encontramos:

- Corregir errores de versiones anteriores.
- Solucionar vulnerabilidades de seguridad.
- Añadir nuevas funcionalidades.
- Mejorar la estabilidad del dispositivo.
- Mejorar el rendimiento.
- Obtener compatibilidad con nuevas tecnologías.
- Solucionar problemas conocidos.

Por tanto, una actualización no debe realizarse únicamente porque exista una versión nueva.
> **Antes de actualizar un dispositivo de red debemos comprobar que la nueva versión es compatible y que la actualización está justificada.**

### 3. Sistema operativo y configuración
Es importante diferenciar entre el **sistema operativo** y la **configuración** del switch.

```text
              SWITCH
                 │
       ┌─────────┴─────────┐
       │                   │
       ▼                   ▼
     IOS             Configuración
       │                   │
       │                   ├── VLAN
       │                   ├── Puertos
       │                   ├── IP
       │                   └── Seguridad
       │
       └── Sistema
           operativo
```

El IOS proporciona las funciones del switch, mientras que la configuración determina cómo está funcionando ese dispositivo concreto.

### 4. Versiones del sistema operativo
Los fabricantes publican diferentes versiones de sus sistemas operativos. Por ejemplo, un switch podría estar utilizando:

```text
Versión actual
IOS 15.x
```

y existir posteriormente una versión:

```text
Nueva versión
IOS 15.x / versión posterior
```

Antes de instalar una nueva versión debemos comprobar:
- Modelo exacto del switch.
- Versión actual.
- Versión que queremos instalar.
- Memoria disponible.
- Espacio disponible en almacenamiento.
- Compatibilidad del hardware.
- Requisitos de la nueva versión.
- Problemas conocidos.

### 5. Identificar la versión instalada
Antes de realizar una actualización debemos conocer qué versión está utilizando actualmente el dispositivo. En un switch Cisco podemos utilizar:

```text
show version
```

Este comando proporciona información sobre el dispositivo. Por ejemplo, podemos encontrar información relacionada con:

- Modelo.
- Versión de IOS.
- Tiempo desde el último arranque.
- Memoria.
- Interfaces.
- Imagen utilizada durante el arranque.

De forma simplificada:

```text
Switch# show version
```

### 6. Identificar el modelo del switch
No todas las versiones del sistema operativo son compatibles con todos los switches. Por ello, debemos identificar correctamente el modelo. Por ejemplo:

```text
Switch
   │
   ├── Fabricante
   ├── Modelo
   ├── Memoria
   └── Versión IOS
```

No debemos descargar una imagen de software pensando únicamente en que pertenece al mismo fabricante.
> **La imagen del sistema operativo debe ser compatible con el modelo concreto del dispositivo.**

### 7. Imagen del sistema operativo
En muchos dispositivos Cisco, el sistema operativo se distribuye como una **imagen de software**. Esta imagen puede almacenarse en la memoria **flash** del switch. De forma simplificada:

```text
              SWITCH

        ┌─────────────────┐
        │     FLASH       │
        │                 │
        │   IOS image     │
        │                 │
        └────────┬────────┘
                 │
                 ▼
          Sistema operativo
```

La memoria flash permite conservar la imagen incluso después de apagar el dispositivo.

### 8. Comprobar el almacenamiento
Antes de copiar una nueva imagen debemos comprobar que existe espacio suficiente. En Cisco podemos utilizar:

```text
show flash:
```

Este comando permite consultar el contenido y el espacio disponible en la memoria flash. Por ejemplo:

```text
Switch# show flash:
```

Debemos comprobar que la nueva imagen puede almacenarse correctamente.

### 9. Obtener la nueva versión
La nueva imagen del sistema operativo debe obtenerse de una **fuente oficial y confiable**. En un entorno profesional, el administrador debe comprobar:

- Que la imagen corresponde al modelo.
- Que la versión es la adecuada.
- Que procede del fabricante.
- Que cumple los requisitos del dispositivo.
- Que no está dañada.
- Que dispone de la documentación correspondiente.

### 10. Copia de seguridad antes de actualizar
Antes de modificar el sistema operativo es fundamental realizar una **copia de seguridad de la configuración**. Recordemos el criterio anterior:

```text
Running-config
       │
       │ guardar
       ▼
Startup-config
```

Podemos guardar la configuración mediante:

```text
copy running-config startup-config
```

Además, en un entorno profesional es recomendable disponer de una copia externa de la configuración.

Por ejemplo:

```text
        SWITCH
           │
           │ copia de seguridad
           ▼
    Servidor / almacenamiento
```

De esta forma podremos recuperar la configuración si se produce algún problema durante la actualización.

### 11. Planificación de la actualización
Una actualización de un switch debe planificarse previamente. Antes de comenzar debemos conocer:

- Qué dispositivo vamos a actualizar.
- Qué versión tiene actualmente.
- Qué versión queremos instalar.
- Por qué necesitamos actualizarlo.
- Cuándo se realizará la actualización.
- Qué impacto tendrá sobre la red.
- Cuánto tiempo puede durar la intervención.
- Cómo volver a la versión anterior si algo falla.

Por tanto:

```text
Identificar
     ↓
Comprobar compatibilidad
     ↓
Realizar copias de seguridad
     ↓
Planificar intervención
     ↓
Actualizar
     ↓
Comprobar funcionamiento
```

### 12. Transferencia de la imagen
La nueva imagen debe transferirse al switch. Dependiendo del modelo y del entorno, pueden utilizarse diferentes mecanismos de transferencia. Uno de los más habituales en dispositivos Cisco es **TFTP**. De forma simplificada:

```text
        ┌───────────────┐
        │ Servidor TFTP │
        │               │
        │ Nueva imagen  │
        └───────┬───────┘
                │
                │ Red
                ▼
        ┌───────────────┐
        │    Switch     │
        │               │
        │    FLASH      │
        └───────────────┘
```

El objetivo es copiar la nueva imagen al almacenamiento del switch.
> Los métodos disponibles dependen del modelo del dispositivo y de su sistema operativo.

### 13. Ejemplo de transferencia mediante TFTP
En determinados dispositivos Cisco podemos utilizar comandos como:

```text
copy tftp: flash:
```

El switch solicitará información como:

```text
Address or name of remote host?
Source filename?
Destination filename?
```

El administrador deberá indicar:
- Dirección IP del servidor TFTP.
- Nombre de la imagen.
- Nombre de destino.

### 14. Seleccionar la imagen de arranque
Una vez copiada la nueva imagen, debemos comprobar que el switch está preparado para utilizarla durante el siguiente arranque. La configuración relacionada con el arranque puede variar según el dispositivo. En equipos Cisco podemos consultar información relacionada con el arranque mediante:

```text
show boot
```

### 15. Reinicio del switch
La actualización del sistema operativo puede requerir reiniciar el dispositivo. Durante el reinicio:

```text
Switch
  │
  ▼
Reinicio
  │
  ▼
Carga del IOS
  │
  ▼
Carga de la configuración
  │
  ▼
Switch operativo
```

Durante este proceso, los dispositivos conectados al switch pueden perder temporalmente la conectividad. Por este motivo, una actualización debe realizarse durante una **ventana de mantenimiento** cuando sea posible.

### 16. Verificar la actualización
Una vez reiniciado el switch debemos comprobar que la actualización se ha realizado correctamente. Podemos utilizar:

```text
show version
```

y comprobar que aparece la nueva versión.

Por ejemplo:

```text
Antes:
IOS versión A

Después:
IOS versión B
```

Pero no debemos limitar la comprobación a la versión. También debemos comprobar que:

- Las interfaces están funcionando.
- Las VLAN están disponibles.
- Los dispositivos tienen conectividad.
- La configuración se ha conservado.
- Los servicios de red funcionan correctamente.

### 17. Comprobación de las interfaces
Podemos consultar el estado de las interfaces mediante comandos como:

```text
show interfaces status
```

Esto permite comprobar rápidamente el estado de los puertos. También podemos utilizar:

```text
show ip interface brief
```

para obtener información resumida sobre las interfaces.

### 18. Comprobar la conectividad
Después de actualizar el switch es recomendable realizar pruebas de conectividad. Por ejemplo:

```text
PC ───── Switch ───── Router
```

Podemos comprobar:

```text
PC → Switch
PC → Gateway
PC → Otro dispositivo
```

Utilizando herramientas como:

```text
ping
```

De esta forma verificamos que la actualización no ha provocado problemas de conectividad.

### 19. ¿Qué ocurre si la actualización falla?
Una actualización puede fallar por diferentes motivos:

- Imagen incorrecta.
- Falta de espacio.
- Imagen dañada.
- Interrupción durante la transferencia.
- Incompatibilidad.
- Problemas durante el arranque.

Por este motivo debemos disponer de un **plan de recuperación**.

```text
        Actualización
              │
       ┌──────┴──────┐
       │             │
     Éxito          Fallo
       │             │
       ▼             ▼
    Verificar     Recuperar
                  versión
                  anterior
```

### 20. Importancia de disponer de una versión anterior
Siempre que sea posible, es recomendable conservar la imagen anterior hasta comprobar que la nueva versión funciona correctamente.Por ejemplo:

```text
FLASH

├── IOS_anterior
└── IOS_nueva
```

Esto puede facilitar la recuperación si la nueva versión presenta problemas. La disponibilidad de varias imágenes y la forma de seleccionarlas dependerán del dispositivo.

### 21. Actualización y seguridad
Las actualizaciones tienen una relación importante con la **seguridad de la red**. Una versión antigua puede contener vulnerabilidades conocidas. Por ello, mantener actualizado el sistema operativo puede contribuir a:

- Corregir vulnerabilidades.
- Mejorar los mecanismos de seguridad.
- Corregir errores.
- Mantener el soporte del fabricante.

Sin embargo:
> **Actualizar no significa instalar siempre la versión más reciente inmediatamente.**
Debemos comprobar primero su compatibilidad y estabilidad.

### 22. Buenas prácticas
Antes de actualizar un switch es recomendable:

1. Identificar el modelo exacto.
2. Consultar la versión instalada.
3. Comprobar los requisitos de la nueva versión.
4. Descargar la imagen desde una fuente confiable.
5. Comprobar el espacio disponible.
6. Realizar una copia de seguridad de la configuración.
7. Planificar una ventana de mantenimiento.
8. Transferir la nueva imagen.
9. Configurar correctamente el proceso de arranque.
10. Reiniciar el dispositivo cuando sea necesario.
11. Comprobar la versión instalada.
12. Verificar interfaces, VLAN y conectividad.
13. Mantener un plan de recuperación.

### 23. Ejemplo de proceso completo
Podemos resumir una actualización de la siguiente forma:

```text
        IDENTIFICAR SWITCH
               │
               ▼
       show version
               │
               ▼
      Comprobar compatibilidad
               │
               ▼
      Hacer copia de seguridad
               │
               ▼
       Comprobar memoria FLASH
               │
               ▼
       Obtener nueva imagen
               │
               ▼
       Copiar imagen al switch
               │
               ▼
       Configurar arranque
               │
               ▼
           Reiniciar
               │
               ▼
       Comprobar nueva versión
               │
               ▼
       Comprobar configuración
               │
               ▼
       Comprobar conectividad
```

### 24. Actividad UP3.7. Actualización del sistema operativo del conmutador - CE3.g)
Partiendo de la red configurada en la actividad del criterio CE3.f), utiliza Cisco Packet Tracer para consultar la versión del sistema operativo de un switch, localizar una imagen IOS compatible en un servidor TFTP y realizar el procedimiento de actualización, comprobando posteriormente la versión instalada.

#### Paso 1. Recuperar el escenario anterior
Abre el archivo de la actividad anterior finalizada. Debes conservar:

- `SW-01` y `SW-02`.
- `PC01-NombreApellido` y `PC02-NombreApellido`.
- `LAP01-NombreApellido` y `LAP02-NombreApellido`.
- Las conexiones y direcciones IP anteriores.
- La configuración de seguridad de puertos realizada en `SW-01`.

No elimines ni reconstruyas la topología. Durante esta actividad añadirás temporalmente un servidor TFTP para transferir la imagen del sistema operativo.

#### Paso 2. Consultar la versión instalada
Accede a la CLI de `SW-01` y ejecuta:

```text
enable
show version
```

Anota la siguiente información:

| Dato | Resultado |
|---|---|
| Modelo del switch | |
| Versión IOS instalada | |
| Imagen IOS utilizada | |
| Tiempo de funcionamiento | |

A continuación, consulta el contenido de la memoria flash:

```text
show flash:
```

Anota el nombre de la imagen IOS instalada y comprueba el espacio disponible que muestre el dispositivo.

#### Paso 3. Añadir un servidor TFTP
Añade un dispositivo **Server-PT** al escenario y asígnale el nombre `SRV-TFTP`. Conéctalo a un puerto Ethernet libre de `SW-01` mediante un cable de cobre directo. Configura su dirección IP desde **Desktop → IP Configuration**:

| Parámetro | Valor |
|---|---|
| Dirección IP | `192.168.10.100` |
| Máscara | `255.255.255.0` |
| Puerta de enlace | No necesaria en esta práctica |

Para que el switch pueda comunicarse con el servidor, configura una dirección de gestión en la interfaz VLAN 1 de `SW-01`:

```text
enable
configure terminal
interface vlan 1
ip address 192.168.10.2 255.255.255.0
no shutdown
end
```

Comprueba que la interfaz VLAN 1 está activa:

```text
show ip interface brief
```

#### Paso 4. Preparar la imagen IOS
Abre `SRV-TFTP` y accede a **Services → TFTP**.

1. Activa el servicio TFTP.
2. Comprueba si el servidor dispone de alguna imagen IOS compatible con el modelo de switch.
3. Anota el nombre exacto del archivo que vas a utilizar.
4. Comprueba que la imagen corresponde al modelo y que el switch dispone de espacio suficiente.

No inventes el nombre de la imagen ni utilices un archivo de otro modelo. Si el servidor no incluye ninguna imagen compatible, consulta si tu versión de Packet Tracer permite añadir una imagen IOS de ejemplo. Si no lo permite, documenta esta limitación y realiza el procedimiento hasta la fase de preparación, sin eliminar ni sobrescribir la imagen instalada.

#### Paso 5. Comprobar la comunicación con el servidor
Desde la CLI de `SW-01`, ejecuta:

```text
ping 192.168.10.100
```

Si no recibes respuesta, revisa la dirección IP del servidor, la interfaz VLAN 1 y la conexión física. No continúes con la transferencia hasta que el switch pueda comunicarse con el servidor TFTP.

#### Paso 6. Transferir la imagen IOS
Cuando tengas disponible una imagen compatible, utiliza el comando:

```text
copy tftp: flash:
```

Sigue las preguntas que muestre la CLI:
- Dirección IP del servidor TFTP: `192.168.10.100`.
- Nombre del archivo de origen: el nombre exacto de la imagen disponible.
- Nombre del archivo de destino: acepta el nombre propuesto si es correcto.

Espera a que finalice la transferencia. Después, comprueba el contenido de la memoria flash:

```text
show flash:
```

Verifica que la nueva imagen aparece en el listado y que la transferencia ha finalizado correctamente.

#### Paso 7. Seleccionar la imagen y reiniciar
Si la versión simulada del switch permite seleccionar la imagen de arranque, configura la imagen nueva mediante el comando apropiado para ese modelo. En los modelos compatibles puede utilizarse una instrucción de este tipo:

```text
configure terminal
boot system flash:/NOMBRE-IMAGEN.bin
end
```

Sustituye `NOMBRE-IMAGEN.bin` por el nombre real del archivo y comprueba que la sintaxis es compatible con el switch utilizado. Antes de reiniciar, guarda la configuración:

```text
copy running-config startup-config
```

Si el procedimiento de actualización está disponible y has comprobado que la imagen es válida, reinicia el switch:

```text
reload
```

Confirma el reinicio cuando te lo solicite.

#### Paso 8. Verificar el resultado
Cuando el switch vuelva a estar operativo, ejecuta:

```text
show version
show flash:
```

Completa la tabla:
| Comprobación | Antes de la actualización | Después de la actualización |
|---|---|---|
| Versión IOS | | |
| Imagen de arranque | | |
| Imagen disponible en flash | | |
| Switch operativo | | |

Si Packet Tracer permite completar la actualización, comprueba que la nueva versión o imagen está seleccionada y que el switch vuelve a funcionar. Si la versión de Packet Tracer no permite completar el cambio de IOS, entrega las evidencias de las comprobaciones y explica en qué fase se encuentra la limitación.

#### Paso 9. Entrega
La entrega será individual, en formato PDF y se realizará a través de Aules. El documento debe contener todas las capturas de pantalla necesarias para demostrar que se ha realizado el procedimiento correctamente. Recordad incluir:

- Captura de `show version` antes de la actualización.
- Captura de `show flash:` antes y después de la transferencia.
- Captura del servidor TFTP con el archivo disponible.
- Captura de `show version` después del reinicio, si se ha podido completar.
- Una explicación del procedimiento y de las dificultades encontradas.