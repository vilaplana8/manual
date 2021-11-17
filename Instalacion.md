# Instalar Owncloud


Como instalar un OwnCloud a través  de un contenedor.


Para crear el contenedor tenemos que abrir el terminal y con el cd nos metemos en la carpeta que nos hemos descargado el archivo zip.
Cuando estamos dentro debemos de ejecutar el siguiente comando para crear el contenedor:

~~~
lxc launch ubuntu:20.04 elmeucontenidor
~~~

Cuandoe la crees la inicias de la siguiente forma:

~~~
lxc start elmeucontenidor
~~~

Cuando este iniciadolo ejecutas con el siguiente comando:

~~~
lxc exec micontenedor -- /bin/bash
~~~


Después instalas el servifor web y lo haremos con los siguientes comandos:

~~~
apt update
apt install -y apache2
~~~

Ahora deberemos de descargar el archivo zip y le haremos unzip dentro de la carpeta var/www/html. Nos meteremos dentro de var/www/html haciendo un cd y pondreos los siguientes comandos:

~~~
apt update
apt install unzip
wget https://download.owncloud.org/community/owncloud-complete-20210721.zip
unzip owncloud-complete-20210721.zip
~~~


Entramos en la carpeta Owncloud que ya estará creada y copiaremos los archivos al directorio anterior.

~~~
cp -r . ..
~~~

Cuando acabemos de hacer esto le cambiaremos los permisos a todos los ficheros, para hacerlo entramos en la carpeta y ponemos los siguientes comandos:


~~~
chown -R www-data:www-data /var/www/html
chmod -R 775 /var/www/html
~~~

Si hacemos `ls -l`se van a ver los ficheros con los siguientes permisos:


![](/FOTOS/permisos.png)


Vamos a instalar el `mysql-server` y unas cuantas librerias `php` ejecutando los siguientes comandos:

~~~
apt update
apt install -y mysql-server
apt install php libapache2-mod-php
apt install php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl mysql php-cli php-ldap php-zip php-curl
~~~

Reiniciamos el servidor con `systemctl restart apache2`


Creamos la base de datos, para ello entramos en mysql usanco el comando `mysql` en el terminal,
y tambien ejecutamos el siguinte comando:

~~~
CREATE DATABASE bbdd;
~~~

Creamos los usuarios que se llamaran usuarios y la contraseña será password.

~~~
CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
CREATE USER 'usuario'@'ruben' IDENTIFIED WITH mysql_native_password BY 'password';
~~~

Le damos los privilegios a los usuarios creados con los siguientes comandos:

~~~
GRANT ALL ON bbdd.* to 'usuario'@'localhost';
GRANT ALL ON bbdd.* to 'usuario'@'ruben';
~~~



Y una vez creado reiniciazmos el servidor haciendo `systemctl restart apache2` y paar acceder al OwnCloudentramos en nuestro navegador y buscamos `localhost:8080`
