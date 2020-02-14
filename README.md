# ApuntesSQL-AngelCastro-ASI1
# Apuntes para base de datos ,grupo ASI1
En estos apuntes tendremos la parte correspondiente al aprendizaje de SQL ,así como ejercicios que hice , explicando como resolverlos y los detalles que más me costaron
## Índice
- [Explicaciones-Principales](#explicaciones-principales)
- [SELECT-BASICS](#select-basics)
- [SELECT-NAME](#SELECT-NAME)
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
WHERE name like 'Y%';
```
## ***Ejercicio 2.2***
> Busca los países que terminen en 'Y'
```SQL
SELECT name FROM world
WHERE name LIKE '%y';
```
## ***Ejercicio 2.3***
> Buscar los continentes que tengan la letra 'x'
```SQL
SELECT name FROM world
WHERE name LIKE '%x%';
  ```
## ***Ejercicio 2.4***
> Busca los países que terminan por -land
```SQL
SELECT name FROM world
WHERE name LIKE '%land';
```
## ***Ejercicio 2.5***
> Busca los países que empiezan por c- y terminan por -ia
```SQL
SELECT name FROM world
WHERE name LIKE 'c%ia';
```
## ***Ejercicio 2.6***
> Busca los países que tengan dos 'oo' en su nombre
```SQL
SELECT name FROM world
WHERE name LIKE '%oo%';
```

## ***Ejercicio 2.7***
>Busca los países que tengan 2 o más 'a' en su nombre
```SQL
SELECT name FROM world
WHERE name LIKE '%a%a%a%';
```
## ***Ejercicio 2.8***
>Busca los países que tengan de segunda letra la 't'
```SQL
SELECT name FROM world
 WHERE name LIKE '_t%'
ORDER BY name;
```
:heavy_exclamation_mark:En este ejercicio utilizamos un order by name que consiste en ordenar los resultados por su nombre,también se utiliza la barrabaja que cuenta como si ahí hubiese una letra


## ***Ejercicio 2.9***
>Busca los países con 2 'o' separadas por dos letras
```SQL
SELECT name FROM world
WHERE name LIKE '%o__o%';
```
## ***Ejercicio 2.10***
>Busca los países que tienen cuatro letras
```SQL
SELECT name FROM world
 WHERE name LIKE '____';
 ```
 
 ## ***ejercicio 2.11***
 >Busca los países cuyo nombre es el de la capital
 ```SQL
 SELECT name
  FROM world
 WHERE name LIKE capital;
 ```
 
 ## ***Ejercicio 2.12***
 >Busca el país cuya capital es un nombre + city
 ```SQL
 SELECT name 
  FROM world
 WHERE capital LIKE concat ('%%' 'city');
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
WHERE capital LIKE concat (name, '_%');
```

## ***Ejercicio 2.15***
>Mostrar el nombre y la extensión donde la capital es una extensión del nombre del país.
```SQL
SELECT name,REPLACE (capital,name,'') AS EXT
FROM world
WHERE capital LIKE concat (name,'_%');
```
En este ejercico usamos la instrucción 'AS' que debe llevar un valor después y sirve para cambiar el nombre al dato que estamos pidiendo

# SELECT-FROM-WORLD

## ***Ejercicio 3.1***
>Seleccionar nombre,población y continente desde world
```SQL
SELECT name, continent, population 
FROM world;
```

## ***Ejercicio 3.2***
>Seleccionar el nombre de los países que tengan una población de 200 millones
```SQL
SELECT name FROM world
WHERE population >= 200000000;
```
## ***Ejercicio 3.3***
>Conseguir el gdp de los paises con al menos 200 millones en su población
```SQL
Select name,gdp/population
from world
where population >200000000;
```

:heavy_exclamation_mark:En este ejercicio calcularemos el gdp y para ellos consiste en poner el gdp y dividirlo entre el número de la población

## ***Ejercicio 3.4***
>Mostrar el nombre y la población en millones de SUDAMERICA
```SQL
SELECT name, population/1000000
FROM world
WHERE continent = 'South America';
```

:heavy_exclamation_mark:Aquí utilizaremos la misma técnica que con el gdp para dividir la población y mostrar los datos en millones

## ***Ejercicio 3.5***
>Sacar el nombre y población de Francia,Alemania y Italia
```SQL
SELECT name, population
FROM world
WHERE name in ('France', 'Germany', 'Italy');
```
IN se utiliza cuando queremos incluir varios valores en una lista de valores

## ***Ejercicio 3.6***
>Muestre los países que son grandes por área (más de 3 millones) o grandes por población (más de 250 millones) pero no ambos. Mostrar nombre, población y área.
```SQL
SELECT name, population, area
FROM world
WHERE (area > 3000000 AND population < 250000000)
  OR (area < 3000000 and population > 250000000);
  ```

NOTA:El operador AND se utiliza como anexo entre dos peticiones y el OR se usa como comparador entre dos peticiones

## ***Ejercicio 3.7***
>Mostrar el nombre , la población en millones y el gdp en miles de millones para los paises de america del sur y con 2 decimales
```SQL
SELECT name, ROUND(population/1000000,2), ROUND(gdp/1000000000, 2)
FROM world
WHERE continent = 'South America';
```

NOTA:La función round sirve para redondear un valor númerico con lo que le indiques y con los decimales que le indiques

## ***Ejercicio 3.8***
>Mostrar el nombre y la capital que coincidan con la misma letra al principio y que no sean iguales
```SQL
SELECT name,  capital
FROM world
WHERE LEFT(name, 1) =LEFT(capital, 1)
  AND name <> capital;
  ```
  NOTA: <> se utiliza para ***'NO IGUAL'***
  
  ## ***Ejercicio 3.9***
  >Mostrar el nombre de los países que contengan todas las vocales y que no tengan espacios
  ```SQL
  SELECT name
   FROM world
WHERE name LIKE '%a%'
 AND name LIKE '%e%'
 AND name LIKE '%i%'
 AND name LIKE '%o%'
 AND name LIKE '%u%'
 
  AND name NOT LIKE '% %';
  ```
  NOTA:NOT LIKE indica algo que no queremos que contenga como por ejemplo en este ejercicio le indicamos que no debe tener espacios en su nombre
  
  # SELECT-FROM-NOBEL
  
  ## ***Ejercicio 4.1***
  >Mostrar el año ,el tema y el ganador del año 1960
  ```sql
  SELECT yr, subject, winner
  FROM nobel
 WHERE yr = 1960;
 ```
 
 ## ***Ejercicio 4.2***
 >Mostrar el ganador del año 1960 y ademas que este en la tematica de física
 ```sql
 SELECT winner
  FROM nobel
 WHERE yr = 1960
   AND subject = 'Physics';
   ```
   
 ## ***Ejercicio 4.3***
 >Mostrar el año y tema que gano Albert Einstein
 ```sql
 SELECT yr, subject
FROM nobel
WHERE winner = 'Albert Einstein';
```

## ***Ejercicio 4.4***
>Mostrar el ganador del tema de paz y del año 2000
```sql
SELECT winner
FROM nobel
WHERE subject = 'Peace' AND yr >= 2000;
```

## ***Ejercicio 4.5***
>Mostrar el año,tema y ganador que esten entre 1980 y 1989(ambos incluidos) y tematica de literatura
```sql
SELECT yr, subject, winner
FROM nobel
WHERE (yr >=1980 AND yr <=1989) AND subject = 'Literature';
```

## ***Ejercicio 4.6***
>Mostramos todos los datos desde nobel de los 3 ganadores elegidos
```sql
SELECT *
FROM nobel
WHERE winner IN ('Theodore Roosevelt', 'Woodrow Wilson', 'Jimmy Carter');
```
NOTA:utilizamos IN para incluir varios nombres

## ***Ejercicio 4.7***
>Mostrar todos los datos desde nobel de tematica fisica y del año 1980 y junto con los de quimica del 1984
```sql
SELECT *
FROM nobel
WHERE (subject = "Physics" AND yr = '1980') OR (subject = 'Chemistry' AND yr = 1984);
```

## ***Ejercicio 4.8***
>Mostrar ganador ,año y tematica desde nobel cuyo ganador empiece por sir y mostrar el mas reciente primero y ordenarlo por nombre
```sql
SELECT winner, yr, subject
FROM nobel
WHERE winner LIKE 'sir%'
ORDER BY yr DESC, winner;
```
NOTA: ORDER by sirve para ordenar por tal columna con las indicaciones que le demos y el orden puede ser ascendiente o descendiente


# SELECT-WITHIN-SELECT

## ***Ejercicio 5.1***
>Mostrar los países que tienen mayor población que RUSIA
``` SQL
SELECT name
 FROM world
  WHERE population > 
     (SELECT population
      FROM world
      WHERE name='Russia');
 ```
 NOTA: En este tipo de ejercicios utilizaremos dos select para comparar la población de un país con la de otro creando variables de mundo
 
 ## ***Ejercicio 5.2***
 >Mostrar el nombre desde mundo en el continente de europa con gdp mayor que reino unido
 ```sql
 SELECT name
FROM world
WHERE continent = 'Europe'
   AND gdp / population >
      (SELECT gdp / population
       FROM world
      WHERE name = 'United Kingdom');
  ```
      
  ## ***Ejercicio 5.3***
  >Mostrar el nombre y el continente de los países de los continentes que contienen Argentina o Australia . Ordenar por nombre del país.
  ```sql
 SELECT name, continent
FROM world
WHERE continent IN (SELECT continent FROM world WHERE name IN ('Argentina', 'Australia'))
ORDER BY name;
```
NOTA:Aquí tenemos un ejercicio un poco mas completo en el que se utiliza un order by, un IN para poder incluir el continente y los países de los que forman parte argentina y australia


## ***Ejercicio 5.4***
>Muestra el nombre y la población de cada país en Europa. Mostrar la población como un porcentaje de la población de Alemania.
```sql
SELECT name, CONCAT(ROUND(population/(SELECT population FROM world WHERE name = 'Germany'), 0), %)
FROM world
WHERE continent = 'Europe';
```
NOTA:Este ejercicio es bastante complejo debido al uso de un concat y que dentro de el tetenemos un redondeo ,uso de lugares decimales y al final porcentajes


## ***Ejercicio 5.5***
>Mostrar el país más grande por área en cada continente,muestre el continente,el nombre y el área
```sql
SELECT continent, name, area
FROM world x
WHERE area >= ALL
    (SELECT area FROM world y
    WHERE y.continent=x.continent
    AND area>0);
```
NOTA:En este ejercicio comparamos dos tablas world una x e y  para así comparar los dos continentes y saber cual tiene mayor área

## ***Ejercicio 5.6***
>Algunos países tienen una población más de tres veces mayor que la de cualquiera de sus vecinos (en el mismo continente). Dar a los países y continentes.
```SQL
SELECT name,continent
FROM world AS W1
WHERE population > ALL (
SELECT population * 3
FROM world AS W2
WHERE W1.CONTINENT = W2.CONTINENT
AND W1.name <> W2.name
);
```

# SUM-AND-COUNT



  






