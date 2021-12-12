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
- [Ejemplos:](#ejemplos)
- [Ejercicios:](#ejercicios)
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


# Comandos SQL (Grupos de comandos)

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

# Claúsulas
- FROM: Especifica la tabla de la que se quiere obtener los registros.
- WHERE: Especifica las condiciones o los criterios de los registros seleccionados.
- GROUP BY: Agrupa los registros seleccionados en función de un campo.
- HAVING: Especifica las condiciones o criterios que deben cumplir los grupos.
- ORDER BY: Ordena los registros seleccionados en función de un campo.

# Operadores de comparación
- BETWEEN: Especifica rangos de valores.
- LIKE: "Como". Utilizado con caracteres comodín
- IN: "En". Para especificar registros en un campo en concreto.

![estructura](https://i.imgur.com/niMgDsy.png)

Nota: Si se cambia el tipo de dato desde el gestor de BBDD se pueden eliminar registros, es mejor hacerlo desde el origen

# Ejemplos:
1. SELECT EMPRESA, DIRECCIÓN, POBLACIÓN FROM CLIENTES 
2. SELECT NOMBREARTÍCULO, SECCIÓN, PRECIO FROM PRODUCTOS WHERE SECCIÓN = "CERÁMICA"
3. SELECT NOMBREARTÍCULO, SECCIÓN, PRECIO FROM PRODUCTOS WHERE SECCIÓN = "CERÁMICA" OR SECCIÓN = "DEPORTES"
4. SELECT * FROM PRODUCTOS WHERE FECHA BETWEEN '2000-03-01' AND '2000-04-20'
5. SELECT * FROM PRODUCTOS WHERE FECHA >= "2000-03-01" AND FECHA <= "2000-04-30"

# Ejercicios:
1. Realizar una consulta que muestre los campos “Empresa” y “Población” de la tabla “Clientes”.\
   `SELECT EMPRESA, POBLACIÓN FROM CLIENTES`.\ 
   ![1](https://i.imgur.com/TmyXY5N.png).
2. Realizar una consulta que muestre los artículos de la sección “Cerámica”.\
   `SELECT SECCION, NOMBREARTÍCULO FROM PRODUCTOS WHERE SECCIÓN = "CERÁMICA"`.\ 
   ![2](https://i.imgur.com/wIcjbnN.png).

3. Realizar una consulta que muestre los productos de la sección “Deportes” cuyo precio esté entre 100 y 200 €. En la consulta solo se mostrarán los campos “Nombre de artículo” y “Precio”.\
   `SELECT NOMBREARTÍCULO, PRECIO FROM PRODUCTOS WHERE PRECIO BETWEEN 100 AND 200`.\
   ![3](https://i.imgur.com/dc3zsZp.png).
4. Realizar una consulta que muestre los productos cuyo país no sea España.\
   `SELECT NOMBREARTÍCULO, PAÍSDEORIGEN FROM PRODUCTOS WHERE PAÍSDEORIGEN != "ESPAÑA"`.\
   ![4](https://i.imgur.com/UPhJb6R.png).
5. Realizar una consulta que muestre los artículos españoles de la sección “Deportes” o aquellos cuyo precio sea superior a 350 € independientemente de cual sea su sección o país de origen.\
   ``SELECT NOMBREARTÍCULO, PAÍSDEORIGEN, PRECIO FROM PRODUCTOS WHERE PAÍSDEORIGEN = "ESPAÑA" OR PRECIO > 350``.\
   ![5](https://i.imgur.com/Nneirld.png).
6. Realizar una consulta que muestre los productos cuya fecha esté entre 1/05/2001 y 15/12/2001. En la consulta solo se visualizarán los campos “Nombre de artículo”, “Sección” y “Fecha”.\
   ``SELECT NOMBREARTÍCULO, SECCIÓN, FECHA FROM PRODUCTOS WHERE FECHA >= "2001-05-01" AND FECHA <= "2001-12-15"``.\
   ![6](https://i.imgur.com/1v0W2qH.png)



# Consultas de selección

   ### Consultas multitabla
   ### Consultas de agrupación
   ### Consultad de cálculo
   ### Subconsultas
# Consultas de acción
   ### Creación de tabla
   ### Actualización
   ### Eliminación
   ### Datos anexados
# Consultas de referencias cruzadas
# Consultas de definición de datos
   ### Tipos de datos
   ### Índices
   ### Integridad referencial
    
