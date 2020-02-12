# ApuntesSQL-AngelCastro-ASI1
# Apuntes para base de datos ,grupo ASI1
En estos apuntes tendremos la parte correspondiente al aprendizaje de SQL ,así como ejercicios que hice , explicando como resolverlos y los detalles que más me costaron
## Índice
- [Explicaciones-Principales](#explicaciones-principales)
- [SELECT-BASICS](#select-basics)
    + [EJERCICIO 1.1](#ejercicio-11)
    + [EJERCICIO 1.2](#ejercicio-12)
    + [EJERCICIO 1.3](#ejercicio-13)
- [SELECT-NAME](#SELECT-NAME)
    + [EJERCICIO 2.1-2.5](#ejercicio-21-25)
    +
    +
- [SELECT-FROM-WORLD](#SELECT-FROM-WORLD)
- [SELECT-FROM-NOBEL](#SELECT-FROM-NOBEL)
- [SELECT-WITHIN-SELECT](#SELECT-WITHIN-SELECT)
- [SUM-AND-COUNT](#SUM-AND-COUNT)
- [JOIN](#JOIN)
- [MORE-JOIN-OPERATIONS](#MORE-JOIN-OPERATIONS)
- [USING-NULL](#USING-NULL)

# ***__:small_blue_diamond: EXPLICACIONES-PRINCIPALES :small_blue_diamond:__***

# SELECT-BASICS
 
## ***Ejercicio 1.1***
> Mostrar la población de alemania
```SQL
SELECT population
FROM world
WHERE name ='GERMANY';
```
## ***Ejercicio 1.2*** 
> Mostrar el nombre y la población de 'Noruega' 'Suecia' y 'Dinamarca'
```SQL
SELECT name,population
FROM world
WHERE name = 'Sweden'
OR name = 'Norway'
OR name = 'Denmark' ;
```
 ## ***Ejercicio 1.3***
 > Mostrar el país y el área para países con un área entre 200,000 y 250,000.
```SQL
SELECT name, area FROM world
WHERE area BETWEEN 200000 AND 250000;
-- En caso de no poder utilizar between ,hay una excepción que sería utilizar el signo > o < con/sin signos de =
Por ejemplo: WHERE area >=200000 AND area <=250000 -- Esto tendría el mismo significado que la consulta anterior
```

# SELECT-NAME
En estos ejercicios utilizamos herramientas como '%' para sacar nombres de ciertos países

:heavy_exclamation_mark: El porcentaje actúa como un relleno pero en el lugar donde se encuentra hay un texto que desconocemos 
:heavy_exclamation_mark:

## ***Ejercicio 2.1*** 
> Busca el país que empieza por 'Y'
```SQL
SELECT name
FROM world
WHERE name like 'Y%'
```
## ***Ejercicio 2.2***
> Busca los países que terminen en 'Y'
```SQL
SELECT name FROM world
WHERE name LIKE '%y'
```



