# Next-Cloud

 1. Entrar a Next-Cloud

 ![](/FOTOS/pagina.png)

 2. Elegimos la opcion de `server packages`

 ![](/FOTOS/elegir-opcion.png)

 3. Instalamos `Next-Cloud`

 ![](/FOTOS/INSTALACION.png)

 4. Creamos una carpeta llamada `clouds` haciendo mkdir y entramos dentro de la carpeta haciendo cd.

 ![](/FOTOS/carpeta.png)

 5. Ahora descargamos la máquina que necsitamos para con el siguiente comando `vagrant init ubuntu/focal64` y hacemos `vagrant up --provider=virtualbox`para proveer el virtualbox

 ![](/FOTOS/instalarmaquina.png)

 6. Después copiamos el archivo dentro de la carpeta que hemos creado.

![](/FOTOS/copiar.png)

7. Encendemos la máquina y entramos dentro de la máquina para verificar que funciona.

![](/FOTOSencender.png)
![](/FOTOS/verificar.png)

9. Instalamos `unzip`, movemos el archivo nextcloud al directorio `/var/www/html` y le hacemos un `umv nzip` a la crapeta `nextcloud-22.2.0.zip`.

![](/FOTOS/installunzip.png)
![](/FOTOS/mover.png)
![](/FOTOS/unzip.png)

10. Despues hacemos sudo -s para entrar en root y ponemos los siguientes comandos para instalar el servidor web el apache2.

![](/FOTOS/apache.png)

11. Después instalamos el servidor de base de datos con el siguiente comando.

![](/FOTOS/mysql.png)

12. Y instalamos algunas librerias de php que es el lenguaje pincipal que utilizan las aplicaciones.

![](/FOTOS/php.png)

13. Entramos al servidor `mysql` de la siguiente manera.

![](/FOTOS/mysql2.png)

14. Dentro de mysql creamos la database.

![](/FOTOS/database.png)

15. Con este comando podremos apagra la maquina `vagrant halt` y con este otro podremos encender la máquina `vagrant up`.
