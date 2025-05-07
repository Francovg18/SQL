
# 📘 Guía Básica de PostgreSQL y SQL

## 🔍 ¿Qué es SQL?

**SQL (Structured Query Language)** es un lenguaje estándar para interactuar con bases de datos relacionales. Permite:

- Crear y eliminar estructuras (tablas, vistas).
- Insertar, actualizar y eliminar datos.
- Realizar consultas y reportes complejos.

---

## 🎯 ¿Por qué usar SQL?

- Es el lenguaje universal para trabajar con bases de datos relacionales.
- Permite obtener información precisa con consultas eficientes.
- Es compatible con sistemas como PostgreSQL, MySQL, SQL Server, Oracle, etc.

---

## 🐘 ¿Por qué elegir PostgreSQL?

PostgreSQL es un sistema de gestión de bases de datos relacional **open-source** que destaca por:

- ✅ Estabilidad y rendimiento.
- ✅ Soporte de tipos avanzados (JSON, arrays, GIS, etc.).
- ✅ Compatible con Power BI, Python, R, etc.
- ✅ Ideal para entornos empresariales y académicos.

---

## 🏗 Estructura básica de una base de datos

Una **tabla** en SQL se asemeja a una hoja de cálculo, con filas (registros) y columnas (campos).

---

## 🛠 Comandos básicos de SQL en PostgreSQL

### 📌 Crear una tabla

```sql
CREATE TABLE empleados (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100),
    edad INT,
    cargo VARCHAR(50),
    salario DECIMAL(10,2)
);
```

---

### 🗑 Eliminar una tabla

```sql
DROP TABLE empleados;
```

---

### 📝 Insertar datos

```sql
INSERT INTO empleados (nombre, edad, cargo, salario)
VALUES
('Ana Pérez', 28, 'Analista', 3500.00),
('Luis Rojas', 35, 'Gerente', 7500.00);
```

---

### 🔄 Actualizar datos

```sql
UPDATE empleados
SET salario = 8000.00
WHERE nombre = 'Luis Rojas';
```

---

### ❌ Eliminar registros

```sql
DELETE FROM empleados
WHERE edad > 60;
```

---

## 🔎 Consultas básicas

### Mostrar todos los registros

```sql
SELECT * FROM empleados;
```

---

### Filtrar con condiciones (`WHERE`)

```sql
SELECT nombre, salario
FROM empleados
WHERE salario > 4000;
```

---

### Ordenar resultados (`ORDER BY`)

```sql
SELECT nombre, salario
FROM empleados
ORDER BY salario DESC;
```

---

### Contar registros

```sql
SELECT COUNT(*) AS total_empleados
FROM empleados;
```

---

## 🤝 JOIN (Uniones entre tablas)

### Crear otra tabla para ejemplo:

```sql
CREATE TABLE departamentos (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(50)
);

INSERT INTO departamentos (nombre)
VALUES ('Recursos Humanos'), ('Finanzas');

-- Añadir campo de relación en empleados
ALTER TABLE empleados ADD COLUMN departamento_id INT;

-- Relacionar empleados con departamentos
UPDATE empleados SET departamento_id = 1 WHERE nombre = 'Ana Pérez';
UPDATE empleados SET departamento_id = 2 WHERE nombre = 'Luis Rojas';
```

---

### JOIN: unir empleados con departamentos

```sql
SELECT e.nombre, e.cargo, d.nombre AS departamento
FROM empleados e
JOIN departamentos d ON e.departamento_id = d.id;
```

---

## 🔗 Relaciones entre tablas: `persona` y `direccion`

```sql
CREATE TABLE persona (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(20),
    edad INT,
    sueldo DECIMAL(10,2)
);

CREATE TABLE direccion (
    id SERIAL PRIMARY KEY,
    persona_id INT REFERENCES persona(id),
    calle VARCHAR(50),
    ciudad VARCHAR(30),
    codigo_postal VARCHAR(10)
);

-- Insertar datos
INSERT INTO persona (nombre, edad, sueldo)
VALUES
('Carlos López', 35, 5200.50),
('María Paz', 27, 4100.00);

INSERT INTO direccion (persona_id, calle, ciudad, codigo_postal)
VALUES
(1, 'Av. Arce 123', 'La Paz', '1001'),
(2, 'Calle 21 de Calacoto', 'La Paz', '1002');
```

---

## 🔍 Consultas JOIN entre persona y direccion

### Ver nombre, ciudad y sueldo

```sql
SELECT p.nombre, p.sueldo, d.ciudad
FROM persona p
JOIN direccion d ON p.id = d.persona_id;
```

### Ver personas que viven en "La Paz"

```sql
SELECT p.nombre, d.calle
FROM persona p
JOIN direccion d ON p.id = d.persona_id
WHERE d.ciudad = 'La Paz';
```

### Personas sin dirección (LEFT JOIN)

```sql
SELECT p.nombre, d.ciudad
FROM persona p
LEFT JOIN direccion d ON p.id = d.persona_id
WHERE d.id IS NULL;
```

### Dirección y edad ordenadas por ciudad

```sql
SELECT p.nombre, p.edad, d.ciudad, d.calle
FROM persona p
JOIN direccion d ON p.id = d.persona_id
ORDER BY d.ciudad ASC;
```

---

## ✅ Conclusión

La creación de tablas relacionadas permite diseñar **bases de datos normalizadas**, evitando duplicación de datos y facilitando el mantenimiento. Con SQL puedes consultar, unir y analizar fácilmente la información distribuida entre varias tablas.

---

## 📚 Recursos recomendados

- [Documentación oficial PostgreSQL](https://www.postgresql.org/docs/)
- [W3Schools SQL Tutorial](https://www.w3schools.com/sql/)
- [PostgreSQL Exercises](https://pgexercises.com/)
