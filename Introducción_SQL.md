# INDICE
 [1. Introducción](#1.-Introducción)
 [2. Componentes del SQL](#componentes-del-sql)
 [3. Comandos](#comandos)
 [4. Cláusulas](#clausulas)
 [5. Operadores Lógicos](#operadores-logicos)
 [6. Operadores de Comparación](#operadores-de-comparacion)
 [7. Funciones de Agregado](#funciones-de-agregado)



### 1. Introducción

El  lenguaje de consulta estructurado (****SQL****)  
es un lenguaje de base de datos normalizado, utilizado por el motor de base  
de datos de Microsoft Jet.  **SQL**  
se utiliza para crear objetos QueryDef, como el argumento de origen del método  
OpenRecordSet y como la propiedad RecordSource del control de datos. También  
se puede utilizar con el método Execute para crear y manipular directamente  
las bases de datos Jet y crear consultas  **SQL**  
de paso a través para manipular bases de datos remotas cliente – servidor.

#### 2. Componentes del SQL

El  lenguaje  **SQL**  está compuesto por comandos, cláusulas, operadores  
y funciones de agregado. Estos elementos se combinan en las instrucciones para  
crear, actualizar y manipular las bases de datos.

#### 3  **Comandos**

Existen  dos tipos de comandos  **SQL**:

-   Los   DLL que permiten crear y definir nuevas bases de datos, campos e índices.
-   Los DML que permiten generar consultas para ordenar, filtrar y extraer datos  
    de la base de datos.

#### Comandos DLL

**Comando**  **Descripción**


**CREATE**

Utilizado para crear nuevas tablas, campos  
e índices.

**DROP**

Empleado para eliminar tablas e índices

**ALTER**

Utilizado para modificar las tablas agregando  
campos o cambiando la definición de los campos.

#### Comandos DML

**Comando**  **Descripción**

**SELECT**

Utilizado  
para consultar registros de la base de datos que satisfagan un criterio  
determinado

**INSERT**

Utilizado  
para cargar lotes de datos en la base de datos en una única  
operación.

**UPDATE**

Utilizado  
para modificar los valores de los campos y registros especificados

**DELETE**

Utilizado  
para eliminar registros de una tabla de una base de datos

#### 4 Cláusulas

Las cláusulas son condiciones de modificación utilizadas para  
definir los datos que desea seleccionar o manipular.

**Comando** / **Descripción**

**FROM**

Utilizada  
para especificar la tabla de la cual se van a seleccionar los registros

**WHERE**

Utilizada  
para especificar las condiciones que deben reunir los registros que  
se van a seleccionar

**GROUP  BY**

Utilizada  
para separar los registros seleccionados en grupos específicos

**HAVING**

Utilizada  
para expresar la condición que debe satisfacer cada grupo

**ORDER  BY**

Utilizada  
para ordenar los registros seleccionados de acuerdo con un orden específico

#### 5  Operadores Lógicos

**Operador**    **Uso**

**AND**

Es  el “y” lógico. Evalúa dos condiciones y devuelve un  
valor de verdad sólo si ambas son ciertas.

**OR**

Es  el “o” lógico. Evalúa dos condiciones y devuelve un  
valor de verdad si alguna de las dos es cierta.

**NOT**

Negación  lógica. Devuelve el valor contrario de la expresión.

#### 6 Operadores de Comparación

**Operador** / **Uso**

**<**

Menor que

**>**

Mayor  que

**<>**

Distinto  de

**<=**

Menor  ó Igual que

**>=**

Mayor  ó Igual que

**BETWEEN**

Utilizado  
para especificar un intervalo de valores.

**LIKE**

Utilizado  
en la comparación de un modelo

**In**

Utilizado  
para especificar registros de una base de datos

#### 7 Funciones de Agregado

Las  funciones de agregado se usan dentro de una cláusula  **SELECT**  
en grupos de registros para devolver un único valor que se aplica a un  
grupo de registros.

**Comando** / **Descripción**

**AVG**

Utilizada  
para calcular el promedio de los valores de un campo determinado

**COUNT**

Utilizada  
para devolver el número de registros de la selección

**SUM**

Utilizada  
para devolver la suma de todos los valores de un campo determinado

**MAX**

Utilizada  
para devolver el valor más alto de un campo especificado

**MIN**

Utilizada  
para devolver el valor más bajo de un campo especificado
