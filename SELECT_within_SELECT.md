
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


7. Encuentre el país más grande (por área) en cada continente, muestre el continente , el nombre y el área :
~~~
SELECT continent, name, area 
FROM world x
WHERE area >= ALL
    (SELECT area
     FROM world y
     WHERE x.continent= y.continent
          AND area>0)
~~~


8. Enumere cada continente y el nombre del país que aparece primero alfabéticamente.
~~~
SELECT continent, name
FROM world x
WHERE  x.name <= ALL (SELECT name 
                      FROM world y 
                      WHERE  x.continent = y.continent)
~~~

9. Encuentre los continentes donde todos los países tienen una población <= 25000000. Luego encuentre los nombres de los países asociados con estos continentes. Mostrar nombre , continente y población .

~~~
SELECT name, continent, population
FROM world x
WHERE 25000000 >= ALL(SELECT population FROM world y WHERE x.continent = y.continent AND
y.population > 0) 

~~~

10. Algunos países tienen una población más de tres veces mayor que la de cualquiera de sus vecinos (en el mismo continente). Dar a los países y continentes.

~~~
SELECT name, continent
FROM world x
WHERE population > ALL  (SELECT population*3 FROM world y WHERE x.continent = y.continent AND
y.name <> x.name) 
~~~

