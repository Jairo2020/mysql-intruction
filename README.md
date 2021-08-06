# mysql-intruction

### Instrucción de algunos comando mysql


* **Ver todas las bases de datos**

```sql
SHOW DATABASES;
```

* **Ver tablas de base de datos**

```sql
SHOW TABLES FROM NameDatabase;
```

* **Ver nombres de columna**

```sql
SHOW COLUMNS FROM NameTable;
```

* **Swich case**

  ```sql
  BEGIN 
    CASE p_op

      WHEN 0 THEN
         UPDATE categories SET name = p_newValue
      WHERE code = p_code;

      WHEN 1 THEN
         UPDATE categories SET name = p_newValue
      WHERE code = p_code;

    END CASE;
  
  END;

  ```
