# Instalación impresora Epson L800

- Para iniciar la configuración de una impresora lo primero que se hace es verificar que este conectada a la corriente y que el cable de datos este conectado tanto a la impresora como al computador, una vez confirmado esto se enciende la impresora.
- El siguiente paso es buscar en lo barra de programas y herramientas que se encuentra a mano izquierda de la pantalla el **Botón de Configuración** general del equipo y dar clic sobre este.
![desktop ubuntu][desktopUbuntu]
- Una Vez abierta la ventana de configuración, dirigirse al **buscador y escribir impresoras**.
![ventana configuración impresora][configuracionImpresora]
- Si aparecen impresoras por defecto lo mejor es eliminarlas para que el equipo reconozca la impresora que se va a configurar desde cero.
- Para eliminar las impresoras se oprime la tuerca que aparece a mano derecha, va a aparecer una lista desplegable y se debe oprimir en la opción quitar impresora.
![quitar impresora][quitarImpresora]
- Una vez eliminadas las impresoras se oprime el **botón verde** que dice Añadir impresora, inmediatamente se detectan las impresoras que estén conectadas al computador.
- Se le da clic izquierdo sobre la impresora a configurar (L800) y se oprime el **botón añadir**.
![añadir impresora][anadirImpresora]
- Una vez añadida la impresora se procede a hacer la respectiva configuración dando clic sobre el botón que tiene el icono de una tuerca a mano derecha y se despliega un listado, se le da clic izquierdo sobre opciones de impresión.
- Se abre una nueva ventana donde solo se debe configurar: 
  ```
  Tipo de papel => EPSON PREMIUM SEMIGLOSS 
  Tamaño        => 10x15 cm (4x6 pulg)
  ```
- Esta ventana tiene dos opciones en la parte superior izquierda se debe darle clic izquierdo sobre la opción **Avanzado** (para configurar solo las márgenes) esta opción debe estar activa, para finalizar se cierra la venta de configuración y nuevamente se oprime la tuerca para seleccionar **impresora de usuario predeterminada**.
![configurar L800 - paso 1][configL800Paso1]
![configurar L800 - paso 2][configL800Paso2]
- Para finalizar se cierran las ventanas de configuración.

[desktopUbuntu]: ./img/escritorio-ubuntu22.png
[configuracionImpresora]: ./img/config-impresora.png
[quitarImpresora]: ./img/quitar-impresora.png
[anadirImpresora]: ./img/anadir-impresora.png
[configL800Paso1]: ./img/config-l800-paso1.png
[configL800Paso2]: ./img/config-l800-paso2.png
