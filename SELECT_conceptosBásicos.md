1.El ejemplo utiliza una cláusula WHERE para mostrar la población de 'Francia'. 
Tenga en cuenta que las cadenas (fragmentos de texto que son datos) deben estar entre 'comillas simples';

```SQL
SELECT population 
from world
where name = 'Germany'
```

2.Verificación de una lista La palabra IN nos permite verificar si un elemento está en una lista. El ejemplo muestra el nombre y la población de los países 'Brasil', 'Rusia', 'India' y 'China'.

Mostrar el nombre y la población de 'Suecia', 'Noruega' y 'Dinamarca'.

```SQL
SELECT name, population 
FROM world
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```
