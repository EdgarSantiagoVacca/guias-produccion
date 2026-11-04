# Instalación de Ubuntu 26.04 (Arranque dual con Windows 11)

Esta guía describe cómo instalar **Ubuntu 26.04 LTS (Resolute Raccoon)** en un PC
que ya tiene **Windows 11**, dejando ambos sistemas operativos disponibles
mediante arranque dual (dual boot).

> Requisitos de Ubuntu 26.04: procesador de doble núcleo a 2 GHz, mínimo 6 GB de
> RAM y 25 GB de disco. Para uso como Kiosko se recomienda dejar bastante más
> espacio para la partición raíz (50–80 GB o más).

## Antes de empezar

```
- Hacer copia de seguridad de los archivos importantes de Windows.
- Tener a mano un USB de recuperación de Windows (opcional pero recomendado).
- Windows 11 usa disco GPT + UEFI, por lo tanto Ubuntu se instala en el mismo modo.
- Regla de oro: Windows se instala primero y Ubuntu después (este es el caso).
```

## Preparar Windows

- Desactivar el **inicio rápido** (Fast Startup). Si queda activo, Windows no se
  apaga del todo y puede corromper la partición compartida o impedir que Ubuntu
  monte el disco (es la causa típica de que no se reconozca el WiFi en dual boot).

- Opción por interfaz gráfica:
  ```
  Panel de control ---> Opciones de energía
    ---> Elegir el comportamiento de los botones de inicio/apagado
    ---> Clic en "Cambiar la configuración actualmente no disponible"
    ---> Desmarcar "Activar inicio rápido"
  ```

- Si la casilla está bloqueada (en gris), desactivar la hibernación desde el
  Símbolo del sistema como administrador:
  ```
  > powercfg /hibernate off
  ```
  Para volver a activarla en el futuro:
  ```
  > powercfg /hibernate on
  ```

- Si la casilla sigue bloqueada por directiva, forzar desde el registro
  (Símbolo del sistema como administrador):
  ```
  > reg add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /v HiberbootEnabled /t REG_DWORD /d 0 /f
  ```

## Liberar espacio para Ubuntu

- Abrir el Administrador de discos de Windows:
  ```
  Win + R ---> diskmgmt.msc
  ```
- Clic derecho sobre la partición C: ---> **Reducir volumen**.
- Liberar al menos 50–80 GB (más si el equipo se usará intensamente).
- Dejar ese espacio **sin asignar**. No crear una partición: Ubuntu la creará.

## Crear el USB de instalación

```
- Descargar la ISO de Ubuntu 26.04 LTS desde ubuntu.com/download.
- Grabar la ISO en un USB de mínimo 8 GB con Rufus o balenaEtcher.
- En Rufus:
    ---> Esquema de partición: GPT
    ---> Sistema destino: UEFI
```

> Se usa GPT (y no MBR) para que el USB arranque en modo UEFI, el mismo modo en
> el que está instalado Windows 11. Ambos sistemas deben usar el mismo modo de
> arranque para que el dual boot funcione.

## Ajustes del BIOS / UEFI

```
- Entrar al BIOS (F2, F10, F12 o Supr según el fabricante).
- Modo de arranque: UEFI (no Legacy/CSM).
- Secure Boot: puede quedar activado (Ubuntu 26.04 lo soporta).
    ---> Si hay problemas al arrancar, desactivarlo.
- Configurar el USB como primer dispositivo de arranque.
```

## Iniciar la instalación

- Arrancar desde el USB y elegir **Instalar Ubuntu**.
- Seleccionar idioma, distribución de teclado y conexión de red.
- En el tipo de instalación elegir la opción **manual / "Algo más"**.
- **No activar el cifrado de disco.** En dual boot con particionado manual,
  el cifrado de Ubuntu añade complejidad innecesaria. Dejar todas las casillas
  de cifrado sin marcar.

## Particionamiento manual

> Verificar primero qué disco es cuál:
> - `sda` suele ser el **USB de instalación** ---> NO se toca.
> - `nvme0n1` (o `sda` si el disco es SATA) es el **disco real** con Windows.

Particiones de Windows que **NO se deben tocar ni formatear**:

```
nvme0n1p1   VFAT    ~100 MB   ---> Partición EFI (Windows Boot Manager)
nvme0n1p2           ~16 MB    ---> Microsoft reserved (MSR)
nvme0n1p3   NTFS    ~1 GB     ---> Partición de recuperación
nvme0n1p4   NTFS    grande    ---> Windows (C:)
```

Crear la partición de Ubuntu sobre el **Espacio libre**:

```
- Seleccionar "Espacio libre" y pulsar el botón "+".
- Crear la partición raíz:
    ---> Tamaño: todo el espacio libre (instalación simple de una sola partición)
    ---> Tipo: primaria
    ---> Utilizar como: Ext4
    ---> Punto de montaje: /
```

Sobre la partición EFI y el swap:

```
- EFI:  reutilizar la partición EFI existente de Windows. NO formatearla.
        El instalador coloca ahí GRUB junto a Windows automáticamente.
- Swap: en Ubuntu 26.04 no se necesita partición de swap (usa /swapfile
        automático). Crear swap dedicado solo si se desea hibernar Ubuntu,
        con un tamaño igual o mayor a la RAM.
```

## Cargador de arranque (GRUB)

```
- En "Dispositivo donde instalar el cargador de arranque", seleccionar el
  DISCO COMPLETO (ej. nvme0n1), nunca una partición concreta ni el USB (sda).
```

## Verificación antes de continuar

```
[ ] Las particiones nuevas se crean solo sobre el espacio libre.
[ ] Ninguna casilla "Formato" marcada en las particiones de Windows (p1–p4).
[ ] La partición raíz / es Ext4.
[ ] El cargador de arranque apunta al disco completo (nvme0n1), no al USB.
[ ] El cifrado de disco está desactivado.
```

Si todo está correcto, pulsar **Siguiente / Instalar** y completar el asistente
(zona horaria, usuario y contraseña).

## Después de la instalación

```
- Retirar el USB y reiniciar.
- GRUB mostrará un menú para elegir entre Ubuntu y Windows Boot Manager.
- GRUB queda como gestor de arranque principal.
```

## Reparar GRUB (si Windows lo sobrescribe)

Si tras una actualización de Windows el equipo arranca directo a Windows y ya
no aparece el menú de GRUB:

```
- Arrancar desde el USB de Ubuntu en modo "Probar Ubuntu".
- Instalar y ejecutar la herramienta boot-repair:
    $ sudo add-apt-repository ppa:yannubuntu/boot-repair
    $ sudo apt update
    $ sudo apt install boot-repair
    $ boot-repair
  ---> Usar la opción "Reparación recomendada".
```

---