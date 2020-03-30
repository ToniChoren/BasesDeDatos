# Indice

1. [Introducción DML](#1)
2. [Insercción de datos(INSERT)](#2)
3. [Actualizacion de registros(UPDATE)](#3)
4. [Borrado de registros(DELETE)](#4)
	
### 1 Introducción DML <a name="1"></a>

Es una de las partes fundamentales del lenguaje SQL. El DML (Data Manipulation Language) __lo forman las instrucciones capaces de modificar los datos de las tablas.__ Al conjunto de instrucciones DML que se ejecutan consecutivamente, se las llama transacciones y se pueden anular todas ellas o aceptar, ya que una instrucción DML no es realmente efectuada hasta que no se acepta (COMMIT)

### 2 Insercción de datos(INSERT) <a name="2"></a>

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

### 3 Actualizacion de registros(UPDATE) <a name="3"></a>

La modificación de los datos de los registros lo implementa la instrucción UPDATE. 
Sintaxis:

 ~~~SQL
UPDATE clientes
SET name='Ourense',
WHERE provincia='Orense';
~~~
El primer dato actualiza la provincia de los clientes de Orense para que aparezca
como Ourense. 

### 4 Borrado de registros(DELETE) <a name="4"></a>

Se realiza mediante la instrucción DELETE.

Es más sencilla que las anteriores, elimina los registros de la tabla que cumplan
la condición indicada. Ejemplo:

 ~~~SQL
DELETE FROM empleados
WHERE seccion=23;
 ~~~
 
 
 [VOLVER A ÍNDICE](#Indice)

