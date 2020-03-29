# Apuntes DDL y DML
## Indice


### Introducción

El DDL es la parte del lenguaje SQL que realiza la función de definición de datos del SGBD. Fundamentalmente se encarga de la creación, modificación y eliminación de los objetos de la base de datos (es decir de los metadatos). Por supuesto es el encargado de la creación de las tablas.

 Cada usuario de una base de datos posee un esquema. El esquema suele tener el mismo nombre que el usuario y sirve para almacenar los objetos de esquema, es decir los objetos que posee el usuario. 

Esos objetos pueden ser: tablas, vistas, índices y otras objetos relacionados con la definición de la base de datos. Los objetos son manipulados y creados por los usuarios. En principio sólo los administradores y los usuarios propietarios pueden acceder a cada objeto, salvo que se modifiquen los privilegios del objeto para permitir el acceso a otros usuarios. 

Hay que tener en cuenta que ninguna instrucción DDL puede ser anulada por una instrucción ROLLBACK (la instrucción ROLLBACK está relacionada con el uso de transacciones que se comentarán más adelante) por lo que hay que tener mucha precaución a la hora de utilizarlas. Es decir, las instrucciones DDL generan acciones que no se pueden deshacer (salvo que dispongamos de alguna copia de seguridad).

### Creación de bases de datos

El comando SQL de creación de una base de datos es CREATE DATABASE. Este comando crea una base de datos con el nombre que se indique. Ejemplo:
~~~SQL
CREATE DATABASE prueba;
~~~
### Creación de tablas

El nombre de las tablas deben cumplir las siguientes reglas: 

- Deben comenzar con una letra 
-  No deben tener más de 30 caracteres 
- Sólo se permiten utilizar letras del alfabeto (inglés), números o el signo de subrayado (también el signo $ y #, pero esos se utilizan de manera especial por lo que no son recomendados) 
- No puede haber dos tablas con el mismo nombre para el mismo esquema (pueden coincidir los nombres si están en distintos esquemas)  
- No puede coincidir con el nombre de una palabra reservada SQL (por ejemplo no se puede llamar SELECT a una tabla)

**CREATE TABLE**
 Es la orden SQL que permite crear una tabla:

~~~SQL
CREATE TABLE nombreTabla(
Dato1 INTEGER [NOT NULL] PRYMARY KEY,
Dato2 VARCHAR(30),
Dato1 CHAR(10)
);
~~~
### Tipos de datos
A la hora de crear tablas, hay que indicar el tipo de datos de cada campo. Necesitamos pues conocer los distintos tipos de datos. Estos son:

|Descripción | Tipo Dato|
|---------------|----------|
| Texto anchura fija  |  CHARACTER(n) ò CHAR(n)|
|  Texto de anchura variable  |    VARCHAR (n)            |
|Enteros pequeños (2 bytes)|SMALLINT |
|Enteros normales (4 bytes)|INTEGER o INT|
|Enteros largos (8 bytes)|BIGUINT|
|Decimal de coma variable|FLOAT|
|Decimal de coma variable|DOUBLE|
|Fechas|DATE|
|Lógicos|BOOLEAN o BOOL|
|Monedas 8 bytes|MONEY|


### Dominios
Se trata de CREATE DOMAIN:

Ejemplo: 

~~~SQL
CREATE DOMAIN Tdireccion AS VARCHAR(3); 
~~~

Gracias a esa instrucción podemos crear la siguiente tabla:
~~~SQL
 CREATE TABLE personal(
  codPers SMALLINT, 
  nombre VARCHAR(30), 
  direccion Tdireccion 
  );
~~~

### Consultar el estado de datos

El diccionario de datos es accesible mediante el esquema  de información (INFORMATION_SCHEMA), un esquema especial que contiene el conjunto de vistas con el que se pueden consultar metadatos de la base de
datos.
 En concreto la vista INFORMATION_SCHEMA.TABLES obtiene una vista de
las tablas creadas. Es decir:
~~~SQL
SELECT * FROM INFORMATION_SCHEMA.TABLES
~~~

### Borrar tablas
La orden __DROP TABLE__ seguida del nombre de una tabla, permite eliminar la tabla en cuestión.
Normalmente, el borrado de una tabla es irreversible, y no hay ninguna petición de confirmación, por lo que conviene ser muy cuidadoso con esta operación.

### Modifica tablas
1. Cambiar de nombre a una tabla
~~~SQL
ALTER TABLE nombreViejo RENAME TO nombreNuevo;
~~~

### Borrar contenido de tablas
Se dispone de una orden no estándar para eliminar definitivamente los datos de una tabla; es la orden __TRUNCATE TABLE__ seguida del nombre de la tabla a borrar. Hace que se elimine el contenido de la tabla, pero no la estructura de la tabla en sí. Incluso borra del archivo de datos el espacio ocupado por la tabla.














