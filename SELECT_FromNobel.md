
nobel
| yr	| subject |	winner |
 |--- | ---- | -------- |     
| 1960	| Chemistry|		Willard F. Libby | 
| 1960	| Literatura| Saint-John Perse |
| 1960	| Medicine|	Sir Frank Macfarlane Burnet |
| 1960	| Medicine|	Medicine	Peter Madawar |  


  
1. Cambie la consulta que se muestra para que muestre premios Nobel para 1950.

```
  SELECT yr, subjet, winner
  FROM nobel
  WHERE yr = 1950
```


2. Muestra quién ganó el premio de literatura de 1962.

```
  SELECT winner
  FROM nobel
  WHERE yr = 1960
   AND subject = 'Physics'
```


3. Muestra el año y el tema que le valió a 'Albert Einstein' su premio.

```
  SELECT yr, subject
  FROM nobel
  WHERE winner =  'Albert Einstein' 
```


4. Dé el nombre de los ganadores de 'Peace' desde el año 2000, incluido el 2000.

```
  SELECT  winner
  FROM nobel
  WHERE subject = 'Peace' AND yr >= 2000;
```


5. Muestre todos los detalles ( año , materia , ganador ) de los ganadores del Premio de Literatura de 1980 a 1989 inclusive.

```
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

```
  SELECT yr, subjet, winner
  FROM nobel
  WHERE yr = 1950
```


7. Mostrar a los ganadores con el nombre John

```
  SELECT winner 
  FROM nobel
  WHERE winner LIKE 'John %';
```


8. Muestre el año, la asignatura y el nombre de los ganadores de Física de 1980 junto con los ganadores de Química de 1984.
```
  SELECT *
  FROM nobel
  WHERE (subject='physics' AND yr=1980) OR
        (subject='chemistry' AND yr=1984)
```

9. Mostrar el año, el tema y el nombre de los ganadores para 1980, excluyendo Química y Medicina

```
  SELECT *
  FROM nobel
  WHERE yr=1980 AND
    subject NOT IN ('Chemistry','Medicine')
```

10. Mostrar el año, el tema y el nombre de las personas que ganaron un premio de 'Medicina' en un año temprano (antes de 1910, sin incluir 1910) junto con los ganadores de un premio de 'Literatura' en un año posterior (después de 2004, incluido 2004)

```
  SELECT *
  FROM nobel 
  WHERE (subject='Medicine' and yr <1910) OR
        (subject='Literature' AND yr>=2004)
```

11. Encuentra todos los detalles del premio ganado por PETER GRÜNBERG

```
  SELECT *
  FROM nobel 
  WHERE winner in ('Peter Grünberg')
```

12. Encuentre todos los detalles del premio ganado por EUGENE O'NEILL

```
  SELECT *
  FROM nobel 
  WHERE winner in ('Eugene O''Neill')
```

13. Enumere los ganadores, el año y el tema donde el ganador comienza con Sir . Mostrar el más reciente primero, luego por orden de nombre.

```
  SELECT winner, yr, subject
  FROM nobel 
  WHERE winner LIKE 'Sir%'
  ORDER BY yr DESC, winner
```

14. La expresión sujeto IN ('Química', 'Física') se puede usar como un valor: será 0 o 1 .

Muestre los ganadores y la asignatura de 1984 ordenados por asignatura y nombre del ganador; pero enumere Química y Física al final.

```
  SELECT winner, subject
  FROM nobel
  WHERE yr=1984 
  order by subject IN ('Physics','Chemistry'),subject,winner
```
