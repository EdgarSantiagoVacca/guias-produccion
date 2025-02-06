# Después de instalar Ubuntu
## Formateo para la instalación de solo Ubuuntu
  ```
  Swap ---> el doble de la RAM si es <= a 4GB
  Swap ---> 4GB si la RAM es > a 4GB
  EFI  ---> 1.1GB se genera automaticamente
  ``` 
## Actualizar el sistema e instalar dependencias
- Deshabilitar suspensión del sistema
- Abrir Software y actualizaciones 
  - En la pestaña Software ---> Descargar desde: **Servidor principal**
  - En la pestaña Otro software ---> Socios de Canonical
  - En la pestaña Más controladores ---> Instalar drivers privativos
- Actualizar sistema:
  ```ShellSession
  $ sudo snap refresh
  $ sudo apt-get update
  $ sudo apt-get upgrade
  $ sudo apt-get install ubuntu-restricted-extras
  ```
- Instalar el soporte de idioma español en todo el sistema
- Archivos Comprimidos:
  ```ShellSession
  $ sudo apt install rar unrar unace p7zip-full p7zip-rar lzip arj sharutils mpack lzma lzop unzip zip bzip2 lhasa cabextract lrzip rzip zpaq kgb xz-utils
  ```
- Impresoras:
  ```ShellSession
  $ sudo apt-get install printer-driver-all
  $ sudo apt-get -y install printer-driver-gutenprint
  
  $ sudo apt-get install lsb
  ```
- Limpieza de Ubuntu:
  ```ShellSession
  $ sudo apt autoclean
  $ sudo apt clean
  $ sudo apt autoremove
  ```
## Crear la carpeta TAKUB
- Crear carpeta Takub
  ```ShellSession
  $ mkdir takub
  ```
- Luego copiar 2 carpetas:
  - utils-22
  - drivers-22
## Deshabilitar Wayland
  ```ShellSession
  $ sudo gnome-text-editor /etc/gdm3/custom.conf
    ---> Busca la línea que dice "#WaylandEnable=false"
    ---> Descommenter esta línea.
  ```
## Instalar programas
- Instalar chromium:
  ```ShellSession
  $ sudo snap install chromium
  ```
