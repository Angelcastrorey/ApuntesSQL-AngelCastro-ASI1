# ApuntesSQL-AngelCastro-ASI1
# Apuntes para base de datos ,grupo ASI1
En estos apuntes tendremos la parte correspondiente al aprendizaje de SQL ,así como ejercicios que hice , explicando como resolverlos y los detalles que más me costaron
## Índice
- [SELECT-BASICS](#select-basics)
- [SELECT-NAME](#SELECT-NAME)
- [SELECT-FROM-WORLD](#SELECT-FROM-WORLD)
- [SELECT-FROM-NOBEL](#SELECT-FROM-NOBEL)
- [SELECT-WITHIN-SELECT](#SELECT-WITHIN-SELECT)
- [SUM-AND-COUNT](#SUM-AND-COUNT)
- [JOIN](#JOIN)
- [MORE-JOIN-OPERATIONS](#MORE-JOIN-OPERATIONS)
- [USING-NULL](#USING-NULL)

# SELECT-BASICS


Ejercicio 1-Mostrar la población de alemania
```SQL
SELECT population
FROM world
WHERE name ='GERMANY';
```
Ejercicio 2-Mostrar el nombre y la población de 'Noruega' 'Suecia' y 'Dinamarca'
```SQL
SELECT name,population
FROM world
WHERE name = 'Sweden'
OR name = 'Norway'
OR name = 'Denmark' ;
```
Ejercicio 3-Mostrar el país y el área para países con un área entre 200,000 y 250,000.
```SQL
SELECT name, area FROM world
WHERE area BETWEEN 200000 AND 250000;
-- En caso de no poder utilizar between ,hay una excepción que sería utilizar el signo > o < con/sin signos de =
Por ejemplo: WHERE area >=200000 AND area <=250000
```

