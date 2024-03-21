<table>
  <tr>
    <td align='left'><img width="100" src="./img/logo-takub.svg"></td>
    <td><h1>Instalación impresora DNP</h1></td>
  </tr>
</table>

Se describirán los pasos necesarios para instalar las impresoras **DNP** en **Ubuntu**:

- Para comenzar se debe actualizar la lista de paquetes en los repositorios del sistema.
  
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



[mediaSize]: ./img/media-size-DS-RX1.png