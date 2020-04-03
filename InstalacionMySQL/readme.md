
# INDICE

1. [Introducción](#1)
2. [Instalar MySQL](#2)
3. [Probar MySQL](#3)
4. [Desinstalación de MySQL](#4)
5. [Instalacion Base de datos Naves Espaciales](#5)
6. [Instalacion Base de datos Proyecto investigación](#6)


# Introducción <a name="1"></a>

MySQL es un sistema de gestión de bases de datos de código abierto, que generalmente está instalado como parte de la popular combinación LAMP (Linux, Apache, MySQL, PHP/Python/Perl). Gestiona sus datos usando una base de datos relacional y SQL (Lenguaje de consulta estructurada).

[⬆⬆ INDICE ⬆⬆](#INDICE)

---

# Instalar MySQL <a name="2"></a>

Únicamente la última versión de MySQL se incluye en el repositorio de paquete APT de forma predeterminada en Ubuntu 18.04. Al momento de escribir esto, esa sería la versión MySQL 5.7.

Para instalarla, actualice el índice del paquete en su servidor con apt:

~~~SQL
  sudo apt update
~~~
![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/captura1.png)

Ahora instalamos el paquete

~~~SQL
  sudo apt-get install mysql-server
~~~

![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/captura2.png)


Con estos dos pasos ya  tendríamos instaldo  MySQL de forma básica y sencilla.

[⬆⬆ INDICE ⬆⬆](#INDICE)

---

# Probar MySQL <a name="3"></a>

Una vez instalado debería haber empezado a ejecutarse automáticamente.
Para probarlo escribimos el soguiente comando.

~~~SQL
  systemctl status mysql.service
~~~
![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/comprobacionServices.PNG)

  Si MySQL no se está ejecutando, puede iniciarlo usando sudo systemctl start mysql.
  
    sudo systemctl start mysql
 
 [⬆⬆ INDICE ⬆⬆](#INDICE)
 
---    

# Desinstalación de MySQL <a name="4"></a>

Generalmente cuando instalamos el MySQL en los sistemas Linux Debian o Ubuntu, se instalan los siguiente paquetes.

    1. mysql-client La última versión del cliente MySQL.
    2. mysql-server La última versión del servidor MySQL.
    3. mysql-common Y el MySQL database common files.

¿Cómo desintalamos el MySQL?

Utilizando los siguientes comandos apt-get podemos desinstalar el MySQL de nuestro Linux. Los comandos serian:

~~~SQL
sudo apt-get --purge remove mysql-client mysql-server mysql-common
sudo apt-get autoremov
~~~

Luego borrarmos el directorio del MySQL /etc/mysql/ con el siguiente comando

~~~SQL
 sudo rm -rf /etc/mysql/
~~~

La explicación de lo que hicimos:

    — purge : Eliminamos los paquetes y los archivos de configuración.
      remove : desinstala los paquetes.
      autoremove : Fuerza para eliminar los paquetes que se instalaron de forma automatica debido a las necesidades de las dependencias de otros paquetes y ahora ya no son necesarios.

[⬆⬆ INDICE ⬆⬆](#INDICE)

---

# Creacion Base de datos Naves Espaciales <a name="5"></a>

- Sino estamos como root, nos logeamos con __sudo su__ y escribimos la contraseña.

- Después ponemos __mysql__ para hacer a la base de datos

- Y luego escribimos la siguiente sentencia:

![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/captura4_Servicio.png)

- Despues vamos introduciendo las sentencias o importarla desde un archivo. 

      En mi caso las voy a introducir mediante consola.

![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/captura5_Servicio.png)


- Cuando terminemos mostramos la bese de datos con el comando:

      show databases
 
![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/database01.PNG)

- Para hacer uso de una bases de datos  se haría de la siguiente manera:

      use navesEspaciales

- Después mostramos las tablas creadas con anterioridad con el siguiente comando

      show tables
      
 ![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/mostrar_navesEspaciales.PNG)
     
 
 - Podemos mostrar la descripcion utilizando el comando __desc__
 
 ![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/desc_planteta.PNG)


[⬆⬆ INDICE ⬆⬆](#INDICE)

---
 
 # Creacion Base de datos Proyecto Investigación <a name="6"></a>
 
 - Sino estamos como root, nos logeamos con __sudo su__ y escribimos la contraseña.

 - Después ponemos __mysql__ para hacer a la base de datos

 - Escribimos el siguiente comando para crear la base de datos: 
      
        CREATE SCHEMA proInv;
    
 - Y luego escribimos la siguiente sentencia:
 
      show databases;
 
 ![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/showDatabaes.PNG)
 
 - Para selecionarla:
 
        use proInv
        
 - Y luego para visializar las sentencias escribimos  __show tables__.
 
 ![Alt text](https://github.com/ToniChoren/BasesDeDatos/blob/master/InstalacionMySQL/capturas/capturas%20ubuntu/showTables.PNG)

[⬆⬆ INDICE ⬆⬆](#INDICE)

***




















