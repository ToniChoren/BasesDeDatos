# Indice

1. [Introducción DML](#1-Introducción-DDL)
2. [Creación de bases de datos](#2-Creación-de-bases-de-datos)
3. [Creación de bases de datos](#3-Creacion-de-tablas)
4. [Tipos de datos](#4-Tipos-de-datos)
5. [Dominios](#5-Dominios)
6. [Consultar el diccionario de datos](#6-Consultar-el-diccionario-de-datos)
7. [Borrar tuplas](#7-Borrar-tablas)
8. [Modificar tablas](#8-Modifica-tablas)

	8.1 [Cambiar de nombre a una tabla](#8.1)
	
	8.2 [Borrar contenido a una tabla](#8.2)	
	
	8.3 [Añadir columnas](#8.3)
	
	8.4 [Borrar columnas](#8.4)
	
	8.5 [Modificar columnas](#8.5)	
	
	8.6 [Renombrar una columna](#8.6)
	
### 1 Introducción DML

Es una de las partes fundamentales del lenguaje SQL. El DML (Data Manipulation Language) __lo forman las instrucciones capaces de modificar los datos de las tablas.__ Al conjunto de instrucciones DML que se ejecutan consecutivamente, se las llama transacciones y se pueden anular todas ellas o aceptar, ya que una instrucción DML no es realmente efectuada hasta que no se acepta (COMMIT)

### 2 Insercción de datos

La adición de datos a una tabla se realiza mediante la instrucción INSERT. 

  Su sintaxis fundamental es:
  
 ~~~SQL
  INSERT INTO tabla [(listaDeCampos)]
  VALUES (valor1 [,valor2 ...])
~~~
Ejemplo:

 ~~~SQL
  INSERT INTO informatica
  VALUES 
  ('valor1','valor2', 'valor3', ),
  ('valor1','valor2', 'valor3', ),
  ('valor1','valor2', 'valor3', );
~~~

### 3 Actualizacion de registros 

La modificación de los datos de los registros lo implementa la instrucción UPDATE. 
Sintaxis:

 ~~~SQL
UPDATE clientes
SET name='Ourense',
WHERE provincia='Orense';
~~~
El primer dato actualiza la provincia de los clientes de Orense para que aparezca
como Ourense. 

### Borrado de registros

Se realiza mediante la instrucción DELETE.

Es más sencilla que las anteriores, elimina los registros de la tabla que cumplan
la condición indicada. Ejemplo:

 ~~~SQL
DELETE FROM empleados
WHERE seccion=23;
 ~~~
 
 
 


