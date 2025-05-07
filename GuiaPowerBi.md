# 📊 Guía Completa de Power BI para Principiantes

---

## 🟡 ¿Qué es Power BI?

**Power BI** es una herramienta de análisis de datos de Microsoft que permite:

- Conectar múltiples fuentes de datos.
- Transformar, modelar y visualizar información.
- Crear dashboards e informes interactivos.
- Compartir reportes con usuarios o equipos.

---

## 🧩 Componentes de Power BI

| Componente       | Descripción                                             |
| ---------------- | ------------------------------------------------------- |
| Power BI Desktop | Aplicación para crear reportes y dashboards.            |
| Power BI Service | Plataforma en línea para compartir y colaborar.         |
| Power BI Mobile  | App para visualizar dashboards en dispositivos móviles. |
| Power BI Gateway | Puente para actualizar datos desde fuentes locales.     |

---

## 🟢 Instalación de Power BI Desktop

1. Descargar desde: [https://powerbi.microsoft.com/](https://powerbi.microsoft.com/)
2. Requiere Windows 10 o superior.
3. Abrir Power BI Desktop y comenzar nuevo reporte.

---

## 🔌 1. Conectar una fuente de datos

Pasos:

1. Click en “Obtener datos”.
2. Elegir fuente: Excel, PostgreSQL, SQL Server, Web, etc.
3. Cargar o transformar los datos con Power Query.

---

## 🧹 2. Transformar datos con Power Query

- Cambiar nombres de columnas.
- Eliminar filas o columnas.
- Reemplazar valores.
- Crear columnas personalizadas.
- Filtrar, agrupar y pivotar datos.

> Power Query usa un lenguaje llamado **M** (no necesitas aprenderlo al principio).

---

## 🧠 3. Modelado de datos

- **Relaciones**: Crear relaciones entre tablas por campos clave.
- **Campos calculados**: Crear nuevas columnas usando fórmulas DAX.
- **Medidas (Measures)**: Cálculos como suma total, promedio, etc.

Ejemplo DAX:

```DAX
TotalVentas = SUM(Ventas[Monto])
```

---

## 📈 4. Visualizaciones

Power BI ofrece:

- Gráficos de barras, líneas, tortas.
- Tarjetas de KPI.
- Tablas y matrices.
- Segmentadores (filtros visuales).
- Mapas geográficos.

> Puedes arrastrar y soltar campos al área de visualización.

---

## 📊 5. Filtros y segmentación

Tipos de filtros:

- A nivel visual.
- A nivel página.
- A nivel reporte.

Segmentadores (`Slicers`) permiten al usuario interactuar con el dashboard.

---

## ☁️ 6. Publicar en Power BI Service

1. Click en “Publicar”.
2. Inicia sesión con cuenta de Microsoft.
3. Elige un espacio de trabajo.
4. El reporte estará disponible online para compartir o programar actualizaciones.

---

## 🔁 7. Actualización de datos

- Puedes actualizar datos manualmente desde Power BI Desktop.
- Para actualizaciones automáticas, usar **Power BI Gateway**.

---

## 🧪 8. Buenas prácticas

- Usar nombres claros para tablas y campos.
- Evitar columnas no utilizadas.
- Dividir tablas amplias en dimensiones y hechos (modelo estrella).
- Documentar tus transformaciones.
- Mantener relaciones 1:N bien definidas.

---

## 🛠 Ejemplo básico: conectar Excel

1. Crear archivo Excel con ventas.
2. Conectar desde Power BI a ese archivo.
3. Transformar y limpiar con Power Query.
4. Crear visualizaciones de ventas por producto y mes.
5. Agregar segmentadores por ciudad y vendedor.

---

## 📚 Recursos recomendados

- [Documentación oficial](https://learn.microsoft.com/es-es/power-bi/)
- [Curso Power BI gratis - Microsoft Learn](https://learn.microsoft.com/es-es/training/powerplatform/power-bi)
- [Foros de ayuda Power BI](https://community.powerbi.com/)
