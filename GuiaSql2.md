# 📘 PostgreSQL - Segunda Clase: Consultas Avanzadas y Buenas Prácticas

---

## 🔢 1. Funciones de agregación

Estas funciones permiten realizar cálculos sobre columnas numéricas.

```sql
SELECT AVG(salario) AS salario_promedio FROM empleados;
SELECT MAX(edad) AS edad_maxima FROM empleados;
SELECT SUM(salario) FROM empleados WHERE cargo = 'Analista';
```

---

## 📊 2. GROUP BY y HAVING

Se usa `GROUP BY` para agrupar datos y `HAVING` para aplicar condiciones a grupos.

```sql
-- Salario promedio por cargo
SELECT cargo, AVG(salario) AS promedio
FROM empleados
GROUP BY cargo;

-- Cargos con promedio mayor a 5000
SELECT cargo, AVG(salario) AS promedio
FROM empleados
GROUP BY cargo
HAVING AVG(salario) > 5000;
```

---

## 🔁 3. Subconsultas (subqueries)

Consultas anidadas dentro de otra.

```sql
-- Empleados con salario mayor al promedio
SELECT nombre, salario
FROM empleados
WHERE salario > (
    SELECT AVG(salario) FROM empleados
);
```

---

## 📅 4. Funciones de fecha y texto

### Fechas

```sql
SELECT NOW(); -- Fecha y hora actual
SELECT AGE('2024-12-01'); -- Diferencia entre hoy y esa fecha
```

### Texto

```sql
SELECT UPPER(nombre), LOWER(nombre), LENGTH(nombre)
FROM empleados;
```

---

## 🏷 5. Alias con AS

Permiten nombrar columnas o tablas temporalmente.

```sql
SELECT nombre AS empleado, salario AS sueldo FROM empleados;
```

---

## 👁 6. Vistas (VIEW)

Una vista guarda una consulta como si fuera una tabla.

```sql
CREATE VIEW vista_analistas AS
SELECT nombre, salario
FROM empleados
WHERE cargo = 'Analista';

-- Usar la vista
SELECT * FROM vista_analistas;
```

---

## 📌 7. Índices básicos

Los índices mejoran la velocidad de búsqueda en columnas.

```sql
CREATE INDEX idx_nombre ON empleados(nombre);
```

---

## ✅ 8. Buenas prácticas de modelado

- Usa nombres descriptivos en tablas y columnas.
- Evita la redundancia de datos.
- Normaliza tu base de datos.
- Usa claves primarias (`PRIMARY KEY`) y foráneas (`FOREIGN KEY`).
- Aplica restricciones (`NOT NULL`, `UNIQUE`, `CHECK`) para asegurar calidad de datos.

---

## 📚 Recursos recomendados

- [PostgreSQL Date Functions](https://www.postgresql.org/docs/current/functions-datetime.html)
- [SQL Subqueries](https://www.w3schools.com/sql/sql_subqueries.asp)
- [Indexing in PostgreSQL](https://www.postgresql.org/docs/current/indexes.html)
