---
title: "Puerto USB Conmutable"
description: "Aprende sobre el sistema de conmutación USB de hardware y software dual en el Openterface Mini-KVM. Comprende los cuatro estados operativos, las pautas de seguridad y las futuras capacidades de acceso remoto."
keywords: "conmutación USB, conmutador KVM, conmutador de hardware, conmutador de software, control de puerto USB, KVM sobre USB, KVM sobre IP, acceso remoto, gestión de dispositivos USB, periféricos de ordenador, gestión de energía USB"
---

# **Guía de Conmutación de Puerto USB** | Openterface Mini-KVM

El dispositivo mini-KVM tiene un solo puerto USB-A 2.0 que puede **conectarse a** el ordenador anfitrión o al dispositivo objetivo, pero **nunca a ambos a la vez**. 

El control proviene de dos interruptores:

- **Interruptor de Hardware**: Un interruptor físico de dos posiciones en el dispositivo ![Toggle Switch](https://assets.openterface.com/images/shell-icons/toggle-h-t.svg#only-light){:style="height:20px"} ![Toggle Switch](https://assets.openterface.com/images/shell-icons/toggle-h-t_1.svg#only-dark){:style="height:20px"} (hacia adentro = host, hacia afuera = objetivo).  
- **Interruptor de Software**: Un botón de conmutación en la aplicación anfitrión que redirige instantáneamente el puerto USB al anfitrión o al objetivo.

## Estados Operativos

La conexión del puerto USB-A depende de las posiciones del **Interruptor de Hardware** y del **Interruptor de Software**. La siguiente tabla resume los cuatro estados posibles:

| **Estado**| **Interruptor de Hardware**  | **Interruptor de Software**  | **Puerto Conectado A**  | **Estado de Sincronización**         |
|-----------|------------------------------|------------------------------|-------------------------|--------------------------------------|
| 1         | Anfitrión                    | Anfitrión                    | Anfitrión               | Sincronizado                         |
| 2         | Objetivo                     | Objetivo                     | Objetivo                | Sincronizado                         |
| 3         | Objetivo                     | Anfitrión                    | Anfitrión               | Fuera de Sincronización (→ Anfitrión)|
| 4         | Anfitrión                    | Objetivo                     | Objetivo                | Fuera de Sincronización (→ Objetivo) |

- **Sincronizado** significa que las configuraciones de hardware y software coinciden.  
- **Fuera de Sincronización** significa que el software anula temporalmente el interruptor de hardware hasta que se mueva nuevamente el interruptor de hardware.

Cualquier movimiento manual del interruptor de hardware actualizará la pantalla del software y regresará a un estado sincronizado.

Al iniciar, el dispositivo se conecta por defecto al anfitrión. El software detecta la posición del interruptor de hardware y se sincroniza en consecuencia.

!!! Advertencia "Recuerda expulsar la unidad flash antes de cambiar el interruptor"
    Si el puerto USB está siendo utilizado por una unidad flash, asegúrate de expulsar la unidad flash antes de cambiar el interruptor para transferir el uso del puerto a otro ordenador.

??? Nota "¿Cómo compartir una memoria USB/disco entre los dispositivos Anfitrión y Objetivo?"
    Los archivos se pueden transferir entre el anfitrión y el objetivo siguiendo estos pasos:

    1. Monta una unidad USB en el anfitrión cuando el pequeño interruptor negro esté configurado en el lado del puerto Tipo-C del anfitrión.
    2. Copia los archivos en esta unidad montada.
    3. Después de copiar, desmonta la unidad sin desconectarla físicamente.
    4. Cambia el pequeño interruptor negro al otro lado. Esta acción cambia la conexión del puerto USB-A al objetivo.
    5. Monta la memoria USB en el dispositivo objetivo y copia/mueve los archivos de la unidad, completando el proceso de transferencia de archivos del anfitrión al objetivo.

    Este método también se puede utilizar en la dirección opuesta.

!!! Nota "Orientación al Usuario"
    - **Prioridad del Interruptor de Software**: Independientemente de la posición del interruptor de hardware, hacer clic en el interruptor de software cambiará inmediatamente la dirección del circuito.

    - **Sincronización del Interruptor de Hardware**: Cualquier conmutación manual del Interruptor de Hardware alineará su estado con el Interruptor de Software, cambiando a cualquiera de los Estados 1 o 2 desde los Estados 3 o 4 fuera de sincronización. Sin embargo, esta sincronización no altera necesariamente la conexión real del circuito.

    - **Supervisión del Interruptor de Hardware**: El Interruptor de Hardware, a pesar de ser físico, es supervisado por el software y no controla directamente la dirección del circuito. En cambio, el software interpreta la posición del interruptor y gestiona la conmutación real del circuito.
