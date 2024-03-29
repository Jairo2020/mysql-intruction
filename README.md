# mysql-intruction

### Instrucción de algunos comando mysql

- **Ver todas las bases de datos**

```sql
SHOW DATABASES;
```

- **Ver tablas de base de datos**

```sql
SHOW TABLES FROM NameDatabase;
```

- **Ver nombres de columna**

```sql
SHOW COLUMNS FROM NameTable;
```

```sql
SELECT table_schema, table_name, column_name, data_type FROM information_schema.columns
WHERE table_schema = 'nameDatabase'
ORDER BY column_name, table_name;
```

**Swich case**

```sql
BEGIN CASE p_op

    WHEN 0 THEN
       UPDATE categories SET name = p_newValue
    WHERE code = p_code;

    WHEN 1 THEN
       UPDATE categories SET name = p_newValue
    WHERE code = p_code;

END CASE;

```

**PROCEDIMIENTOS DE ALMACENADO**

- **Visualizar todos los procedimientos de almacenado.**

La primera sentencia muestra información resumida de todos los procedimientos de almacenado.

Y la segunda muestra información a detalle de todos los procedimientos de almacenado.

```sql
SHOW PROCEDURE STATUS;
```

```sql
SELECT * FROM mysql.proc;
```

Este es una alternativa.

```sql
select ROUTINE_SCHEMA,
    ROUTINE_NAME,
    ROUTINE_TYPE,
    DATA_TYPE as TYPE,
    NULL as PARENT_SCHEMA,
    NULL as PARENT_NAME
from INFORMATION_SCHEMA.ROUTINES
union
select TRIGGER_SCHEMA,
    TRIGGER_NAME,
    'TRIGGER',
    EVENT_MANIPULATION,
    EVENT_OBJECT_SCHEMA,
    EVENT_OBJECT_TABLE
from INFORMATION_SCHEMA.TRIGGERS;
```

- **Devuelve los nombres de los procedimientos**

```sql
SELECT ROUTINE_NAME FROM INFORMATION_SCHEMA.ROUTINES
   WHERE ROUTINE_TYPE = 'PROCEDURE'
   ORDER BY ROUTINE_NAME
```

- **Seleccionar procedimiento específico.**

```sql
SHOW CREATE PROCEDURE nameProcedure
```

- **Visualizar procedimientos pertenecientes a una base de datos.**

```sql
SHOW PROCEDURE STATUS WHERE Db = 'nameDataBase';
```

Código para mostrar todos los detalles del procedimiento de almacenado perteneciente a una base de datos.

```sql
SELECT * FROM mysql.proc
WHERE db = 'nameDataBase' AND name = 'nameProcedure' ;
```

Posible solución para cuando es con un usuario registrado, queda por probar.

```sql
GRANT SELECT ON mysql.proc TO 'youruser'@'yourhost' IDENTIFIED BY 'yourpass' ;
```

Código alternativo y solo muestra los nombres de los procedimientos de almacenado.

```sql
SELECT
    routine_name
FROM
    information_schema.routines
WHERE
    routine_type = 'PROCEDURE'
        AND routine_schema = 'nameDB';
```
