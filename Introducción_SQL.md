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
   
   9.2 [SELECT from Nobel ](#SELECT-from-Nobel )
   
   9.3 [SELECT from WORLD ](#SELECT-from-WORLD )
   
   9.4 [SELECT within SELECT ](#SELECT-within-SELECT )
   
   9.5 [SUM and COUNT](#SUM-and-COUNT)
   
   9.6 [The JOIN operation](#SThe-JOIN-operation)
   
   9.7 [More JOIN operations](#More-JOIN-operations)
   
   9.8 [Using Null](#Using-Null)
   
   9.8 [Self join](#Self-join )




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
### SELECT from WORLD 

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
### SELECT from Nobel

nobel
| yr	| subject |	winner |
 |--- | ---- | -------- |     
| 1960	| Chemistry|		Willard F. Libby | 
| 1960	| Literatura| Saint-John Perse |
| 1960	| Medicine|	Sir Frank Macfarlane Burnet |
| 1960	| Medicine|	Medicine	Peter Madawar |  


  
1. Cambie la consulta que se muestra para que muestre premios Nobel para 1950.

```SQL
  SELECT yr, subjet, winner
  FROM nobel
  WHERE yr = 1950
```


2. Muestra quién ganó el premio de literatura de 1962.

```SQL
  SELECT winner
  FROM nobel
  WHERE yr = 1960
   AND subject = 'Physics'
```


3. Muestra el año y el tema que le valió a 'Albert Einstein' su premio.

```SQL
  SELECT yr, subject
  FROM nobel
  WHERE winner =  'Albert Einstein' 
```


4. Dé el nombre de los ganadores de 'Peace' desde el año 2000, incluido el 2000.

```SQL
  SELECT  winner
  FROM nobel
  WHERE subject = 'Peace' AND yr >= 2000;
```


5. Muestre todos los detalles ( año , materia , ganador ) de los ganadores del Premio de Literatura de 1980 a 1989 inclusive.

```SQL
  SELECT yr,subject,winner
  FROM nobel
  WHERE subject = 'Literature'
   AND yr BETWEEN 1980 AND 1989
```


6. Mostrar todos los detalles de los ganadores presidenciales:

- Theodore Roosevelt
- Woodrow Wilson
- Jimmy Carter
- Barack Obama

```SQL
  SELECT yr, subjet, winner
  FROM nobel
  WHERE yr = 1950
```


7. Mostrar a los ganadores con el nombre John

```SQL
  SELECT winner 
  FROM nobel
  WHERE winner LIKE 'John %';
```


8. Muestre el año, la asignatura y el nombre de los ganadores de Física de 1980 junto con los ganadores de Química de 1984.

```SQL
  SELECT *
  FROM nobel
  WHERE (subject='physics' AND yr=1980) OR
        (subject='chemistry' AND yr=1984)
```

9. Mostrar el año, el tema y el nombre de los ganadores para 1980, excluyendo Química y Medicina

```SQL
  SELECT *
  FROM nobel
  WHERE yr=1980 AND
    subject NOT IN ('Chemistry','Medicine')
```

10. Mostrar el año, el tema y el nombre de las personas que ganaron un premio de 'Medicina' en un año temprano (antes de 1910, sin incluir 1910) junto con los ganadores de un premio de 'Literatura' en un año posterior (después de 2004, incluido 2004)

```SQL
  SELECT *
  FROM nobel 
  WHERE (subject='Medicine' and yr <1910) OR
        (subject='Literature' AND yr>=2004)
```

11. Encuentra todos los detalles del premio ganado por PETER GRÜNBERG

```SQL
  SELECT *
  FROM nobel 
  WHERE winner in ('Peter Grünberg')
```

12. Encuentre todos los detalles del premio ganado por EUGENE O'NEILL

```SQL
  SELECT *
  FROM nobel 
  WHERE winner in ('Eugene O''Neill')
```

13. Enumere los ganadores, el año y el tema donde el ganador comienza con Sir . Mostrar el más reciente primero, luego por orden de nombre.

```SQL
  SELECT winner, yr, subject
  FROM nobel 
  WHERE winner LIKE 'Sir%'
  ORDER BY yr DESC, winner
```

14. La expresión sujeto IN ('Química', 'Física') se puede usar como un valor: será 0 o 1 .

Muestre los ganadores y la asignatura de 1984 ordenados por asignatura y nombre del ganador; pero enumere Química y Física al final.

```SQL
  SELECT winner, subject
  FROM nobel
  WHERE yr=1984 
  order by subject IN ('Physics','Chemistry'),subject,winner
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
---
### SUM and COUNT


world
|name	| continent |	area | population |	gdp |
| --- | ---- | -------- |   --------| ----- |  
| Afghanistan	| Asia|		652230 | 25500100    | 20343000000 |
| Albania	| Europe| 28748 | 25500100    | 20343000000 |
| Algeria	| Africa|2381741 | 37100000    | 188681000000 |
| Andorra	| Europe|468 | 78115    | 3712000000 |
| Angola	| Africa|	1246700 |   20609294    | 100990000000 |
| ... |

  
1. Mostrar la población total del mundo.
     
~~~SQL
SELECT SUM(population)
FROM world;
~~~


2. Enumere todos los continentes, solo una vez cada uno.
    
~~~SQL
SELECT DISTINCT(continent)
FROM world;
~~~


3. Dar el GDP total de África

~~~SQL
SELECT SUM(gdp)
FROM world
WHERE continent= 'Africa';
~~~


4. ¿Cuántos países tienen un área de al menos 1000000?

~~~SQL
SELECT COUNT(name)
FROM world
WHERE area  > 1000000;
~~~


5.¿Cuál es la población total de ('Estonia', 'Letonia', 'Lituania') 

~~~SQL
SELECT SUM(population)
FROM world
WHERE name IN   ('Estonia', 'Latvia', 'Lithuania');
~~~

Usando GROUP BY y HAVING
6. Para cada continente, muestre el continente y el número de países.

~~~SQL
SELECT continent, COUNT(name)
FROM world
GROUP BY(continent);
~~~


7. Para cada continente, muestre el continente y el número de países con poblaciones de al menos 10 millones.
~~~SQL
SELECT continent, COUNT(name)
FROM world
WHERE population >= 10000000
GROUP BY(continent);
~~~


8. Enumere los continentes que tienen una población total de al menos 100 millones.
~~~SQL
SELECT continent
FROM world
GROUP BY continent
HAVING SUM(population)>= 100000000;
~~~
---
### The JOIN operation

game
|id	| mdate |	stadium | team1 |	team2 |
| --- | ---- | -------- |   --------| ----- |  
| 1001	| 8 June 2012|		National Stadium, Warsaw | POL    | GRE |
| 1002	| 8 June 2012| Stadion Miejski (Wroclaw) | RUS    | CZE |
| 1003	| 12 June 2012| Stadion Miejski (Wroclaw) | GRE    | CZE |
| 1004	| 12 June 2012| National Stadium, Warsaw | POL    | RUS |
| ... |



goal
|matchid|	teamid	|player	| gtime |
| ----  | -----   | ---   | ---- |
|1001|	POL |	Robert Lewandowski|	17|
|1001	|GRE	|Dimitris Salpingidis|	51|
|1002|	RUS|	Alan Dzagoev	|15|
|1002|	RUS	|Roman Pavlyuchenko|	82|


eteam
|id	|teamname	|coach|
|---|---|---|
|POL|	Poland|	Franciszek| Smuda|
|RUS|	Russia|	Dick |Advocaat|
|CZE|	Czech| Republic|	Michal Bilek|
|GRE|	Greece|	Fernando Santos|
...


1. El primer ejemplo muestra el gol marcado por un jugador con el apellido 'Bender'. El *dice que enumere todas las columnas de la tabla, una forma más corta de decirmatchid, teamid, player, gtime

Modifíquelo para mostrar el matchid y el nombre del jugador para todos los goles marcados por Alemania. Para identificar jugadores alemanes, verifique: teamid = 'GER'

~~~SQL
SELECT goal.matchid, goal.player
FROM goal  
  WHERE teamid = 'GER';
~~~

2. De la consulta anterior puedes ver que Lars Bender anotó un gol en el juego 1012. Ahora queremos saber qué equipos estaban jugando en ese partido.

Observe en el que la columna matchiden la goaltabla corresponde a la idcolumna en la gametabla. Podemos buscar información sobre el juego 1012 al encontrar esa fila en la tabla de juegos .

Mostrar id, estadio, equipo1, equipo2 solo para el juego 1012

~~~SQL
SELECT game.id, game.stadium, game.team1, game.team2
FROM game
WHERE id = '1012';
~~~

3. Modifíquelo para mostrar el jugador, teamid, estadio y mdate para cada gol alemán.

~~~SQL
SELECT goal.player, goal.teamid, game.stadium, game.mdate
  FROM game JOIN goal ON (id=matchid)
WHERE teamid= 'Ger';
~~~
4. Muestra al equipo1, al equipo2 y al jugador por cada gol marcado por un jugador llamado Mario player LIKE 'Mario%'

~~~SQL
SELECT  game.team1, game.team2,  goal.player
FROM game JOIN goal ON (id=matchid)
WHERE goal.player LIKE 'Mario%';
~~~

5. Mostrar player, teamid, coach, gtimepara todos los goles marcados en los primeros 10 minutosgtime<=10

~~~SQL
SELECT player, teamid, coach, gtime
  FROM goal JOIN eteam ON (teamid=id)
 WHERE gtime<=10;

~~~

6. Enumere las fechas de los partidos y el nombre del equipo en el que 'Fernando Santos' fue el entrenador del equipo1.

~~~SQL
SELECT game.mdate, eteam.teamname
  FROM game JOIN eteam ON (team1=eteam.id)
 WHERE coach ='Fernando Santos';
~~~

7. Enumere al jugador por cada gol marcado en un juego donde el estadio fue 'Estadio Nacional, Varsovia'

~~~SQL
SELECT player
  FROM goal JOIN game ON (id=matchid)
 WHERE stadium = 'National Stadium, Warsaw';
~~~


8. En su lugar, muestre el nombre de todos los jugadores que marcaron un gol contra Alemania.

~~~SQL
SELECT DISTINCT goal.player
  FROM game JOIN goal ON matchid = id 
    WHERE (team1='GER' OR team2='GER') AND teamid <> 'GER';
~~~


9. Muestra el nombre del equipo y el número total de goles marcados.

~~~SQL
SELECT teamname, COUNT(teamid)
  FROM eteam JOIN goal ON id=teamid
 ORDER BY teamname;
~~~

10. Muestra el estadio y la cantidad de goles marcados en cada estadio.

~~~SQL
SELECT game.stadium,COUNT(1)
  FROM goal JOIN game ON id=matchid
GROUP BY stadium;
~~~

11. Para cada partido que involucre 'POL', muestre el matchid, la fecha y el número de goles marcados.

~~~SQL
SELECT matchid, mdate, COUNT(teamid)
  FROM game JOIN goal ON matchid = id 
 WHERE (team1 = 'POL' OR team2 = 'POL')
GROUP BY matchid, mdate;
~~~

12. Muestra el estadio y la cantidad de goles marcados en cada estadio.

~~~SQL
SELECT matchid, mdate, COUNT(teamid)
  FROM game JOIN goal ON matchid = id 
 WHERE (teamid= 'GER')
GROUP BY matchid, mdate;
~~~

13. Enumere cada partido con los goles marcados por cada equipo como se muestra. Esto usará " CASO CUANDO " que no se ha explicado en ningún ejercicio anterior.

~~~SQL
SELECT mdate,
  team1,
  SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  team2,
  SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
  FROM game LEFT JOIN goal ON matchid = id
GROUP BY mdate,matchid,team1,team2;
~~~
---
  movie
| id |	title |	yr |	director |	budget	| gross |
| ---|  --- |   --- |   ---   |   ----   |  ----  |


actor
|id	|name|
|  ---|  --- |


casting
| movieid	| actorid |	ord |
|--- | --- | --- |


1. Listar las películas donde está el año 1962 [Show id , title ]
~~~SQL
SELECT id, title
 FROM movie
 WHERE yr=1962;
~~~

2. Dar año de 'Ciudadano Kane'.
~~~SQL
SELECT movie.yr
FROM movie
WHERE movie.title = 'Citizen Kane';
~~~

3. Enumere todas las películas de Star Trek, incluya la identificación , el título y el año (todas estas películas incluyen las 
   palabras Star Trek en el título). Ordenar resultados por año.
~~~SQL
SELECT id, title, yr
FROM movie
 WHERE title LIKE 'Star Trek%'
ORDER BY yr ASC;
~~~

4. ¿Qué número de identificación tiene el actor 'Glenn Close'?
~~~SQL
SELECT actor.id
FROM  actor
 WHERE  name = 'Glenn Close';
~~~

5. ¿Cuál es el id de la película 'Casablanca'
~~~SQL
SELECT movie.id
FROM  movie
WHERE  movie.title = 'Casablanca';
~~~

6. Obtenga la lista de actores de 'Casablanca'.

¿Qué es una lista de reparto?
Use movieid = 11768 , (o el valor que obtuvo de la pregunta anterior)
~~~SQL
SELECT actor.name
FROM  actor JOIN casting ON actor.id = casting.actorid
WHERE  casting.movieid = (  
                   SELECT movie.id
                   FROM   movie
                   WHERE  movie.title ='Casablanca');
~~~

7. Obtenga la lista de actores de la película 'Alien'
~~~SQL
SELECT actor.name
FROM  movie  JOIN casting  ON movie.id = casting.movieid JOIN
      actor ON actor.id = casting.actorid
WHERE movie.title = 'Alien';
~~~

8. Enumere las películas en las que ha aparecido 'Harrison Ford'
~~~SQL
SELECT movie.title
FROM  movie JOIN casting ON movie.id = casting.movieid 
            JOIN actor ON actor.id = casting.actorid
WHERE actor.name =  'Harrison Ford';
~~~

9. Enumere las películas donde ha aparecido 'Harrison Ford', pero no en el papel protagonista. [Nota: el campo ord del casting da 
   la posición del actor. Si ord = 1, entonces este actor está en el papel protagonista]
~~~SQL
SELECT movie.title
FROM  movie, casting, actor
WHERE actor.name  =  'Harrison Ford' 
    AND movie.id = movieid
    AND actor.id = actorid 
    AND ord <> 1 ;
~~~

10. Enumere las películas junto con la estrella principal de todas las películas de 1962.
~~~SQL
SELECT movie.title, actor.name
FROM  movie JOIN casting ON movie.id = casting.movieid 
            JOIN actor ON actor.id = casting.actorid
WHERE movie.yr = 1962 
AND casting.ord = 1;
~~~

11. Cuáles fueron los años más ocupados para 'Rock Hudson', muestran el año y la cantidad de películas que hizo cada año durante 
    cualquier año en el que hizo más de 2 películas.
~~~SQL
SELECT movie.yr, COUNT(movie.title) 
FROM
  movie JOIN casting ON movie.id= casting.movieid
        JOIN actor   ON actor.id= casting.actorid
WHERE actor.name='Rock Hudson'
GROUP BY movie.yr 
HAVING COUNT(*) > 2;
~~~

12. Liste el título de la película y el actor principal de todas las películas en las que 'Julie Andrews' jugó.
~~~SQL
SELECT movie.title, actor.name 
FROM  movie JOIN casting ON movie.id= casting.movieid
            JOIN actor   ON actor.id= casting.actorid
WHERE casting.ord = 1 AND movie.id IN (
  SELECT casting.movieid  
  FROM actor JOIN casting ON actor.id = casting.actorid
  WHERE actor.name='Julie Andrews');
~~~

13. Obtenga una lista, en orden alfabético, de los actores que han tenido al menos 15 papeles protagonistas .
~~~SQL
SELECT name
    FROM casting JOIN actor
      ON  actorid = actor.id
    WHERE ord=1
    GROUP BY name
    HAVING COUNT(movieid)>=15;
~~~


14. Enumere las películas lanzadas en el año 1978 ordenadas por el número de actores en el elenco, luego por título.
~~~SQL
  SELECT title, COUNT(actorid)
  FROM casting,movie                
  WHERE yr=1978
        AND movieid=movie.id
  GROUP BY title
  ORDER BY 2 DESC,1 ASC;

~~~

15. Lista de todas las personas que han trabajado con 'Art Garfunkel'.
~~~SQL
SELECT DISTINCT d.name
FROM actor d JOIN casting a ON (a.actorid=d.id)
   JOIN casting b on (a.movieid=b.movieid)
   JOIN actor c on (b.actorid=c.id 
                and c.name='Art Garfunkel');
  WHERE d.id!=c.id
~~~

---
###  Using Null

teacher
| id	| dept	| name |	phone |	mobile |
|---|---|---|---|---|
|101	|1	|Shrivell	|2753|	07986 |555 |1234|
|102|	1|	Throd|	2754|	07122 |555| 1920|
|103	|1	| Splint	| 2293 |	
| 104| 	|	Spiregrain|	3287	|
|105	|  2| Cutflower |	3212	| 07996 555 6574|
|106|		|Deadyawn|	3345|	     |
|...|

dept
|id	| name|
|--- |--- |
|1	|Computing|
|2	|Design|
|3	|Engineering|
|...|


1. Enumere los maestros que tienen NULL para su departamento.

Por qué no podemos usar =
Puede pensar que la frase dept = NULL funcionaría aquí, pero no funciona; puede usar la frase dept IS NULL
~~~SQL
SELECT name
FROM teacher
WHERE dept IS NULL;
~~~


2. Tenga en cuenta que INNER JOIN extraña a los maestros sin departamento y a los departamentos sin maestro.

~~~SQL
SELECT teacher.name, dept.name
 FROM teacher INNER JOIN dept
           ON (teacher.dept=dept.id);
~~~

3. Use una UNIÓN diferente para que todos los maestros estén en la lista.

~~~SQL
SELECT teacher.name, dept.name
FROM teacher 
LEFT JOIN dept ON (teacher.dept=dept.id);

~~~


4. Use una UNIÓN diferente para que todos los departamentos estén listados.

~~~SQL
SELECT teacher.name, dept.name
FROM teacher 
RIGHT JOIN dept ON (teacher.dept=dept.id);
~~~

5. Use COALESCE para imprimir el número de móvil. Utilice el número '07986 444 2266' si no se proporciona ningún número. Mostrar nombre del profesor y número de teléfono móvil o '07986444 2266'

~~~SQL
SELECT name, COALESCE(mobile,'07986 444 2266')
FROM teacher;
~~~

6. Use la función COALESCE y una IZQUIERDA PARA imprimir el nombre del maestro y el nombre del departamento. Use la cadena 'Ninguno' donde no hay departamento.

~~~SQL
SELECT teacher.name, COALESCE(dept.name,'None')
FROM teacher LEFT JOIN dept
ON teacher.dept=dept.id;
~~~

7. Use COUNT para mostrar la cantidad de maestros y la cantidad de teléfonos móviles.

~~~SQL
SELECT COUNT(teacher.name), COUNT(mobile)
FROM teacher;
~~~

8. Use COUNT y GROUP BY dept.name para mostrar cada departamento y la cantidad de personal. Use una UNIÓN DERECHA para asegurarse de que el departamento de Ingeniería esté en la lista.

~~~
SELECT dept.name, COUNT(teacher.name)SQL
FROM teacher RIGHT JOIN dept
ON teacher.dept=dept.id
GROUP BY dept.name;
~~~

Usando CASE
9. Use CASE para mostrar el nombre de cada maestro seguido de 'Sci' si el maestro está en el departamento 1 o 2 y 'Art' de lo contrario.

~~~SQL
SELECT name, CASE WHEN dept IN (1,2)
THEN 'Sci'
ELSE 'Art' END
FROM teacher;
~~~

10. Use CASE para mostrar el nombre de cada maestro seguido de 'Sci' si el maestro está en el departamento 1 o 2, muestre 'Art' si el departamento del maestro es 3 y 'Ninguno' de lo contrario.

~~~SQL
SELECT name, CASE WHEN dept IN (1,2) 
THEN 'Sci'
WHEN dept = 3 
THEN 'Art'
ELSE 'None' END
FROM teacher;
~~~
---
### Self join 

|stops|
| --- |
|id|
|name|


|route|
| --- |
|num|
|company|
|pos|
|stop|


1. Cuántas paradas hay en la base de datos.

~~~SQL
SELECT COUNT(*) 
FROM stops;
~~~

2. Encuentra el valor de id para la parada 'Craiglockhart'

~~~SQL
SELECT id 
FROM stops 
WHERE name='Craiglockhart';
~~~

3. Dé la identificación y el nombre de las paradas en el servicio '4' 'LRT'.

~~~SQL
SELECT id, name FROM stops, route
  WHERE id=stop
    AND company='LRT'
    AND num='4';
~~~

4. La consulta que se muestra proporciona el número de rutas que visitan London Road (149) o Craiglockhart (53). Ejecute la consulta y observe que los dos servicios que vinculan estas paradas tienen un recuento de 2. Agregue una cláusula HAVING para restringir la salida a estas dos rutas.

~~~SQL
SELECT company, num, COUNT(*)
FROM route WHERE stop=149 OR stop=53
GROUP BY company, num
HAVING COUNT(*)=2;
~~~

5 Ejecute la unión automática que se muestra y observe que b.stop le ofrece todos los lugares a los que puede llegar desde Craiglockhart, sin cambiar las rutas. Cambie la consulta para que muestre los servicios de Craiglockhart a London Road.

~~~SQL
SELECT a.company, a.num, a.stop, b.stop
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
WHERE a.stop = 53 AND b.stop=149;
~~~

6. La consulta que se muestra es similar a la anterior, sin embargo, al unir dos copias de la tabla de paradas podemos referirnos a las paradas por nombre en lugar de por número. Cambie la consulta para que se muestren los servicios entre 'Craiglockhart' y 'London Road'. Si estás cansado de estos lugares, prueba 'Fairmilehead' contra 'Tollcross'

~~~SQL
SELECT a.company, a.num, stopa.name, stopb.name
FROM route a JOIN route b ON
  (a.company=b.company AND a.num=b.num)
  JOIN stops stopa ON (a.stop=stopa.id)
  JOIN stops stopb ON (b.stop=stopb.id)
WHERE stopa.name='Craiglockhart'
  AND stopb.name='London Road';
~~~

7. Dé una lista de todos los servicios que conectan las paradas 115 y 137 ('Haymarket' y 'Leith')

~~~SQL
SELECT DISTINCT R1.company, R1.num
FROM route R1, route R2
WHERE R1.num=R2.num AND R1.company=R2.company
    AND R1.stop=115 AND R2.stop=137
~~~

8. Dé una lista de los servicios que conectan las paradas 'Craiglockhart' y 'Tollcross'
~~~SQL
SELECT R1.company, R1.num
FROM route R1, route R2, stops S1, stops S2
WHERE R1.num=R2.num AND R1.company=R2.company
    AND R1.stop=S1.id AND R2.stop=S2.id
    AND S1.name='Craiglockhart'
    AND S2.name='Tollcross';
~~~

9. Proporcione una lista distinta de las paradas a las que se puede llegar desde 'Craiglockhart' tomando un autobús, incluido 'Craiglockhart', ofrecido por la compañía LRT. Incluya la compañía y el autobús no. de los servicios relevantes.

~~~SQL
SELECT DISTINCT S2.name, R2.company, R2.num
FROM stops S1, stops S2, route R1, route R2
WHERE S1.name='Craiglockhart'
  AND S1.id=R1.stop
  AND R1.company=R2.company AND R1.num=R2.num
  AND R2.stop=S2.id
~~~

---
