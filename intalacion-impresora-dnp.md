<table>
  <tr>
    <td><img width="150px" src="./img/logo-takub.svg"></td>
    <td><h1>Instalación impresora DNP</h1></td>
  </tr>
</table>

Se describirán los pasos necesarios para instalar las impresoras **DNP** en **Ubuntu**:

- Para comenzar se debe actualizar la lista de paquetes en los repositorios del sistema en la terminal.
  ```ShellSession
  $ sudo apt update
  ```
- Después se instala el paquete con los controladores
  ```ShellSession
  $ sudo apt-get -y install printer-driver-gutenprint
  ```
- En este punto se conecta la impresora al **PC** y se verifica que la impresora se instale automáticamente. El nombre de la impresora deben ser alguno de los siguientes:
  > - DS-RX1
  > - Dai_Nippon_Printing_DS-RX1
- Para comprobar que efectivamente la impresora se instaló correctamente debemos ingresar a las opciones de la impresora y verificar que en la opción **Media Size** se pueda seleccionar las siguientes opciones:
  > - 4x6
  > - 2x6*2

  ![media size][mediaSize]

### No reconoce la impresora correctamente

Estes pasos solo se deben hacer si la impresora **no es reconocida** o es **detectada con un driver genérico** y ya haber echo los pasos anteriores.

- Se debe abrir el navegador en la siguiente ruta:
  > localhost:631
- Luego hacer click en la pestaña **administración**:
  ![admin cups][adminCups]
- Se debe ingresar el usuario y contraseña:
  ![login cups][loginCups]
- Para conocer el nombre de usuario se debe ir a la terminal:
  ```ShellSession
  $ whoami
  ```
- Copiamos el nombre e ingresamos la contraseña.
- Seleccionamos la impresora en **Impresoras locales** y click en **siguiente**:
  ![paso 1 cups][paso1Cups]
- Avanzamos con el botón **siguiente**:
  ![paso 2 cups][paso2Cups]
- Seleccionamos la Marca **Dai Nippon Printing** y click en **siguiente**:
  ![paso 3 cups][paso3Cups]
- Seleccionamos la Modelo **Dai Nippon Printing DSRX1 - CUPS...** y click en **siguiente**:
  ![paso 4 cups][paso4Cups]
- Se crea la impresora exitosamente:
  ![paso 5 cups][paso5Cups]
- Para finalizar se verifica la impresora en el sistema:
  ![paso 6 cups][paso6Cups]

[mediaSize]: ./img/media-size-DS-RX1.png
[adminCups]: ./img/admin-cups.png
[loginCups]: ./img/login-cups.png
[paso1Cups]: ./img/paso-1-cups.png
[paso2Cups]: ./img/paso-2-cups.png
[paso3Cups]: ./img/paso-3-cups.png
[paso5Cups]: ./img/paso-5-cups.png
[paso6Cups]: ./img/paso-6-cups.png