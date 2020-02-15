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
   
   9.1 [SELECT basics](#SELECT-basics)
   
   9.2 [SELECT from WORLD ](#9.2 SELECT-from WORLD)
   
   9.3 [SELECT within SELECT ](#SELECT-within-SELECT )




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
---

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
---
### 9.2 SELECT from WORLD 

mundo
|nombre|continente|	zona	|población|	pib|
|---   |   ----  |  ---:  |  ---:    | ---: |
|Afganistán|	Asia|	652230|	25500100	|20343000000|
|Albania	|Europa|	28748|	2831741|	12960000000|
|Argelia|	África	|2381741|	37100000	|188681000000|
|Andorra|	Europa|	468 |	78115|	3712000000|
|Angola	|África	|1246700|	20609294|	100990000|
|...|

1.  Mostrar el nombre, el continente y la población de todos los países.

```SQL
SELECT name, continent, population 
FROM world
```

2.  Muestre el nombre de los países que tienen una población de al menos 200 millones. 200 millones es 200000000, hay ocho ceros.

```SQL
SELECT name 
FROM world
WHERE population >= 200000000
```

3.  Dar el namey el PIB per cápita de los países con una populationde al menos 200 millones de dólares.
    
    AYUDA: Cómo calcular el PIB per cápita
    El PIB per cápita es el PIB dividido por la población PIB / población

```SQL
SELECT name, gdp/population
FROM world
WHERE population >= 200000000
```

4.  Mostrar el namey populationen millones para los países de la continent"América del Sur". 
Divida la población por 1000000 para obtener la población en millones.

```SQL
SELECT name, population/1000000 AS Penes
FROM world
WHERE continent = 'South America'
```

5.  Mostrar el namey populationpara Francia, Alemania, Italia

```SQL
SELECT world.name, world.population
FROM world
WHERE  name IN ('France', 'Germany', 'Italy')
```

6.  Mostrar los países que tienen una namepalabra que incluye la palabra 'United'

```SQL
SELECT name
FROM world
WHERE  name LIKE 'United%'
```

7.  Dos formas de ser grande: un país es grande si tiene un área de más de 3 millones de kilómetros cuadrados o tiene 
    una población de más de 250 millones.

Muestre los países que son grandes por área o grandes por población. Mostrar nombre, población y área.

```SQL
SELECT name, population, area
FROM world
WHERE   area >3000000 OR population > 250000000
```

8. Exclusivo OR(XOR). Muestre los países que son grandes por área (más de 3 millones) o grandes por población (más de 250 millones) pero no ambos. Mostrar nombre, población y área.

- Australia tiene un área grande pero una población pequeña, debería incluirse .
- Indonesia tiene una gran población pero un área pequeña, debería incluirse .
- China tiene una gran población y una gran área, debería excluirse .
- Reino Unido tiene una población pequeña y un área pequeña, debería excluirse .

~~~SQL
SELECT name, population, area
FROM world
WHERE  area >3000000 XOR population > 250000000
~~~

9.  Muestre el namey populationen millones y el PIB en miles de millones para los países de continent'América del Sur'. Use la función 
    `ROUND` para mostrar los valores con dos decimales.

Para América del Sur, muestra la población en millones y el PIB en miles de millones, ambos con 2 decimales.
Millones y miles de millones
Dividir por 1000000 (6 ceros) por millones. Dividir por 1000000000 (9 ceros) por miles de millones..

```SQL
SELECT name, continent, population 
FROM world
```

10.  Muestre el namePIB per cápita para aquellos países con un PIB de al menos un billón (1000000000000; eso es 12 ceros). Redondea este      valor al 1000 más cercano.

Muestre el PIB per cápita de los países del billón de dólares a los $ 1000 más cercanos.

```SQL
SELECT name,
       ROUND(gdp / population, -3) AS 'PIB'
FROM world
WHERE gdp >= 1000000000000
```

11.  Grecia tiene la capital Atenas.
     Cada una de las cadenas 'Grecia' y 'Atenas' tiene 6 caracteres.

Muestre el nombre y la capital donde el nombre y la capital tienen el mismo número de caracteres.
  - Puede usar la función `LENGTH` para encontrar el número de caracteres en una cadena

Muestre los países que son grandes por área o grandes por población. Mostrar nombre, población y área.

```SQL
SELECT name, capital
  FROM world
 WHERE LENGTH(name) =  LENGTH(capital)
```

12.  La capital de Suecia es Estocolmo. Ambas palabras comienzan con la letra 'S'.

Muestra el nombre y la capital donde coinciden las primeras letras de cada uno. No incluya países donde el nombre y la capital sean la misma palabra.
- Puede usar la función `LEFT` para aislar el primer carácter.
- Puede usarlo <>como operador `NOT EQUALS`.

```SQL
SELECT name,capital
FROM world
WHERE LEFT(name,1)=LEFT(capital,1)
AND name<>capital

```

13.  Guinea Ecuatorial y República Dominicana tienen todas las vocales (aeiou) en el nombre. No cuentan porque tienen más de una palabra en el nombre.

Encuentra el país que tiene todas las vocales y sin espacios en su nombre.

- Puede usar la frase name NOT LIKE '%a%'para excluir caracteres de sus resultados.
- La consulta mostrada extraña países como Bahamas y Bielorrusia porque contienen al menos una 'a'

```SQL
SELECT name
   FROM world
WHERE name LIKE 'B%'
  AND name NOT LIKE '%a%'
```
---
### SELECT within SELECT 


world
|name	| continent |	area | population |	gdp |
| --- | ---- | -------- |   --------| ----- |  
| Afghanistan	| Asia|		652230 | 25500100    | 20343000000 |
| Albania	| Europe| 28748 | 25500100    | 20343000000 |
| Algeria	| Africa|2381741 | 37100000    | 188681000000 |
| Andorra	| Europe|468 | 78115    | 3712000000 |
| Angola	| Africa|	1246700 |   20609294    | 100990000000 |
| ... |

  
1. Enumere el nombre de cada país donde la población es mayor que la de 'Russia'.
  
  world(name, continent, area, population, gdp)
  
~~~SQL
SELECT name 
FROM world
WHERE population >
     (SELECT population 
      FROM world
      WHERE name='Russia');
~~~


2. Mostrar los países de Europa con un PIB per cápita mayor que 'Reino Unido'.
    PIB per cápita
    El PIB per cápita es el pib / población
    
~~~SQL
SELECT name
FROM world
  WHERE continent='Europe' AND gdp/population >
                                     (SELECT gdp/population 
                                      FROM world
                                      WHERE name='United Kingdom');
~~~


3. Enumere el nombre y el continente de los países de los continentes que contienen Argentina o Australia . Ordenar por nombre del país.

~~~SQL
SELECT name, continent
FROM world 
WHERE continent IN  (
                SELECT continent 
                FROM  world 
                WHERE name IN  ('Australia','Argentina')) 
ORDER BY name;   
~~~


4. ¿Qué país tiene una población que es más que Canadá pero menos que Polonia? Mostrar el nombre y la población.

~~~SQL
SELECT name, population
FROM world 
WHERE population > (SELECT population+1 FROM world WHERE name= 'Canada') AND population <
                   (SELECT population-1 FROM world WHERE name= 'Poland');

~~~


5. Alemania (población de 80 millones) tiene la mayor población de los países de Europa. Austria (población 8,5 millones) tiene el 11% de la población de Alemania.

Muestra el nombre y la población de cada país en Europa. Mostrar la población como un porcentaje de la población de Alemania.
    Lugares decimales
Puede usar la función ROUND para eliminar los lugares decimales.
    Símbolo de porcentaje%
Puede usar la función CONCAT para agregar el símbolo de porcentaje.
~~~SQL
SELECT name, CONCAT(ROUND( 100 * population / (SELECT population 
                                               FROM world 
                                               WHERE name= 'Germany'),0),'%')
FROM world 
WHERE continent= 'Europe';
~~~


6. ¿Qué países tienen un PIB mayor que todos los países de Europa? [ Solo proporcione el nombre .] (Algunos países pueden tener valores de pib NULL)

~~~SQL
SELECT name
FROM world 
WHERE  gdp > ALL (SELECT gdp 
                  FROM world 
                  WHERE continent= 'Europe' AND gdp IS NOT NULL);
~~~


7. Encuentre el país más grande (por área) en cada continente, muestre el continente , el nombre y el área :
~~~SQL
SELECT continent, name, area 
FROM world x
WHERE area >= ALL
    (SELECT area
     FROM world y
     WHERE x.continent= y.continent
          AND area>0);
~~~


8. Enumere cada continente y el nombre del país que aparece primero alfabéticamente.
~~~SQL
SELECT continent, name
FROM world x
WHERE  x.name <= ALL (SELECT name 
                      FROM world y 
                      WHERE  x.continent = y.continent);
~~~

9. Encuentre los continentes donde todos los países tienen una población <= 25000000. Luego encuentre los nombres de los países asociados con estos continentes. Mostrar nombre , continente y población .

~~~SQL
SELECT name, continent, population
FROM world x
WHERE 25000000 >= ALL(SELECT population FROM world y WHERE x.continent = y.continent AND
y.population > 0);

~~~

10. Algunos países tienen una población más de tres veces mayor que la de cualquiera de sus vecinos (en el mismo continente). Dar a los países y continentes.

~~~SQL
SELECT name, continent
FROM world x
WHERE population > ALL  (SELECT population*3 FROM world y WHERE x.continent = y.continent AND
y.name <> x.name);
~~~

