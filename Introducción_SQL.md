# INDICE

1. [Introducción](#1-Introduccion)
2. [Componentes del SQL](#2-Componentes-del-SQL)
3. [Sublenguajes SQL](#3-Sublenguajes)
4. [Cláusulas](#4-Clausulas)
5. [Operadores Lógicos](#5-Operadores-Logicos)
6. [Operadores de Comparación](#6-Operadores-de-Comparacion)
7. [Funciones de Agregado](#7-Funciones-de-Agregado-o-reductoras)
8. [Funciones](#8-Funciones)
9. [SQLZOO](#9-SQLZOO)



### 1 Introduccion

El  lenguaje de consulta estructurado (****SQL****)  
es un lenguaje de base de datos normalizado, utilizado por el motor de base  
de datos de Microsoft Jet.  **SQL**  
se utiliza para crear objetos QueryDef, como el argumento de origen del método  
OpenRecordSet y como la propiedad RecordSource del control de datos. También  
se puede utilizar con el método Execute para crear y manipular directamente  
las bases de datos Jet y crear consultas  **SQL**  
de paso a través para manipular bases de datos remotas cliente – servidor.

### 2 Componentes del SQL

El  lenguaje  **SQL**  está compuesto por comandos, cláusulas, operadores  
y funciones de agregado. Estos elementos se combinan en las instrucciones para  
crear, actualizar y manipular las bases de datos.

### 3 Sublenguajes 

Existen  6 tipos de sublenguajes  **SQL**:

-   DQL(Data Query Lenguaje)
-   DML (Data Manipulation Lenguaje) que permiten crear y definir nuevas bases de datos, campos e índices.
-   DDL (Data Definition Lenguaje) que permiten generar consultas para ordenar, filtrar y extraer datos  
    de la base de datos.
-   TCL (Transation Control Lenguaje) 
-   DCL (Data Control) Lenguaje)
-   SCL (Session Control Lenguaje)

El núcleo central de SQL está compuestos por: 
DQL, DML, DDL

|****DQL**** | |
| --- | --- |
| SELECT | es el más difícil, y opera sobre datos|

|****DML**** | |
| --- | --- |
|SELECT| esta sentencia se utiliza para realizar consultas sobre los datos|
|INSERT| con esta instrucción podemos insertar los valores en una base de datos|
|UPDATE| sirve para modificar los valores de uno o varios registros|
|DELETE| se utiliza para eliminar las finas de una tabla|

|****DDL**** | |
| --- | --- |
|CREATE| Utilizado para crear nuevas tablas, campos e índices|
|DROP| Empleado para eliminar tablas e índices|
|ALTER| Utilizado para modificar las tablas agregando campos o cambiando la definición de los campos|


|****DCL**** | |
| --- | --- |
|GRANT| permite otorgar permisos|
|REVOKE| elimina los permisos que previamente se han concedido|


|****TCL**** | |
| --- | --- |
|COMMIT| Finaliza la transacción y realiza los cambios hechos durante la transacción. Las transacción bloqueadas sobre la tabla           quedan liberadas.|
|ROLLBACK| Rechaza la transacción y no aplica cambios, volviendo al estado antes de iniciarse la transacción|

|****SCL**** |  |
| --- | --- |
|ALTER | Utilizado para modificar las tablas agregando campos o cambiando la definición de los campos|
|SESSION| |



### 4 Clausulas

Las cláusulas son condiciones de modificación utilizadas para  
definir los datos que desea seleccionar o manipular.

|**Comando** | **Descripción**|
| --- | --- |
|**FROM**| Utilizada para especificar la tabla de la cual se van a seleccionar los registros|
|**WHERE**|Utilizada para especificar las condiciones que deben reunir los registros que se van a seleccionar|
|**GROUP  BY**|Utilizada para  agrupar en sub-tablas los valores repetidos de un atributo.|
|**HAVING**|HAVING se usa junto con GROUP BY para filtrar las tuplas de cada sub-tabla |
|**ORDER  BY**|Utilizada para ordenar los registros seleccionados de acuerdo con un orden específico,pudiendo hacerse de manera ascendiente y descendiente.|

### 5 Operadores Logicos

|**Operador**  |  **Uso**|
|---|---|
|**AND**|Es  el “y” lógico. Evalúa dos condiciones y devuelve un valor de verdad sólo si ambas son ciertas|
|**OR**|Es  el “o” lógico. Evalúa dos condiciones y devuelve un valor de verdad si alguna de las dos es cierta|
|**NOT**|Negación  lógica. Devuelve el valor contrario de la expresión|

### 6 Operadores de Comparacion

|**Operador** | **Uso**|
|---|---|
|**<**|Menor que|
|**>**|Mayor  que|
|**<>**|Distinto  de|
|**<=**|Menor  ó Igual que|
|**>=**|Mayor  ó Igual que|
|**BETWEEN**|Utilizado para especificar un intervalo de valores|
|**LIKE**|Utilizado en la comparación de un modelo|
|**IN**|Utilizado para especificar registros de una base de datos|

### 7 Funciones de Agregado o reductoras

Las  funciones de agregado se usan dentro de una cláusula  **SELECT**  o en el HAVING del GROUP BY
en grupos de registros para devolver un único valor que se aplica a un  
grupo de registros.
Además todas ignoran valores *NULL*

|**Comando** |**Descripción**|
| --- | --- |
|**AVG**|Utilizada para calcular el promedio de los valores de un campo determinado|
|**COUNT**|Utilizada para devolver el número de registros de la selección|
|**SUM**|Utilizada para devolver la suma de todos los valores de un campo determinado|
|**MAX**|Utilizada para devolver el valor más alto de un campo especificado|
|**MIN**|Utilizada para devolver el valor más bajo de un campo especificado|

> Cuando se usa una función reductora en el SELECT, función `AS` renombra el resultado de la consulta para que no se vea el nombre de la función.

### 8 Funciones

|**Comando** |**Descripción**|
| --- | --- |
|**CONCAT**|concatena cadenas de texto o valores de un campo|
|**ROUND**|redondea el número que se le pasa como primer parámetro. El segundo parámetro será el número de decimales |
|**REPLACE**|reemplazar caracteres dentro de una cadena. Requiere tres argumentos|
|**LENGTH**|devuelve el largo o número de caracteres de la cadena |
|**LEFT**|devuelve una sub-cadena de la cadena que se le pasa como primer parámetro|
|**AS**| renombrar un determinado campo, pudiendo usar el nuevo nombre en el resto de la consulta. Se suele utilizar en el `SELECT` para devolver el nombre del atributo que queramos y en el `FROM` cuando se trabaja con varias tablas.|
|**DISTINCT**| se emplea en el `SELECT` antes de un atributo para indicar que omita los valores repetidos de este mismo|

# 9 SQLZOO
### SELECT basics

mundo
|nombre|continente|	zona	|población|	pib|
|---   |   ----  |  ---   |  ---    | ---|
|Afganistán|	Asia|	652230|	25500100	|20343000000|
|Albania	|Europa|	28748|	2831741|	12960000000|
|Argelia|	África	|2381741|	37100000	|188681000000|
|Andorra|	Europa|	468	78115|	3712000000|
|Angola	|África	|1246700|	20609294|	100990000|
|...|


1. El ejemplo utiliza una cláusula `WHERE`  para mostrar la población de 'Francia'. 
Tenga en cuenta que las cadenas (fragmentos de texto que son datos) deben estar entre 'comillas simples';

```SQL
SELECT population 
from world
where name = 'Germany'
```

2. Verificación de una lista La palabra `IN` nos permite verificar si un elemento está en una lista. El ejemplo muestra el nombre y la población de los países 'Brasil', 'Rusia', 'India' y 'China'.

Mostrar el nombre y la población de 'Suecia', 'Noruega' y 'Dinamarca'.

```SQL
SELECT name, population 
FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```

3. ¿Qué países no son demasiado pequeños ni demasiado grandes? `BETWEEN` permite la verificación del rango (el rango especificado incluye los valores límite). El siguiente ejemplo muestra países con un área de 250,000-300,000 km2. Modifíquelo para mostrar el país y el área para países con un área entre 200,000 y 250,000..

```SQL
SELECT name, area 
FROM world
WHERE area BETWEEN 200000 AND 250000
```



