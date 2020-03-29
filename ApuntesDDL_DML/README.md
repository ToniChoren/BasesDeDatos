
## Indice
1. [Introducción]_(#1 Introducción)
2. [Creación de bases de datos]
3. [Creación de bases de datos]
4. [Tipos de datos]
5. [Consultar el diccionario de datos]
6. [Borrar tuplas]
7. [Modificar tablas]
	7.1 [Cambiar de nombre a una tabla]
	7.2 [Borrar contenido a una tabla]
	7.3 [Añadir columnas]
	7.4 [Borrar columnas]
	7.5 [Modificar columnas]
	7.6 [Renombrar una columna]
	7.7 [Valor por defecto]
8. [Restricciones]
	8.1 [Prohibir nulos]
	8.2 [Valores únicos]
	8.3 [Clave Primaria]
	8.4 [Valores Foránea]
	8.5 [Restricciones de vaoración]


### 1 Introducción

El DDL es la parte del lenguaje SQL que realiza la función de definición de datos del SGBD. Fundamentalmente se encarga de la creación, modificación y eliminación de los objetos de la base de datos (es decir de los metadatos). Por supuesto es el encargado de la creación de las tablas.

 Cada usuario de una base de datos posee un esquema. El esquema suele tener el mismo nombre que el usuario y sirve para almacenar los objetos de esquema, es decir los objetos que posee el usuario. 

Esos objetos pueden ser: tablas, vistas, índices y otras objetos relacionados con la definición de la base de datos. Los objetos son manipulados y creados por los usuarios. En principio sólo los administradores y los usuarios propietarios pueden acceder a cada objeto, salvo que se modifiquen los privilegios del objeto para permitir el acceso a otros usuarios. 

Hay que tener en cuenta que ninguna instrucción DDL puede ser anulada por una instrucción ROLLBACK (la instrucción ROLLBACK está relacionada con el uso de transacciones que se comentarán más adelante) por lo que hay que tener mucha precaución a la hora de utilizarlas. Es decir, las instrucciones DDL generan acciones que no se pueden deshacer (salvo que dispongamos de alguna copia de seguridad).

### 2 Creación de bases de datos

El comando SQL de creación de una base de datos es CREATE DATABASE. Este comando crea una base de datos con el nombre que se indique. Ejemplo:
~~~SQL
CREATE DATABASE prueba;
~~~
### 3 Creación de tablas

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
### 4 Tipos de datos
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

### Consultar el diccionario de datos

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

2. Borrar contenido de tablas
Se dispone de una orden no estándar para eliminar definitivamente los datos de una tabla; es la orden __TRUNCATE TABLE__ seguida del nombre de la tabla a borrar. Hace que se elimine el contenido de la tabla, pero no la estructura de la tabla en sí. Incluso borra del archivo de datos el espacio ocupado por la tabla.

3. Añadir columnas

Permite añadir nuevas columnas a la tabla. Se deben indicar su tipo de datos y sus propiedades si es necesario (al estilo de CREATE TABLE). Las nuevas columnas se añaden al final, no se puede indicar otra posición (hay que recordar que el orden de las columnas no importa).
~~~SQL
ALTER TABLE facturas ADD (fecha DATE);
~~~


4. Borrar columnas

Elimina la columna indicada de manera irreversible e incluyendo los datos que contenía. No se puede eliminar la única columna de una tabla que sólo tiene esa columna (habrá que usar DROP TABLE). 
~~~SQL
ALTER TABLE facturas DROP (fecha);
~~~
5. Modificar columnas

Permite cambiar el tipo de datos y propiedades de una determinada columna. Sintaxis:
~~~SQL
ALTER TABLE facturas MODIFY(fecha TIMESTAMP);
~~~


6. Renombrar una columna

Esto permite cambiar el nombre de una columna. 
Sintaxis 
~~~SQL
ALTER TABLE nombreTabla 
RENAME COLUMN nombreAntiguo TO nombreNuevo 
~~~
Ejemplo:
~~~SQL
 ALTER TABLE facturas RENAME COLUMN fecha TO fechaYhora;
~~~
7. Valor por defecto

A cada columna se le puede asignar un valor por defecto durante su creación mediante la propiedad __DEFAULT.__ Se puede poner esta propiedad durante la creación o modificación de la tabla, añadiendo la palabra __DEFAULT__ tras el tipo de datos del campo y colocando detrás el valor que se desea por defecto.

Ejemplo:
~~~SQL 
  CREATE TABLE articulo (cod NUMBER(7), nombre VARCHAR2(25), precio NUMBER(11,2) DEFAULT 3.5); 
~~~
La palabra DEFAULT se puede añadir durante la creación o la modificación de la tabla (comando ALTER TABLE)

### Restricciones

Una restricción es una condición de obligado cumplimiento para una o más columnas de la tabla. No se puede repetir.
Se aconseja la siguiente regla a la hora de poner nombre a las restricciones:  
- Tres letras para el nombre de la tabla 
- Carácter de subrayado  
- Tres letras con la columna afectada por la restricción 
- Carácter de subrayado 
- Dos letras con la abreviatura del tipo de restricción. La abreviatura puede ser: 
	- __NN__. NOT NULL.  
	- __PK__. PRIMARY KEY 
	- __UK__. UNIQUE 
	- __FK__. FOREIGN KEY 
	- __CK__. CHECK (validación) 

Por ejemplo para hacer que la clave principal de la tabla Alumnos sea el código del alumno, el nombre de la restricción podría ser:

	alu_cod_pk
			 
1. Prohibir nulos

La restricción NOT NULL permite prohibir los nulos en una determinada tabla. Eso obliga a que la columna tenga que tener obligatoriamente un valor para que sea almacenado el registro. Se puede colocar durante la creación (o modificación) del campo añadiendo la palabra NOT NULL tras el tipo:
~~~SQL 
CREATE TABLE cliente(dni VARCHAR2(9) NOT NULL);
~~~

2. Valores únicos

Las restricciones de tipo UNIQUE obligan a que el contenido de una o más columnas no puedan repetir valores. Nuevamente hay dos formas de colocar esta restricción:

~~~SQL
CREATE TABLE cliente(dni VARCHAR2(9) UNIQUE);
~~~
3. Clave Primaria

La clave primaria de una tabla la forman las columnas que indican a cada registro de la misma. La clave primaria hace que los campos que la forman sean NOT NULL (sin posibilidad de quedar vacíos) y que los valores de los campos sean de tipo UNIQUE (sin posibilidad de repetición). 

Si la clave está formada por un solo campo basta con:
~~~SQL
CREATE TABLE cliente( 
dni VARCHAR(9) PRIMARY KEY, 
nombre VARCHAR(50)
);
~~~
Poniendo un nombre a la restricción:

~~~SQL
CREATE TABLE cliente( dni VARCHAR(9) CONSTRAINT cliente_pk PRIMARY KEY, 
nombre VARCHAR(50)
);
~~~
Si la clave está formada por más de un campo:
~~~SQL
CREATE TABLE alquiler,
dni VARCHAR(9), 
cod_pelicula INTEGER(5), 
CONSTRAINT alquiler_pk 
PRIMARY KEY(dni,cod_pelicula)) ;
~~~

