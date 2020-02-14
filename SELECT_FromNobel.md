
nobel
| yr	| subject |	winner |
 |--- | ---- | -------- |     
| 1960	| Chemistry|		Willard F. Libby | 
| 1960	| Literatura| Saint-John Perse |
| 1960	| Medicine|	Sir Frank Macfarlane Burnet |
| 1960	| Medicine|	Medicine	Peter Madawar |  


  
1. Cambie la consulta que se muestra para que muestre premios Nobel para 1950.

~~~
SELECT yr, subjet, winner
FROM nobel
WHERE yr = 1950
~~~


2. Muestra quién ganó el premio de literatura de 1962.

~~~
SELECT winner
  FROM nobel
 WHERE yr = 1960
   AND subject = 'Physics'
~~~


3. Muestra el año y el tema que le valió a 'Albert Einstein' su premio.

~~~
SELECT yr, subject
FROM nobel
 WHERE winner =  'Albert Einstein' 
   
~~~


4. Dé el nombre de los ganadores de 'Peace' desde el año 2000, incluido el 2000.

~~~
SELECT  winner
FROM nobel
WHERE subject = 'Peace' AND yr >= 2000;
~~~


5. Muestre todos los detalles ( año , materia , ganador ) de los ganadores del Premio de Literatura de 1980 a 1989 inclusive.

~~~
SELECT yr,subject,winner
FROM nobel
WHERE subject = 'Literature'
AND yr BETWEEN 1980 AND 1989
~~~


6. Mostrar todos los detalles de los ganadores presidenciales:

- Theodore Roosevelt
- Woodrow Wilson
- Jimmy Carter
- Barack Obama

~~~
SELECT yr, subjet, winner
FROM nobel
WHERE yr = 1950
~~~


1. Cambie la consulta que se muestra para que muestre premios Nobel para 1950.

~~~
SELECT * 
FROM nobel
 WHERE  winner IN ('Theodore Roosevelt',
  'Woodrow Wilson',
  'Jimmy Carter',
  'Barack Obama')
~~~


1. Cambie la consulta que se muestra para que muestre premios Nobel para 1950.

~~~
SELECT yr, subjet, winner
FROM nobel
WHERE yr = 1950
~~~

