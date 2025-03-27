# Configuración Táctil

Se describirán los pasos necesarios para **configurar** la orientación del **marco táctil** en una **pantalla**:

- Para comenzar se debe verificar que el táctil si este funcionando tocando la pantalla en el escritorio y revisando cual es la orientación que tiene.
- Luego se ingresa al archivo de configuración:
  ```ShellSession
  $ SUDO_EDITOR="gedit -w" sudoedit /etc/udev/rules.d/99-calibration.rules
  ```
- Aquí se debe colocar la siguiente linea:
  ```
  ---> Para rotar a la izquierda
  ATTRS{name}=="IrScreen cc", ENV{LIBINPUT_CALIBRATION_MATRIX}="0.000000 1.000000 0.000000 -1.000000 0.000000 1.000000 0.000000 0.000000 1.000000"
  ---> Para rotar a la derecha
  ATTRS{name}=="IrScreen cc", ENV{LIBINPUT_CALIBRATION_MATRIX}="0.000000 -1.000000 1.000000 1.000000 0.000000 0.000000 0.000000 0.000000 1.000000"
  ---> Cambiar CALIBRATION_MATRIX por alguna de estas opciones: 
        ENV{LIBINPUT_CALIBRATION_MATRIX}="1 0 0 0 1 0" # default
        ENV{LIBINPUT_CALIBRATION_MATRIX}="0 -1 1 1 0 0" # 90 degree clockwise
        ENV{LIBINPUT_CALIBRATION_MATRIX}="-1 0 1 0 -1 1" # 180 degree clockwise
        ENV{LIBINPUT_CALIBRATION_MATRIX}="0 1 0 -1 0 1" # 270 degree clockwise
        ENV{LIBINPUT_CALIBRATION_MATRIX}="-1 0 1 1 0 0" # reflect along y axis
  ```