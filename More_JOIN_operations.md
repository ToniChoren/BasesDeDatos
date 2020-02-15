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
