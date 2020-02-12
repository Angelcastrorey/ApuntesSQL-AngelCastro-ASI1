# ApuntesSQL-AngelCastro-ASI1
# Apuntes para base de datos ,grupo ASI1
En estos apuntes tendremos la parte correspondiente al aprendizaje de SQL ,así como ejercicios que hice , explicando como resolverlos y los detalles que más me costaron
## Índice
- [select-basics](#select-basics)
# SELECT-BASICS

Ejercicio 1-Mostrar la población de alemania

[SELECT population
FROM world
WHERE name ='GERMANY']

Ejercicio 2-Mostrar el nombre y la población de 'Noruega' 'Suecia' y 'Dinamarca'

[SELECT name,population
FROM world
WHERE name = 'Sweden'
OR name = 'Norway'
OR name = 'Denmark' ;]

Ejercicio 3-Mostrar el país y el área para países con un área entre 200,000 y 250,000.

[SELECT name, area FROM world
  WHERE area BETWEEN 200000 AND 250000]
  
