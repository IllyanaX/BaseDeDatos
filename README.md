# BASES DE DATOS PARA PRINCIPIANTES

## CONCEPTOS BÁSICOS 

Una base de datos es una herramienta que permite almacenar datos de forma estructurada.

Cuando hablamos de bases de datos, vamos a hablar de entidades que nosotros creamos y diseñamos para resolver problemas de todo tipo: tu presupuesto personal, el registro de nóminas en un trabajo, la biblioteca pública, la agenda telefónica, etc. Si te fijas bien encontramos bases de datos en todas partes. 

Al ponernos manos a la obra y crear una base de datos, es muy importante que entendamos cabalmente el problema, de manera que aseguremos que el diseño de la base de datos será el más óptimo para solucionar cualquier problema que se nos ponga en el camino. 

### **SOFTWARE**

Existen programas que permiten diseñar y construir bases de datos de manera más amigable e intuitiva. Vamos a empezar por uno que conocemos todos: 

<img src="images/Excel-Logo.png" width="60" height="35" />

**Excel**

Microsoft Excel es un programa que nos permite editar hojas de cálculo, a través de libros abiertos. Ni más, ni menos.
Tiene algunas limitaciones, sin embargo, es bastante útil y nos servirá de ayuda en más de una ocasión. 
Debemos considerar que:

- El tamaño de las hojas de cálculo es de 1,048,576 filas y 16,348 columnas.

- Cada celda puede contener un total de 32,767 caracteres.

- El número de campos en un formulario es de 32.

También es importante mencionar que Excel no poseé integridad referencial, es decir que podemos encontrar datos duplicados dentro del mismo libro, en diferentes hojas. 

Excel nos da la ventaja si estamos manejando pequeños volúmenes de datos, permite recolectar datos, filtrarlos, hacer búsquedas rápidas y aplicar operaciones.

 - Fórmulas versátiles

 - Funciones aplicables a subconjuntos de datos seleccionados.

 - Fucionalidades de gráficos, lo que nos permite visualizar nuestra información de forma sencilla y más fácil de explicar. 

También econtraremos Sistema Gestores de Bases de datos (Database Management Systems  por sus siglas en inglés), más completos y también más complejos, aquí una pequeña lista de los más usados:

<a href="https://dev.mysql.com/doc/" target="blank"><img src="images/MySQL-Logo.png" height="40" width="40" /></a> 

**MySQL**

Este software es un es un sistema gestor de bases de datos relacionales relacionales, de código abierto que nos permite almacenar, gestionar, y recuperar datos estructurados de manera eficiente. Se usar en proyectos de pequeña y gran escala.

<a href="https://www.postgresql.org/docs/" target="blank"><img src="images/Postgresql-Logo.png" height="40" width="40" /></a>

**PostgreSQL**

PostgresSQL o solo Postgres es un sistema de bases de datos de modelo objeto-relacional. Es muy estable y robusto, con 20 años de colaboración en su desarrollo al ser de código abierto, lo que contribuye directamente a su resitencia, integridad y exactitud.

<a href="https://docs.oracle.com/en/database/oracle/oracle-database/" target="blank"><img src="images/Oracle-logo.png"/></a>

Oracle puede trabajar con lenguajes PL/SQL y SQL para escribir consultas (queries), para acceder a los datos que se encuentra alojados en su base de datos. 

Dale click en los íconos para ver la documentación.

## BASES DE DATOS RELACIONAL

Un modelo relacional representa conjuntos que tienen relación entre ellos en un arreglo bidimensional, en forma de tablas. Se pueden pensar como una hoja de Excel. 

Cada relación tiene un conjunto nombrable de atributos que encontraremos en las columnas y valores para cada atributo en cada una de las filas (tuplas) de nuestra tabla:

| Atributo 1| Atributo 2|... | Atributo n |
|:---------:|:---------:|:--:|:----------:|
|Valor 1.1  | Valor 2.1 |... | Valor n.1  |
|Valor 1.2  | Valor 2.2 |... | Valor n.2  |
|Valor 1.3  | Valor 2.3 |... | Valor n.3  |
|     ⋮     |⋮           |⋮   | ⋮           |
|Valor 1.n  |Valor 2.n  |⋮   | Valor n.n   |

Las bases de datos relacionales cuentan con: 

- **Esquema (scheme)** : es una descripción estructural de de las relaciones en la base de datos.

- **Instancias (instances)**: son todos aquellos elementos que conforman al contenido en un tiempo determinado. 

- **Llaves (Keys)**: Keys es un tipo de atributo especial porque su valor es único dentro de la tupla, son idetificadores, es importante aclarar que una llave puede ser una combinación de atributos. 

En SQL podemos pensar que una tabla es un tipo de entidad, y que cada columna es una instancia específica del tipo de entidad.

## SQL

### Consultas (Queries)

Para poder extraer información de una base de datos SQL necesitamos seleccionar que parte de la tabla, así como de que tabla, estaremos obteniendo la información, en SQL lo hacemos a través de la siguiente instrucción:

``` sql:
SELECT columna, otra_columna FROM mi_tabla;
```

También podemos seleccionar toda la tabla con un asterisco: 

```sql:
SELECT * FROM my_table;
```
Ahora, si tenemos una tabla con miles de filas y solo necesitamos cierta información, la palabra reservada ```WHERE```

``` sql:
SELECT columna, otra_columna FROM mi_Tabla
WHERE condición, AND/OR otra_condición;
```

Podemos usar tantas columnas y tantas condiciones como sean necesarias para nuestra consulta, aun más, se pueden construir cláusulas mucho más complejas combinando operadores lógicos.

Algunos de estos operadores son: 

|Operador         | Condición          | Ejemplo en SQL |
|-----------------|--------------------|----------------|
|=, !=,<,>, =<, =>| Operadores estándar numéricos| nombre_columna != Juan|
|BETWEEN ... AND ...| El valor está dentro de un rango definido (inclusivo)| nombre_columna BETWEEN 27 AND 37|
|IN(...)   | Valor existente en una lista| nombre_columna IN (12, 13, 101)|
NOT IN (...)| Valor que no existe en una lista| nombre_columna NOT IN (22, 17, 303)|
| LIKE | Comparación exacta de cadenas (case sensitive)| columna_nombre LIKE "Maria"|
|NOT LIKE| Comparación exacta de cadenas diferentes (case senstive)| colmna_nombre NOT LIKE "gmail"|

No debemos olvidar que para que el analizador de queries pueda distinguir que estamos hablando de una cadena debemos usar comillas ``` "..." ```

[Apache Lucene](https://lucene.apache.org/) or [Sphinx](https://sphinxsearch.com/) son implemenmtaciones para bases de datos que se especializan en busquedas del tipo full-text

## Filtrar y ordenar datos en una consulta

En el álgebra relacional veremos que las relaciones excluyen valores repetidos, sin embargo en SQL tenemos que darle instrucciones para filtrar elementos este tipo de elementos usando la palabra reservada ``` DISTINCT ```. 

```
SELECT DISTINCT columna, otra_columna, ... FROM mi_tabla WHERE condicion(es);
```

>NOTA: Considera que la instrucción ```DISTINCT``` remueve indiscriminadamente todos las columnas duplicadas

Para ordenar los datos dentro de una tabla tenemos otra claúsula:  ```ORDER BY```, esto nos permitirá ordenar los valores en orden acendente o decendente. 

```
SELECT columna, otra_columna, … FROM mi_tabla WHERE condicion(es) ORDER BY columna ASC/DESC;
```

Cuando ordenamos los datos de 