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
~~~
SELECT name
FROM teacher
WHERE dept IS NULL
~~~


2. Tenga en cuenta que INNER JOIN extraña a los maestros sin departamento y a los departamentos sin maestro.

~~~
SELECT teacher.name, dept.name
 FROM teacher INNER JOIN dept
           ON (teacher.dept=dept.id)
~~~

3. Use una UNIÓN diferente para que todos los maestros estén en la lista.

~~~
SELECT teacher.name, dept.name
FROM teacher 
LEFT JOIN dept ON (teacher.dept=dept.id)

~~~


4. Use una UNIÓN diferente para que todos los departamentos estén listados.

~~~
SELECT teacher.name, dept.name
FROM teacher 
RIGHT JOIN dept ON (teacher.dept=dept.id)
~~~

5. Use COALESCE para imprimir el número de móvil. Utilice el número '07986 444 2266' si no se proporciona ningún número. Mostrar nombre del profesor y número de teléfono móvil o '07986444 2266'

~~~
SELECT name, COALESCE(mobile,'07986 444 2266')
FROM teacher
~~~

6. Use la función COALESCE y una IZQUIERDA PARA imprimir el nombre del maestro y el nombre del departamento. Use la cadena 'Ninguno' donde no hay departamento.

~~~
SELECT teacher.name, COALESCE(dept.name,'None')
FROM teacher LEFT JOIN dept
ON teacher.dept=dept.id
~~~

7. Use COUNT para mostrar la cantidad de maestros y la cantidad de teléfonos móviles.

~~~
SELECT COUNT(teacher.name), COUNT(mobile)
FROM teacher
~~~

8. Use COUNT y GROUP BY dept.name para mostrar cada departamento y la cantidad de personal. Use una UNIÓN DERECHA para asegurarse de que el departamento de Ingeniería esté en la lista.

~~~
SELECT dept.name, COUNT(teacher.name)
FROM teacher RIGHT JOIN dept
ON teacher.dept=dept.id
GROUP BY dept.name
~~~

Usando CASE
9. Use CASE para mostrar el nombre de cada maestro seguido de 'Sci' si el maestro está en el departamento 1 o 2 y 'Art' de lo contrario.

~~~
SELECT name, CASE WHEN dept IN (1,2) 
THEN 'Sci'
ELSE 'Art' END
FROM teacher
~~~

10. Use CASE para mostrar el nombre de cada maestro seguido de 'Sci' si el maestro está en el departamento 1 o 2, muestre 'Art' si el departamento del maestro es 3 y 'Ninguno' de lo contrario.

~~~
SELECT name, CASE WHEN dept IN (1,2) 
THEN 'Sci'
WHEN dept = 3 
THEN 'Art'
ELSE 'None' END
FROM teacher
~~~
