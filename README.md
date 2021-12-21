# Temario

- [Temario](#temario)
- [Características de SQL](#características-de-sql)
  - [Estructura general](#estructura-general)
  - [Comandos SQL (Grupos de comandos)](#comandos-sql-grupos-de-comandos)
    - [Data Definition Language (DDL)](#data-definition-language-ddl)
    - [Data Manipulation Language (DML)](#data-manipulation-language-dml)
    - [Data Control Language (DCL)](#data-control-language-dcl)
    - [Transaction Control Language (TCL)](#transaction-control-language-tcl)
  - [Claúsulas](#claúsulas)
  - [Operadores de comparación](#operadores-de-comparación)
  - [Ejemplos 1:](#ejemplos-1)
  - [Ejercicios 1:](#ejercicios-1)
  - [Ejemplos 2](#ejemplos-2)
  - [Ejercicios 2](#ejercicios-2)
- [Consultas de selección](#consultas-de-selección)
  - [Consultas multitabla](#consultas-multitabla)
  - [Consultas de agrupación](#consultas-de-agrupación)
  - [Consultad de cálculo](#consultad-de-cálculo)
  - [Subconsultas](#subconsultas)
- [Consultas de acción](#consultas-de-acción)
  - [Creación de tabla](#creación-de-tabla)
  - [Actualización](#actualización)
  - [Eliminación](#eliminación)
  - [Datos anexados](#datos-anexados)
- [Consultas de referencias cruzadas](#consultas-de-referencias-cruzadas)
- [Consultas de definición de datos](#consultas-de-definición-de-datos)
  - [Tipos de datos](#tipos-de-datos)
  - [Índices](#índices)
  - [Integridad referencial](#integridad-referencial)


# Características de SQL
- SQL (Structured Query Language) es un lenguaje estructurado de consultas. Inventado por IBM.
- Lenguaje para interactuar con BBDD relacionales.
- Solicitud SQL -> Gestor BBDD (Servidor) -> Respuesta.

## Estructura general
Instrucción SQL = Comando + Claúsula + Operadores + Funciones.

Nota: no es necesario contar con los 4 puntos (mínimo comando y cláusula)


## Comandos SQL (Grupos de comandos)

### Data Definition Language (DDL)
- Crear tablas
- Modificar tablas
- Eliminar tablas
- Comandos:
  - CREATE
  - ALTER
  - DROP
  - TRUNCATE
  
### Data Manipulation Language (DML)
- Consultas
- Seleccionar registros
- Actualizar
- Borrar registros
- Consultas de selección y acción
- Comandos:
  - SELECT
  - INSERT
  - UPDATE
  - DELETE
  
### Data Control Language (DCL)
Proporcionar seguridad
- Comandos:
  - GRANT
  - REVOKE

### Transaction Control Language (TCL)
Gestión en los cambios de los datos
- Comandos:
  - COMMIT
  - ROLLBACK
  - SAVEPOINT

## Claúsulas
- FROM: Especifica la tabla de la que se quiere obtener los registros.
- WHERE: Especifica las condiciones o los criterios de los registros seleccionados.
- GROUP BY: Agrupa los registros seleccionados en función de un campo.
- HAVING: Especifica las condiciones o criterios que deben cumplir los grupos.
- ORDER BY: Ordena los registros seleccionados en función de un campo.

## Operadores de comparación
- BETWEEN: Especifica rangos de valores.
- LIKE: "Como". Utilizado con caracteres comodín
- IN: "En". Para especificar registros en un campo en concreto.

![estructura](https://i.imgur.com/niMgDsy.png)

Nota: Si se cambia el tipo de dato desde el gestor de BBDD se pueden eliminar registros, es mejor hacerlo desde el origen

## Ejemplos 1:
1. SELECT EMPRESA, DIRECCIÓN, POBLACIÓN FROM CLIENTES 
2. SELECT NOMBREARTÍCULO, SECCIÓN, PRECIO FROM PRODUCTOS WHERE SECCIÓN = "CERÁMICA"
3. SELECT NOMBREARTÍCULO, SECCIÓN, PRECIO FROM PRODUCTOS WHERE SECCIÓN = "CERÁMICA" OR SECCIÓN = "DEPORTES"
4. SELECT * FROM PRODUCTOS WHERE FECHA BETWEEN '2000-03-01' AND '2000-04-20'
5. SELECT * FROM PRODUCTOS WHERE FECHA >= "2000-03-01" AND FECHA <= "2000-04-30"

## Ejercicios 1:
1. Realizar una consulta que muestre los campos “Empresa” y “Población” de la tabla “Clientes”.

        SELECT 
            EMPRESA, 
            POBLACIÓN 
        FROM 
            CLIENTES 

   ![1](https://i.imgur.com/TmyXY5N.png)
   
2. Realizar una consulta que muestre los artículos de la sección “Cerámica”.
   
       SELECT 
          SECCION, 
          NOMBREARTÍCULO 
       FROM 
          PRODUCTOS 
       WHERE 
          SECCIÓN = "CERÁMICA" 

   ![2](https://i.imgur.com/wIcjbnN.png)

3. Realizar una consulta que muestre los productos de la sección “Deportes” cuyo precio esté entre 100 y 200 €. En la consulta solo se mostrarán los campos “Nombre de artículo” y “Precio”.
   
        SELECT 
            NOMBREARTÍCULO, 
            PRECIO 
        FROM 
            PRODUCTOS 
        WHERE 
            (PRECIO BETWEEN 100 AND 200) AND 
            SECCIÓN = "DEPORTES" 
   
   ![3](https://i.imgur.com/Lfv6iqd.png)
   
4. Realizar una consulta que muestre los productos cuyo país no sea España.
   
        SELECT 
            NOMBREARTÍCULO, 
            PAÍSDEORIGEN 
        FROM 
            PRODUCTOS 
        WHERE 
            PAÍSDEORIGEN != "ESPAÑA"
        
   ![4](https://i.imgur.com/UPhJb6R.png)

   Nota: También se puede usar "<>" como "diferente a"

5. Realizar una consulta que muestre los artículos españoles de la sección “Deportes” o aquellos cuyo precio sea superior a 350 € independientemente de cual sea su sección o país de origen.
   
        SELECT * 
        FROM 
            PRODUCTOS 
        WHERE 
            (PAÍSDEORIGEN = "ESPAÑA" AND SECCIÓN = "DEPORTES") OR 
            PRECIO > 350
   
   ![5](https://i.imgur.com/RYXRkvx.png)

6. Realizar una consulta que muestre los productos cuya fecha esté entre 1/05/2001 y 15/12/2001. En la consulta solo se visualizarán los campos “Nombre de artículo”, “Sección” y “Fecha”.
   
        SELECT 
            NOMBREARTÍCULO, 
            SECCIÓN, 
            FECHA 
        FROM 
            PRODUCTOS 
        WHERE 
            FECHA >= "2001-05-01" AND 
            FECHA <= "2001-12-15"

   ![6](https://i.imgur.com/CjfHEq8.png)
   
   Nota: En otros gestores DB se utiliza otro formato en la fecha.

## Ejemplos 2
1. Ordenar por sección.
    
        SELECT * 
        FROM 
            PRODUCTOS 
        WHERE 
            SECCIÓN = "DEPORTES" OR 
            SECCIÓN = "CERÁMICA" 
        ORDER BY 
            SECCIÓN ASC 

   ![2.1](https://i.imgur.com/zSxRDKc.png)

2. Ordenar por sección y luego por precio.
   
        SELECT * 
        FROM 
            PRODUCTOS 
        WHERE 
            SECCIÓN = "DEPORTES" OR 
            SECCIÓN = "CERÁMICA" 
        ORDER BY 
            SECCIÓN,
            PRECIO

   ![2.2](https://i.imgur.com/enP8wWM.png)

3. Agrupar por sección y sumar el precio para obtener el total.
   
        SELECT 
            SECCIÓN, 
            SUM(PRECIO) AS PRECIO_TOTAL 
        FROM 
            PRODUCTOS
        GROUP BY 
            SECCIÓN 
        ORDER BY 
            PRECIO_TOTAL

   ![2.3](https://i.imgur.com/GMBQDcY.png)

4. Agrupar solamente sección de deportes y cerámica, obtener el promedio de ambas.
   
  Respuesta 1.

        SELECT 
          SECCIÓN, 
          AVG(PRECIO) AS PRECIO_TOTAL 
        FROM 
          PRODUCTOS 
        WHERE 
          SECCIÓN = "CERÁMICA" OR 
          SECCIÓN = "DEPORTES" 
        GROUP BY 
          SECCIÓN 
        ORDER BY 
          PRECIO_TOTAL


  ![#](https://i.imgur.com/MHOpzMW.png)

  Respuesta 2.

        SELECT 
          SECCIÓN, 
          AVG(PRECIO) AS MEDIA_PRECIO 
        FROM 
          PRODUCTOS 
        GROUP BY 
          SECCIÓN 
        HAVING 
          SECCIÓN = "CERÁMICA" OR 
          SECCIÓN = "DEPORTES" 
        ORDER BY 
          MEDIA_PRECIO.

  Nota: "HAVING" sustituye al "WHERE" en las consultas de agrupación.

#. Pregunta.
Respuesta.
![#]().

## Ejercicios 2

# Consultas de selección
   ## Consultas multitabla
   ## Consultas de agrupación
   ## Consultad de cálculo
   ## Subconsultas



# Consultas de acción
   ## Creación de tabla
   ## Actualización
   ## Eliminación
   ## Datos anexados
# Consultas de referencias cruzadas
# Consultas de definición de datos
   ## Tipos de datos
   ## Índices
   ## Integridad referencial
    


![1](https://i.imgur.com/OwY7jQw.png)
![1](https://i.imgur.com/zQDCvDm.png)


SELECT 

track.title, 
genre.name, 
album.title, 
artist.name 

FROM

track JOIN 
genre JOIN 
album JOIN 
artist 

ON

track.genre_id  = genre.genre_id    AND 
track.album_id  = album.album_id    AND 
album.artist_id = artist.artist_id


SELECT DISTINCT 
artist.name, 
genre.name

FROM 
track JOIN
album JOIN
genre JOIN
artist

ON
track.album_id  = album.album_id 	AND
track.genre_id  = genre.genre_id 	AND
album.artist_id = artist.artist_id


WHERE artist.name = "Led Zepplin"
