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

# ***:small_blue_diamond: EXPLICACIONES-PRINCIPALES :small_blue_diamond:***
***SELECT***:  Es la instrucción más versatil de base de datos porque con ella podemos consultar información de una o varias tablas

***FROM***: Es también una instrucción muy útil ya que complementa a 'SELECT' para decir de que tabla queremos coger la información

***WHERE***: Sirve para especificar criterios que tienen que cumplir los valores de campo para que los registros que contienen los valores se incluyan en los resultados de la consulta.


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
## ***Ejercicio 2.3***
> Buscar los continentes que tengan la letra 'x'
```SQL
SELECT name FROM world
WHERE name LIKE '%x%'
  ```
## ***Ejercicio 2.4***
> Busca los países que terminan por -land
```SQL
SELECT name FROM world
WHERE name LIKE '%land'
```
## ***Ejercicio 2.5***
> Busca los países que empiezan por c- y terminan por -ia
```SQL
SELECT name FROM world
WHERE name LIKE 'c%ia'
```
## ***Ejercicio 2.6***
> Busca los países que tengan dos 'oo' en su nombre
```SQL
SELECT name FROM world
WHERE name LIKE '%oo%'
```

## ***Ejercicio 2.7***
>Busca los países que tengan 2 o más 'a' en su nombre
```SQL
SELECT name FROM world
WHERE name LIKE '%a%a%a%'
```
## ***Ejercicio 2.8***
>Busca los países que tengan de segunda letra la 't'
```SQL
SELECT name FROM world
 WHERE name LIKE '_t%'
ORDER BY name
```
:heavy_exclamation_mark:En este ejercicio utilizamos un order by name que consiste en ordenar los resultados por su nombre,también se utiliza la barrabaja que cuenta como si ahí hubiese una letra


## ***Ejercicio 2.9***
>Busca los países con 2 'o' separadas por dos letras
```SQL
SELECT name FROM world
WHERE name LIKE '%o__o%'
```
## ***Ejercicio 2.10***
>Busca los países que tienen cuatro letras
```SQL
SELECT name FROM world
 WHERE name LIKE '____'
 ```
 
 ## ***ejercicio 2.11***
 >Busca los países cuyo nombre es el de la capital
 ```SQL
 SELECT name
  FROM world
 WHERE name LIKE capital
 ```
 
 ## ***Ejercicio 2.12***
 >Busca el país cuya capital es un nombre + city
 ```SQL
 SELECT name 
  FROM world
 WHERE capital LIKE concat ('%%' 'city')
```
Función de Concat:Unir cadenas o caracteres , de los cuales tienes que dar el valor o decir que existen

## ***Ejercicio 2.13***
>Busca el país cuyo nombre de la capital incluya el del país
```SQL
SELECT capital,name
FROM world
WHERE capital LIKE concat ('%' ,name ,'%' );
```

## ***Ejercicio 2.14***
>Busca la capital y el nombre donde la capital es una extensión del nombre del país
```sql
SELECT capital,name
FROM world
WHERE capital LIKE concat (name, '_%')
```

## ***Ejercicio 2.15***
>Mostrar el nombre y la extensión donde la capital es una extensión del nombre del país.
```SQL
SELECT name,REPLACE (capital,name,'') AS EXT
FROM world
WHERE capital LIKE concat (name,'_%')
```
En este ejercico usamos la instrucción 'AS' que debe llevar un valor después y sirve para cambiar el nombre al dato que estamos pidiendo



