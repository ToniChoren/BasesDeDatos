
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
