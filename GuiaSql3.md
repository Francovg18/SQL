# 📘 PostgreSQL - Tercera Clase: Integraciones, Funciones y Transacciones

---

## 🔗 1. Conectar PostgreSQL con Power BI

### Requisitos:

- Instalar el conector de PostgreSQL (Npgsql).
- Tener el puerto 5432 abierto y el usuario habilitado.

### Pasos:

1. Abrir Power BI → Obtener Datos → PostgreSQL.
2. Ingresar el host, base de datos, usuario y contraseña.
3. Elegir las tablas o vistas a importar.

---

## 📤 2. Importar y Exportar CSV

### Exportar:

```sql
COPY empleados TO '/ruta/empleados.csv' DELIMITER ',' CSV HEADER;
```

### Importar:

```sql
COPY empleados(nombre, edad, cargo, salario)
FROM '/ruta/empleados.csv' DELIMITER ',' CSV HEADER;
```

> Asegúrate de tener permisos adecuados o usar rutas dentro del servidor.

---

## 🔧 3. Funciones definidas por el usuario

Permiten encapsular lógica en una función reutilizable.

```sql
CREATE OR REPLACE FUNCTION salario_anual(mensual DECIMAL)
RETURNS DECIMAL AS $$
BEGIN
    RETURN mensual * 12;
END;
$$ LANGUAGE plpgsql;

-- Uso:
SELECT nombre, salario, salario_anual(salario) AS anual
FROM empleados;
```

---

## 🔄 4. Uso de transacciones

Las transacciones garantizan consistencia en las operaciones.

```sql
BEGIN;

UPDATE empleados SET salario = salario + 500 WHERE cargo = 'Analista';
DELETE FROM empleados WHERE edad < 20;

COMMIT; -- Confirmar cambios

-- O bien:
ROLLBACK; -- Deshacer todo
```

---

## 🧬 5. Tipos de datos avanzados (introductorio)

### JSON:

```sql
CREATE TABLE productos (
    id SERIAL PRIMARY KEY,
    nombre TEXT,
    detalles JSON
);

INSERT INTO productos (nombre, detalles)
VALUES ('Laptop', '{"ram": "16GB", "procesador": "i7"}');

SELECT detalles->>'ram' AS ram FROM productos;
```

### ARRAY:

```sql
CREATE TABLE cursos (
    id SERIAL PRIMARY KEY,
    nombre TEXT,
    temas TEXT[]
);

INSERT INTO cursos (nombre, temas)
VALUES ('SQL Básico', ARRAY['SELECT', 'JOIN', 'WHERE']);

SELECT unnest(temas) FROM cursos WHERE nombre = 'SQL Básico';
```

---

## 📚 Recursos recomendados

- [psycopg2 (conexión con Python)](https://www.psycopg.org/)
- [Documentación PostgreSQL JSON](https://www.postgresql.org/docs/current/functions-json.html)
- [Power BI y PostgreSQL](https://learn.microsoft.com/es-es/power-bi/connect-data/desktop-connect-postgresql)
