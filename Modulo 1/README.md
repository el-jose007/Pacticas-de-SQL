# Módulo 1: Consultas Básicas en SQL
En este módulo aprenderás los fundamentos para recuperar datos de una base de datos usando el lenguaje SQL. Comenzaremos con las consultas más simples y progresaremos hacia técnicas que te permitirán personalizar y controlar mejor los resultados.

## 🧩 1. ¿Qué es una consulta en SQL?
Una consulta en SQL es una instrucción que le pide a la base de datos que devuelva información específica.
La instrucción principal para realizar consultas es la palabra clave SELECT, que se utiliza para seleccionar columnas de una o más tablas.

Sintaxis básica:
```sql
SELECT columnas
FROM tabla;
```
** SELECT: indica qué columnas deseas recuperar.
FROM: especifica de qué tabla provienen esos datos.**

💡 Consejo: Toda consulta SQL debe tener al menos estas dos cláusulas para ser válida. 

🧩 2. Ver todos los datos de una tabla
Si deseas ver todos los campos y registros de una tabla (por ejemplo, clientes), puedes usar el símbolo *, que representa "todas las columnas".

sql


1
2
⌄
SELECT *
FROM clientes;
Resultado esperado (ejemplo simplificado):
ID_CLIENTE
NOMBRE
APELLIDO
EMAIL
CIUDAD
TELEFONO
1
Ana
Gómez
ana.gomez@email.com
Buenos Aires
1111-1111
2
Luis
Pérez
luis.perez@email.com
Córdoba
2222-2222
...
...
...
...
...
...

⚠️ Advertencia: Usar SELECT * en tablas grandes puede ralentizar el sistema. Es mejor especificar solo las columnas que necesitas. 

🧩 3. Seleccionar columnas específicas
Para obtener solo cierta información (por ejemplo, nombre y ciudad), enumera las columnas deseadas separadas por comas:

sql


1
2
⌄
SELECT nombre, ciudad
FROM clientes;
Resultado:
NOMBRE
CIUDAD
Ana
Buenos Aires
Luis
Córdoba
María
Rosario
...
...

🧩 4. Renombrar columnas con alias (AS)
Los nombres originales de las columnas pueden ser poco claros o muy largos. Puedes usar la palabra clave AS para asignarles un alias (nombre temporal) en los resultados.

sql


1
2
3
4
⌄
SELECT 
    nombre AS "Nombre del cliente", 
    ciudad AS "Ciudad de residencia"
FROM clientes;
Resultado:
NOMBRE DEL CLIENTE
CIUDAD DE RESIDENCIA
Ana
Buenos Aires
Luis
Córdoba

💡 Nota: Las comillas dobles (") son opcionales en muchos sistemas, pero ayudan cuando el alias contiene espacios o caracteres especiales. 

🧩 5. Ordenar resultados (ORDER BY)
Para organizar los resultados según un criterio (por ejemplo, alfabéticamente por apellido), usa ORDER BY.

sql


1
2
3
⌄
SELECT nombre, apellido
FROM clientes
ORDER BY apellido ASC;
ASC: orden ascendente (A → Z, 1 → 9).
DESC: orden descendente (Z → A, 9 → 1).
✅ Por defecto, ORDER BY usa ASC, así que podrías omitirlo si ese es tu objetivo. 

🧩 6. Eliminar filas duplicadas (DISTINCT)
Si una columna tiene valores repetidos y solo quieres ver los valores únicos, usa DISTINCT.

sql


1
2
⌄
SELECT DISTINCT ciudad
FROM clientes;
Resultado:
CIUDAD
Buenos Aires
Córdoba
Rosario
Mendoza

🔄 DISTINCT se aplica a la combinación de todas las columnas seleccionadas. Si usas SELECT DISTINCT ciudad, país, eliminará duplicados solo cuando ambas columnas coincidan. 

🧩 7. Limitar el número de resultados (LIMIT)
Cuando solo necesitas un subconjunto de filas (por ejemplo, para pruebas o paginación), usa LIMIT.

sql


1
2
3
⌄
SELECT *
FROM clientes
LIMIT 3;
Esto devolverá solo las primeras 3 filas de la tabla.

⚠️ El orden de las filas sin ORDER BY no está garantizado. Si necesitas resultados predecibles, combina LIMIT con ORDER BY. 

📝 Ejercicios de práctica
Usa la tabla clientes para resolver los siguientes ejercicios:

Muestra todos los clientes, pero solo con las columnas: nombre, apellido y ciudad.
Lista los emails de todos los clientes, asegurándote de que no haya duplicados (usa DISTINCT).
Obtén todos los clientes ordenados por ciudad en orden ascendente.
Obtén los 5 primeros clientes que aparezcan en la tabla (usa LIMIT).
Muestra el nombre y la ciudad de cada cliente, pero que en el resultado las columnas se llamen:
Cliente
Ubicación
✅ Solución sugerida para el ejercicio 5: 

sql


1
2
3
4
⌄
SELECT 
    nombre AS "Cliente",
    ciudad AS "Ubicación"
FROM clientes;