4. Clave foránea

Una clave secundaria o foránea, es uno o más campos de una tabla que están relacionados con la clave principal.

~~~SQL
CREATE TABLE alquiler( 
dni VARCHAR2(9) CONSTRAINT dni_fk REFERENCES clientes, 
cod_pelicula NUMBER(5) CONSTRAINT pelicula_fk REFERENCES peliculas, 
CONSTRAINT alquiler_pk PRIMARY KEY(dni,cod_pelicula) 
);
~~~


La integridad referencial es una herramienta imprescindible de las bases de datos relacionales. Pero provoca varios problemas. Por ejemplo, si borramos un registro en la tabla principal que está relacionado con uno o varios de la secundaria ocurrirá un error, ya que de permitírsenos borrar el registro ocurrirá fallo de integridad (habrá claves secundarios refiriéndose a una clave principal que ya no existe). 

Por ello se nos pueden ofrecer soluciones a añadir tras la cláusula REFERENCES. 
Son:
- __ON DELETE SET NULL.__ Coloca nulos todas las claves secundarias relacionadas con la borrada. 
- __ON DELETE CASCADE.__ Borra todos los registros cuya clave secundaria es igual que la clave del registro borrado. 
- __ON DELETE SET DEFAULT.__ Coloca en el registro relacionado el valor por defecto en la columna relacionada
- __ON DELETE NOTHING.__ No hace nada.

En el caso explicado se aplicarían las cláusulas cuando se eliminen filas de la clave principal relacionada con la clave secundaria. En esas cuatro cláusulas se podría sustituir la palabra __DELETE__ por la palabra __UPDATE,__ haciendo que el funcionamiento se refiera a cuando se modifica un registro de la tabla principal; en muchas bases de datos se admite el uso tanto de ON DELETE como de ON UPDATE.

Ejemplo
~~~SQL
CREATE TABLE alquiler(dni VARCHAR(9), 
cod_pelicula NUMBER(5), 
CONSTRAINT alquiler_pk PRIMARY KEY(dni,cod_pelicula), 
CONSTRAINT dni_fk FOREIGN KEY (dni) REFERENCES clientes(dni) 
ON DELETE SET NULL, 
CONSTRAINT pelicula_fk FOREIGN KEY (cod_pelicula) 
REFERENCES peliculas(cod) 
ON DELETE CASCADE );
~~~

5. Restricción de validación

Son restricciones que dictan una condición que deben cumplir los contenidos de una columna. Una misma columna puede tener múltiples CHECKS en su definición (se pondrían varios CONSTRAINT seguidos, sin comas)

~~~SQL
CREATE TABLE ingresos(
cod INTEGER(5) PRIMARY KEY, 
concepto VARCHAR(40) NOT NULL, 
importe MONEY(11,2) CONSTRAINT importe_min 
CHECK (importe>0) 
CONSTRAINT importe_max 
CHECK (importe<8000) );
~~~








