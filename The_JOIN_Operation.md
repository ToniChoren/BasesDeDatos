game
|id	| mdate |	stadium | team1 |	team2 |
| --- | ---- | -------- |   --------| ----- |  
| 1001	| 8 June 2012|		National Stadium, Warsaw | POL    | GRE |
| 1002	| 8 June 2012| Stadion Miejski (Wroclaw) | RUS    | CZE |
| 1003	| 12 June 2012| Stadion Miejski (Wroclaw) | GRE    | CZE |
| 1004	| 12 June 2012| National Stadium, Warsaw | POL    | RUS |
| ... |



goal
|matchid|	teamid	|player	| gtime |
| ----  | -----   | ---   | ---- |
|1001|	POL |	Robert Lewandowski|	17|
|1001	|GRE	|Dimitris Salpingidis|	51|
|1002|	RUS|	Alan Dzagoev	|15|
|1002|	RUS	|Roman Pavlyuchenko|	82|


eteam
|id	|teamname	|coach|
|---|---|---|
|POL|	Poland|	Franciszek| Smuda|
|RUS|	Russia|	Dick |Advocaat|
|CZE|	Czech| Republic|	Michal Bilek|
|GRE|	Greece|	Fernando Santos|
...


1. El primer ejemplo muestra el gol marcado por un jugador con el apellido 'Bender'. El *dice que enumere todas las columnas de la tabla, una forma más corta de decirmatchid, teamid, player, gtime

Modifíquelo para mostrar el matchid y el nombre del jugador para todos los goles marcados por Alemania. Para identificar jugadores alemanes, verifique: teamid = 'GER'

~~~SQL
SELECT goal.matchid, goal.player
FROM goal  
  WHERE teamid = 'GER';
~~~

2. De la consulta anterior puedes ver que Lars Bender anotó un gol en el juego 1012. Ahora queremos saber qué equipos estaban jugando en ese partido.

Observe en el que la columna matchiden la goaltabla corresponde a la idcolumna en la gametabla. Podemos buscar información sobre el juego 1012 al encontrar esa fila en la tabla de juegos .

Mostrar id, estadio, equipo1, equipo2 solo para el juego 1012

~~~SQL
SELECT game.id, game.stadium, game.team1, game.team2
FROM game
WHERE id = '1012';
~~~

3. Modifíquelo para mostrar el jugador, teamid, estadio y mdate para cada gol alemán.

~~~SQL
SELECT goal.player, goal.teamid, game.stadium, game.mdate
  FROM game JOIN goal ON (id=matchid)
WHERE teamid= 'Ger';
~~~
4. Muestra al equipo1, al equipo2 y al jugador por cada gol marcado por un jugador llamado Mario player LIKE 'Mario%'

~~~SQL
SELECT  game.team1, game.team2,  goal.player
FROM game JOIN goal ON (id=matchid)
WHERE goal.player LIKE 'Mario%';
~~~

5. Mostrar player, teamid, coach, gtimepara todos los goles marcados en los primeros 10 minutosgtime<=10

~~~SQL
SELECT player, teamid, coach, gtime
  FROM goal JOIN eteam ON (teamid=id)
 WHERE gtime<=10;

~~~

6. Enumere las fechas de los partidos y el nombre del equipo en el que 'Fernando Santos' fue el entrenador del equipo1.

~~~SQL
SELECT game.mdate, eteam.teamname
  FROM game JOIN eteam ON (team1=eteam.id)
 WHERE coach ='Fernando Santos';
~~~

7. Enumere al jugador por cada gol marcado en un juego donde el estadio fue 'Estadio Nacional, Varsovia'

~~~SQL
SELECT player
  FROM goal JOIN game ON (id=matchid)
 WHERE stadium = 'National Stadium, Warsaw';
~~~


8. En su lugar, muestre el nombre de todos los jugadores que marcaron un gol contra Alemania.

~~~SQL
SELECT DISTINCT goal.player
  FROM game JOIN goal ON matchid = id 
    WHERE (team1='GER' OR team2='GER') AND teamid <> 'GER';
~~~


9. Muestra el nombre del equipo y el número total de goles marcados.

~~~SQL
SELECT teamname, COUNT(teamid)
  FROM eteam JOIN goal ON id=teamid
 ORDER BY teamname;
~~~

10. Muestra el estadio y la cantidad de goles marcados en cada estadio.

~~~SQL
SELECT game.stadium,COUNT(1)
  FROM goal JOIN game ON id=matchid
GROUP BY stadium;
~~~

11. Para cada partido que involucre 'POL', muestre el matchid, la fecha y el número de goles marcados.

~~~SQL
SELECT matchid, mdate, COUNT(teamid)
  FROM game JOIN goal ON matchid = id 
 WHERE (team1 = 'POL' OR team2 = 'POL')
GROUP BY matchid, mdate;
~~~

12. Muestra el estadio y la cantidad de goles marcados en cada estadio.

~~~SQL
SELECT matchid, mdate, COUNT(teamid)
  FROM game JOIN goal ON matchid = id 
 WHERE (teamid= 'GER')
GROUP BY matchid, mdate;
~~~

13. Enumere cada partido con los goles marcados por cada equipo como se muestra. Esto usará " CASO CUANDO " que no se ha explicado en ningún ejercicio anterior.

~~~SQL
SELECT mdate,
  team1,
  SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  team2,
  SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
  FROM game LEFT JOIN goal ON matchid = id
GROUP BY mdate,matchid,team1,team2;
~~~
