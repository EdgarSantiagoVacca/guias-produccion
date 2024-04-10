# Proceso para encender PC en Windows o Ubuntud por defecto

- Se prende el pc en ubuntud se dirige a terminal.
  ```ShellSession
  $ sudo nautilus
  ```
- Escribir la contraseña.

![Terminal][terminal]
- Se abre el explorador de archivos.
- Luego de esto se debe ubicar en: **+otras ubucaciones**. 

![Explorador][explorador]
- Se dirige a **Equipos** como se ve en la imagen superir.
- Se dirige a **etc** / **defaulf**.
- Luego se busca un archivo el cual tiene el nombre de **Grub** como se ve en la imagen inferior.

![Grub][grub]
- Se dirigue al ítem 
  ```
  GRUB_DEFAULT=
  ```
> [!IMPORTANT]
> Después del igual se coloca el número **0** si se quiere prender el PC en **Ubuntud** o si se quiere prender en Windows se coloca el número **2**.

![Grub File][grubFile]
- Después de colocar el número que se quiere se debe dar **guardar** en la parte superir derecho.
- Luego de darle guardar se cierra todas las pestañas y se vuelve abrir la terminal.
  ```ShellSession
  $ sudo update-grub
  ```
- Pedirá contraseña, se introduce y se actualizará el Grup con la opción seleccionada.

- Se cierra la terminal y se reinicia el equipo para verificar si inicio correctamente según la opción selecionada.

![Update Grub][updateGrub]
- Como se puede ver en la imagen si esta seleccionado el procesador Windows se espera unos segundos y se prendera normal y siempre se prendera en Windows hasta que se vuelva a realizar el mismo procedimiento para cambiarlo a ubuntud solo se debe cambiar al numero **(0)**

![Start Grub][startGrub]

[terminal]: ./img/cambio-so/terminal.jpg
[explorador]: ./img/cambio-so/explorador.jpg
[grub]: ./img/cambio-so/grub.jpg
[grubFile]: ./img/cambio-so/grub-file.jpg
[updateGrub]: ./img/cambio-so/update-grub.png
[startGrub]: ./img/cambio-so/start-grub.jpg