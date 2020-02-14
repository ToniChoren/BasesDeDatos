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

