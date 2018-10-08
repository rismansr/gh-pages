# MySQL

## Wordpress

```sql
UPDATE TABLE wp_options SET option_value = "new domain" WHERE option_name = "siteurl"
UPDATE TABLE wp_options SET option_value = "new domain" WHERE option_name = "home"
```

## check database size

````sql
SELECT table_schema "DB_name",
ROUND(SUM(data_length + index_length) / 1024 / 1024, 1) "DB Size in MB"
FROM information_schema.tables
GROUP BY table_schema;
````

```sql
SELECT table_schema AS "efpiakms_prod",
ROUND(SUM(data_length + index_length) / 1024 / 1024, 2) AS "Size in (MB)"
FROM information_schema.TABLES
GROUP BY table_schema;
```