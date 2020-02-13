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

8. Exclusivo OR (XOR). Muestre los países que son grandes por área (más de 3 millones) o grandes por población (más de 250 millones) pero no ambos. Mostrar nombre, población y área.

- Australia tiene un área grande pero una población pequeña, debería incluirse .
- Indonesia tiene una gran población pero un área pequeña, debería incluirse .
- China tiene una gran población y una gran área, debería excluirse .
- Reino Unido tiene una población pequeña y un área pequeña, debería excluirse .

```SQL
SELECT name, population, area
FROM world
WHERE  area >3000000 XOR population > 250000000
```

9.  Muestre el namey populationen millones y el PIB en miles de millones para los países de continent'América del Sur'. Use la función 
    REDONDEAR para mostrar los valores con dos decimales.

Para América del Sur, muestra la población en millones y el PIB en miles de millones, ambos con 2 decimales.
Millones y miles de millones
Dividir por 1000000 (6 ceros) por millones. Dividir por 1000000000 (9 ceros) por miles de millones..

```SQL
SELECT name, continent, population 
FROM world
```
