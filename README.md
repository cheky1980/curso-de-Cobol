# curso-de-Cobol
Cobol en mvs Z/OS JCL 
instalación en windows
Para emular un MVS con TK4 en una terminal de windows C:\mvs\mvs.bat se cargan los scripts y conecta a la termianl para luego abrir el entorno de ZOC7 y comenzar a trabajar en una terminal cobol. A continuación dejo los enlaces para descargar las aplicaciones.

https://wotho.ethz.ch/tk4-/  donwload tk4-_v1.00_current.zip
http://www.hercules-390.org/
http://tombrennansoftware.com/v200/ donwload Click here to download and install
https://sourceforge.net/projects/x3270/ donwload x3270

Para instalación con linux

sudo apt-get update
Es necesario instalar el emulador Hercules, para ello tecleamos la instrucción:
apt-get install hercules
Una vez finalizada la instalación de Hercules, en el navegador de tu preferencia, busca TK4- wotho o ve a directo a este website Aquí vamos a descargar el emulador del sistema operativo MVS:
Para descargar MVS selecciona con tu mouse el último enlace o da clic en el siguiente link:
Descarga aquí
Posterior a esto, genera en /root una carpeta con el nombre mvs:
mkdir mvs
Ahora, dirígete a esta carpeta desde la terminal y vamos a descargar aquí el archivo comprimido del entorno de desarrollo. Teclea el comando wget seguido del contenido del enlace que copiaste en un paso anterior:
Una vez finalizada la descarga, descomprime el .zip que has descargado, y el contenido déjalo en la carpeta mvs:
unzip tk4-_v1.00_current.zip
Al finalizar la descompresión de este archivo, dirígete a la carpeta conf:
Ahora, edita el contenido del archivo tk4-.cnf con tu editor de texto preferido. En mi caso utilizaré VIM:
Y modificaremos las líneas NUMCPU y MAXCPU, modificando el valor por default 1 a 2, del siguiente modo:
NUMCPU ${NUMCPU:=2}
MAXCPU ${MAXCPU:=2}

Finalmente guarda los cambios realizados.

A continuación regresa a la carpeta mvs y dirígete a la carpeta unattended con:

cd ..

cd unattended

El siguiente paso es activar el script llamado set_console_mode:

./set_console_mode

Con esto hemos hecho que los scripts de ejecución para activar el entorno de desarrollo se ejecuten de manera automática.

Regresa de nuevo a la carpeta mvs y ejecuta el comando:

./mvs

Ahora espera de 2 a 4 minutos a que los scripts ejecuten el emulador que nos servirá como entorno de desarrollo, la pantalla que debes ver al finalizar la ejecución de los scripts y que te indican que puedes ingresar a la terminal 3270 es la siguiente:

Como paso siguiente, vamos a efectuar la instalación de la terminal 3270:
Teclea en la terminal:


sudo apt-get install x3270

10. Al terminar la instalación, ejecuta el comando X3270:


x3270

Nos va a abrir la ventana de configuración en donde vamos a digitar los parámetros 127.0.0.1:3270 (con el primer parámetro indicamos que la ubicación del entorno es nuestra máquina local; con el segundo parámetro indicamos el puerto con el que nos conectamos a nuestra máquina local, por estándar utilizamos 3270)


127.0.0.1:3270

Damos clic en Connect.

Así hemos logrado ingresar a la terminal:

Cuando teclees Enter, ingresas el usuario HERC01, después teclea nuevamente Enter y ahora digita la contraseña: CUL8TR, seguido de Enter:

image19.png
¡Listo! Ya estamos preparados para continuar con el curso desde nuestro sistema operativo Ubuntu.
