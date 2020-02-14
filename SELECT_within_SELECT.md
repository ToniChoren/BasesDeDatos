
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
  
~~~
SELECT name 
FROM world
WHERE population >
     (SELECT population 
      FROM world
      WHERE name='Russia')
~~~


2. Mostrar los países de Europa con un PIB per cápita mayor que 'Reino Unido'.
    PIB per cápita
    El PIB per cápita es el pib / población
~~~
SELECT name
FROM world
  WHERE continent='Europe' AND gdp/population >
                                     (SELECT gdp/population 
                                      FROM world
                                      WHERE name='United Kingdom')
~~~


3. Enumere el nombre y el continente de los países de los continentes que contienen Argentina o Australia . Ordenar por nombre del país.

~~~
SELECT name, continent
FROM world 
WHERE continent IN  (
                SELECT continent 
                FROM  world 
                WHERE name IN  ('Australia','Argentina')) 
ORDER BY name;   
~~~


4. ¿Qué país tiene una población que es más que Canadá pero menos que Polonia? Mostrar el nombre y la población.

~~~
SELECT name, population
FROM world 
WHERE population > (SELECT population+1 FROM world WHERE name= 'Canada') AND population <
                   (SELECT population-1 FROM world WHERE name= 'Poland')

~~~


5. Alemania (población de 80 millones) tiene la mayor población de los países de Europa. Austria (población 8,5 millones) tiene el 11% de la población de Alemania.

Muestra el nombre y la población de cada país en Europa. Mostrar la población como un porcentaje de la población de Alemania.
    Lugares decimales
Puede usar la función ROUND para eliminar los lugares decimales.
    Símbolo de porcentaje%
Puede usar la función CONCAT para agregar el símbolo de porcentaje.
~~~
SELECT name, CONCAT(ROUND(
100 * population / (SELECT population 
                    FROM world 
                    WHERE name= 'Germany'),0),'%')
FROM world 
WHERE continent= 'Europe'
~~~


6. ¿Qué países tienen un PIB mayor que todos los países de Europa? [ Solo proporcione el nombre .] (Algunos países pueden tener valores de pib NULL)

~~~
SELECT name
FROM world 
WHERE  gdp > ALL (SELECT gdp 
                  FROM world 
                  WHERE continent= 'Europe' AND gdp IS NOT NULL)
~~~


7. Mostrar a los ganadores con el nombre John

~~~
SELECT winner 
FROM nobel
  WHERE winner LIKE 'John %';
~~~


8. Muestre el año, la asignatura y el nombre de los ganadores de Física de 1980 junto con los ganadores de Química de 1984.
~~~
SELECT *
FROM nobel
WHERE (subject='physics' AND yr=1980) OR
      (subject='chemistry' AND yr=1984)
~~~

9. Mostrar el año, el tema y el nombre de los ganadores para 1980, excluyendo Química y Medicina

~~~
SELECT *
FROM nobel
WHERE yr=1980 AND
  subject NOT IN ('Chemistry','Medicine')

~~~

10. Mostrar el año, el tema y el nombre de las personas que ganaron un premio de 'Medicina' en un año temprano (antes de 1910, sin incluir 1910) junto con los ganadores de un premio de 'Literatura' en un año posterior (después de 2004, incluido 2004)

~~~
SELECT *
FROM nobel 
WHERE (subject='Medicine' and yr <1910) OR
      (subject='Literature' AND yr>=2004)
~~~

11. Encuentra todos los detalles del premio ganado por PETER GRÜNBERG

~~~
SELECT *
FROM nobel 
WHERE winner in ('Peter Grünberg')
~~~

12. Encuentre todos los detalles del premio ganado por EUGENE O'NEILL

~~~
SELECT *
FROM nobel 
WHERE winner in ('Eugene O''Neill')
~~~

13. Enumere los ganadores, el año y el tema donde el ganador comienza con Sir . Mostrar el más reciente primero, luego por orden de nombre.

~~~
SELECT winner, yr, subject
FROM nobel 
WHERE winner LIKE 'Sir%'
ORDER BY yr DESC, winner
~~~

14. La expresión sujeto IN ('Química', 'Física') se puede usar como un valor: será 0 o 1 .

Muestre los ganadores y la asignatura de 1984 ordenados por asignatura y nombre del ganador; pero enumere Química y Física al final.

~~~
SELECT winner, subject
FROM nobel
WHERE yr=1984 
order by subject IN ('Physics','Chemistry'),subject,winner
~~~
