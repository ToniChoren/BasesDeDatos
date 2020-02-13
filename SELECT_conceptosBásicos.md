1. El ejemplo utiliza una cláusula WHERE para mostrar la población de 'Francia'. 
Tenga en cuenta que las cadenas (fragmentos de texto que son datos) deben estar entre 'comillas simples';

```SQL
SELECT population 
from world
where name = 'Germany'
```

2. Verificación de una lista La palabra IN nos permite verificar si un elemento está en una lista. El ejemplo muestra el nombre y la población de los países 'Brasil', 'Rusia', 'India' y 'China'.

Mostrar el nombre y la población de 'Suecia', 'Noruega' y 'Dinamarca'.

```SQL
SELECT name, population 
FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```

3. ¿Qué países no son demasiado pequeños ni demasiado grandes? BETWEEN permite la verificación del rango (el rango especificado incluye los valores límite). El siguiente ejemplo muestra países con un área de 250,000-300,000 km2. Modifíquelo para mostrar el país y el área para países con un área entre 200,000 y 250,000..

```SQL
SELECT name, area 
FROM world
WHERE area BETWEEN 200000 AND 250000
```
.