- Instalar vlc:
  ```ShellSession
  $ sudo snap install vlc
  ```
  Quitar el titulo de los vídeos [Enlace](https://www.youtube.com/watch?v=KilaUmYKneo)
- Instalar Visual Code
  ```ShellSession
  $ sudo snap install code --classic
  ```
- Instalar Rustdesk.deb
  ```ShellSession
  $ sudo dpkg -i rustdesk-1.2.6-x86_64.deb
  $ sudo apt -f install
  $ sudo systemctl disable rustdesk
  ```
- Instalar anydesk .deb
  ```ShellSession
  $ sudo dpkg -i anydesk_6.3.2-1_amd64.deb
  $ sudo apt -f install
  $ sudo systemctl disable anydesk
  ```
- OnlyOffice
  ```ShellSession
  $ sudo snap install onlyoffice-desktopeditors
  ```
- Instalar Git:
  ```ShellSession
  $ sudo apt install git-all
  ```
- Configurar Git:
  ```ShellSession
  $ git config --global color.ui true
  $ git config --global user.name "Takub Kiosk ##"
  $ git config --global user.email "produccion.takub@gmail.com"
  ```
- Instalar node y yarn: 
  ```ShellSession
  $ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
  $ nvm install --lts
  $ npm install -g yarn
  ```
- Instalar L805
  ```ShellSession
  $ sudo dpkg -i epson-inkjet-printer-escpr_1.8.5-1_amd64.deb
    ---> Instalar driver
  $ sudo dpkg -P epson-inkjet-printer-escpr_1.8.5-1_amd64.deb
    ---> Desintalar driver
  ```
- Instalar L800
  ```ShellSession
  $ sudo dpkg -i epson-inkjet-printer-l800_1.0.1-1_amd64.deb 
    ---> Instalar driver
  $ sudo dpkg -P epson-inkjet-printer-l800_1.0.1-1_amd64.deb.deb
    ---> Desintalar driver
  ```
- Instalar Epson Utility
  ```ShellSession
  $ sudo apt install libqt5widgets5
  $ sudo dpkg -i epson-printer-utility_1.1.2-1_amd64.deb
  ```
- Revisar las aplicaciones predeterminadas
  ```ShellSession
  Vídeo   --->  VLC
  Música  --->  VLC
  Fotos   --->  Visor de imágenes
  ```
## Instalar el entorno de Rails
- Instalar dependencias:
  ```ShellSession
  $ sudo apt-get install software-properties-common
  ```
- Instalar RVM:
  ```ShellSession
  $ sudo apt-add-repository -y ppa:rael-gc/rvm
  $ sudo apt-get update
  $ sudo apt-get install rvm
  $ sudo usermod -a -G rvm $USER
  $ echo 'source "/etc/profile.d/rvm.sh"' >> ~/.bashrc
  ```
- Ir a preferencias de la terminal ---> Perfil ---> Comando ---> Ejecutar la orden como un intérprete de acceso
- Instalar Ruby y Rails:
  - Ruby 2.1.10
    ```ShellSession
    $ rvm install 2.1.10
    $ gem install rails -v 3.2.22.5
    $ gem install rails -v 4.X.X
    ```
  - Ruby 2.5.9
    ```ShellSession
    $ cd /usr/local/src/
    $ sudo wget https://www.openssl.org/source/openssl-1.1.1s.tar.gz
    $ sudo tar -xf openssl-1.1.1s.tar.gz
    $ cd openssl-1.1.1s
    $ sudo ./config --prefix=/usr/local/ssl --openssldir=/usr/local/ssl shared zlib
    $ sudo make
    $ sudo make install
    $ sudo rmdir certs
    $ sudo ln -sf /etc/ssl/certs/ certs
    $ rvm install 2.5.9 --with-openssl-dir=/usr/local/ssl
    $ gem install rails -v 5.x.x.x
    ```
  - Ruby 3.0.4
    ```ShellSession
    $ rvm install 3.0.4 --default	
    $ gem install rails -v 7.x.x.x
    ```
  - Ruby 3.1.4
    ```ShellSession
    $ rvm install 3.1.4	
    $ gem install rails -v 7.x.x.x
    ```
## Crear la clave ssh:
  ```ShellSession
  $ ssh-keygen -t ed25519 -b 4096 -C "santiago.vacca@gmail.com"
  $ cd .ssh/
  $ cat xxxxxx.pub
    ---> Copiar clave y agregarla a Bitbucket
  $ ssh -T git@bitbucket.org
    ---> Verificar que la clave funciona bien
  ```
## Instalar complementos para APPs Takub:
- Instalar complementos:
  ```ShellSession
  $ sudo apt-get install build-essential libcurl4-openssl-dev libxml2-dev
  ```
- Instalar ImageMagick:
  ```ShellSession
  $ sudo apt update
  $ sudo apt install imagemagick
  $ identify --version
    ---> Verificar la versión instalada
  ```
- Configurar ImageMagick:
  ```ShellSession
  $ SUDO_EDITOR="gnome-text-editor" sudoedit /etc/ImageMagick-6/policy.xml
  ```
- Remplazar las siguientes lineas en el archivo teniendo en cuenta las características del PC:
  ```html
  <policymap>
    <!-- <policy domain="resource" name="temporary-path" value="/tmp"/> -->
    <policy domain="resource" name="memory" value="4GiB"/>
    <policy domain="resource" name="map" value="4GiB"/>
    <policy domain="resource" name="width" value="128KP"/>
    <policy domain="resource" name="height" value="128KP"/>
    <!-- <policy domain="resource" name="list-length" value="128"/> -->
    <policy domain="resource" name="area" value="1.0737GP"/>
    <policy domain="resource" name="disk" value="16GiB"/>
    <!-- <policy domain="resource" name="file" value="768"/> -->
    <!-- <policy domain="resource" name="thread" value="4"/> -->
    <!-- <policy domain="resource" name="throttle" value="0"/> -->
    <!-- <policy domain="resource" name="time" value="3600"/> -->
    <!-- <policy domain="coder" rights="none" pattern="MVG" /> -->
    <!-- <policy domain="module" rights="none" pattern="{PS,PDF,XPS}" /> -->
    <!-- <policy domain="path" rights="none" pattern="@*" /> -->
    <!-- <policy domain="cache" name="memory-map" value="anonymous"/> -->
    <!-- <policy domain="cache" name="synchronize" value="True"/> -->
    <!-- <policy domain="cache" name="shared-secret" value="passphrase" stealth="true"/> -->
    <!-- <policy domain="system" name="max-memory-request" value="256MiB"/> -->
    <!-- <policy domain="system" name="shred" value="2"/> -->
    <!-- <policy domain="system" name="precision" value="6"/> -->
    <!-- <policy domain="system" name="font" value="/path/to/font.ttf"/> -->
    <!-- <policy domain="system" name="pixel-cache-memory" value="anonymous"/> -->
    <!-- <policy domain="system" name="shred" value="2"/> -->
    <!-- <policy domain="system" name="precision" value="6"/> -->
    <!-- not needed due to the need to use explicitly by mvg: -->
    <!-- <policy domain="delegate" rights="none" pattern="MVG" /> -->
    <!-- use curl -->
    <policy domain="delegate" rights="none" pattern="URL" />
    <policy domain="delegate" rights="none" pattern="HTTPS" />
    <policy domain="delegate" rights="none" pattern="HTTP" />
    <!-- in order to avoid to get image with password text -->
    <policy domain="path" rights="none" pattern="@*"/>
    <!-- disable ghostscript format types -->
    <policy domain="coder" rights="none" pattern="PS" />
    <policy domain="coder" rights="none" pattern="PS2" />
    <policy domain="coder" rights="none" pattern="PS3" />
    <policy domain="coder" rights="none" pattern="EPS" />
    <policy domain="coder" rights="none" pattern="PDF" />
    <policy domain="coder" rights="none" pattern="XPS" />
  </policymap>
  ```
- Instalar FFMPEG
  ```ShellSession
  $ sudo apt install ffmpeg
  $ ffmpeg -version
  ```
## Instalar Aplicaciones Takub:
  ```ShellSession
  $ mkdir takub
  $ cd takaub
  $ git clone git@bitbucket.org:takub/photobooth2.git
    ---> branch: rails7 ---> Ruby 3.1.4
  $ git clone git@bitbucket.org:takub/collage2.git
    ---> branch: rails7 ---> Ruby 3.1.4
  $ git clone git@bitbucket.org:takub/citycapsula2.git
    ---> branch: rails7 ---> Ruby 3.1.4
  $ git clone git@bitbucket.org:takub/trivia2.git
    ---> branch: rails7 ---> Ruby 3.1.4
  $ git clone git@bitbucket.org:takub/challenge2.git
    ---> branch: rails5 ---> Ruby 2.5.9
  $ git clone git@bitbucket.org:takub/tbmemory.git
    ---> branch: totem  ---> Ruby 2.1.10
  ```
## Instalar servidor:
- Por lo general, Ubuntu viene pre instalado con apache, se debe deshabilitar este modulo:
  ```ShellSession
  $ sudo systemctl stop apache2
  $ sudo systemctl disable apache2
  ```
- Ahora procedemos a instalar el servidor:
  ```ShellSession
  $ sudo apt-get install nginx
  $ sudo apt-get install -y dirmngr gnupg apt-transport-https ca-certificates curl
  $ curl https://oss-binaries.phusionpassenger.com/auto-software-signing-gpg-key.txt | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/phusion.gpg >/dev/null
  $ sudo sh -c 'echo deb https://oss-binaries.phusionpassenger.com/apt/passenger jammy main > /etc/apt/sources.list.d/passenger.list'
  $ sudo apt-get update
  $ sudo apt-get install -y libnginx-mod-http-passenger
  ```
- Habilite el módulo Passenger Nginx y reinicie Nginx
  ```ShellSession
  $ si [ ! -f /etc/nginx/modules-enabled/50-mod-http-passenger.conf ]; entonces sudo ln -s /usr/share/nginx/modules-available/mod-http-passenger.load /etc/nginx/modules-enabled/50-mod-http-passenger.conf ; fi
  $ sudo ls /etc/nginx/conf.d/mod-http-passenger.conf
  $ which ruby
    ---> Verificar la ruta del RUBY, pero en le siguiente paso se debe colocar mejor la ruta de por default de RVM
  $ SUDO_EDITOR="gnome-text-editor" sudoedit /etc/nginx/conf.d/mod-http-passenger.conf 
    ---> Cambiar esta variable:  passenger_ruby /usr/share/rvm/rubies/default/bin/ruby;
  $ sudo service nginx restart
  ```
- Verificar instalación del servidor:
  ```ShellSession
  $ sudo /usr/bin/passenger-config validate-install
  $ sudo /usr/sbin/passenger-memory-stats
  ```
- Configurar Nginx y Passenger:
  ```ShellSession
  $ SUDO_EDITOR="gnome-text-editor" sudoedit /etc/nginx/nginx.conf
    ---> Cambiar la variable: 
        user www-data; ---> user root;
    ---> Agregar la siguiente variable dentro de las llaves de http {}:
        # set client body size
        client_max_body_size 100M;
  $ sudo touch /etc/nginx/sites-enabled/portafolio
  $ SUDO_EDITOR="gnome-text-editor" sudoedit /etc/nginx/sites-enabled/portafolio
  ```
- Agregar la configuración del las apps:
  > Nota: Los proyectos Rails deben tener el archivo .ruby-version para que funcione la opción de especificar la versión de ruby en el archivo de configuración del servidor.
  ```
  server {
    listen 3010;
    server_name _;
    root /home/#{usuario-xxxx}/takub/photobooth2/public;
    passenger_enabled on;
    passenger_friendly_error_pages on;
    #passenger_ruby /home/takub-kiosk19/.rbenv/shims/ruby;
    #passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    
    passenger_app_env production;

    access_log /var/log/nginx/photobooth2.log;
  }

  server {
    listen 3011;
    server_name _;
    root /home/takub-10/takub/collage2/public;
    passenger_enabled on;
    passenger_friendly_error_pages on;
    #passenger_ruby /home/takub-kiosk19/.rbenv/shims/ruby;
    #passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    
    passenger_app_env production;

    access_log /var/log/nginx/collage2.log;
  }

  server {
    listen 3012;
    server_name _;
    root /home/takub-10/takub/citycapsula2/public;
    passenger_enabled on;
    passenger_friendly_error_pages on;
    #passenger_ruby /home/takub-kiosk19/.rbenv/shims/ruby;
    #passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    
    passenger_app_env production;

    access_log /var/log/nginx/citycapsula2.log;
  }

  server {
    listen 3013;
    server_name _;
    root /home/takub-10/takub/trivia2/public;
    passenger_enabled on;
    passenger_friendly_error_pages on;
    #passenger_ruby /home/takub-kiosk19/.rbenv/shims/ruby;
    #passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    
    passenger_app_env production;

    access_log /var/log/nginx/trivia2.log;
  }

  server {
    listen 3014;
    server_name _;
    root /home/takub-10/takub/challenge2/public;
    passenger_enabled on;
    passenger_friendly_error_pages on;
    passenger_ruby /home/takub-10/.rvm/rubies/ruby-2.5.9/bin/ruby;
    #passenger_root /usr/lib/ruby/vendor_ruby/phusion_passenger/locations.ini;
    
    passenger_app_env production;

    access_log /var/log/nginx/challenge2.log;
  }
  ```
## Start Kiosk:
- Crear un archivo llamado startKiosk.sh en la carpeta **takub/utiles**
- Agregar estos comandos:
  ```
  xmodmap -e 'pointer = 1 2 0 4 5 6 7 8 9'
  sleep 5
  #xrandr -o left
  chromium-browser http://localhost:3012/apps/1/welcome --use-fake-ui-for-media-stream --kiosk
  ```
- Abrir el programa **Aplicaciones al inicio**
- Hacer clic en **añadir**
- En nombre colorcar: **Start Kiosk**
- Comando: Buscar la ruta del archivo startKiosk.sh
- Hacer clic **añadir**
## Utils:
- Ingresar a la carpeta de utiles
  ```ShellSession
  $ cd takub/utiles/
  ```
- Crear un archivo llamado utils
  ```ShellSession
  $ touch utils.sh
  ```
- Editar el archivo utils.sh
  ```ShellSession
  bundle install
  RAILS_ENV=production rake db:create db:migrate db:seed
  rake assets:precompile --trace RAILS_ENV=production
  SUDO_EDITOR="gedit -w" sudoedit /etc/nginx/sites-enabled/portafolio
  sudo service nginx restart
  ```
## Problemas:
- Cuando no reconoce el WIfI de Ubuntu en un pc que tiene Windows también.
  > Toca desactivar el inicio rápido de Windows, ver el siguiente [enlace](https://www.genbeta.com/paso-a-paso/tienes-problemas-arranque-windows-10-11-esta-opcion-te-puede-ayudar-a-solucionarlos-como-activar-inicio-rapido)
- Cuando no instala un paquete .deb por dependencias
  ```ShellSession
  $ sudo apt -f install
  ```
- Solucionar conección con Anydesk y Teamviewer
  ```ShellSession
  $ sudo vim /etc/gdm3/custom.conf
    ---> Desactivar el Wayland: WaylandEnable=false
    ---> Reiniciar el PC
  ```
- Si no instala RVM
  ```ShellSession
  $ rvm fix-permissions user
  ---> Lo siguiente es otra opción
  $ mkdir -p $HOME/.rvm
  $ curl -sSL https://get.rvm.io | bash -s -- --user-install
  ```
  > Ver [Enlace](https://unix.stackexchange.com/questions/351865/problem-in-rvm-installation)
- Solución a la instalación de Ruby 2.5 
  > Ver [Enlace](https://github.com/rvm/ubuntu_rvm/issues/67#issuecomment-1107065230).
- Subir archivos grandes en el servidor:
  ```ShellSession
  $ sudo atom /etc/nginx/nginx.conf
    ---> (Dentro del archivo agregar la siguiente linea dentro de http{})
    ---> client_max_body_size 1G;
  ```
## Extras:
- Instalar rbenv:
  ```ShellSession
  $ git clone https://github.com/rbenv/rbenv.git ~/.rbenv
  $ echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc
  $ type rbenv
  ```
- Si rbenv install no se encuentra se debe hacer esto:
  ```ShellSession
  $ git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
  ```
- Instalar ruby:
  ```ShellSession
  $ rbenv install 3.2.2
  $ rbenv global 3.2.2
  ```