README.md — Proyecto de Análisis de Ventas en Power BI
Análisis de Ventas con Power BI

Este proyecto forma parte de un laboratorio práctico cuyo objetivo es aplicar procesos de ETL, modelado de datos e implementación de dashboard interactivo utilizando Power BI Desktop.
Incluye limpieza de datos, creación de relaciones, inteligencia de tiempo, medidas DAX y construcción de un informe profesional.

bjetivos del Proyecto

Conectar Power BI a múltiples fuentes de datos.

Realizar transformaciones ETL en Power Query.

Construir un modelo relacional bajo un esquema Estrella.

Crear y marcar una Tabla Calendario.

Desarrollar medidas DAX para KPIs.

Diseñar un dashboard con visuales variados, mapa y segmentadores.

Exportar documentación técnica del proceso.

ETL – Extracción, Transformación y Carga
Fuentes utilizadas (mínimo 3)

sales.csv

products.csv

customers.csv

Opcional: stores.csv, calendar generada por DAX.

Transformaciones realizadas

En el Editor de Power Query se aplicaron:

Cambio de tipos de datos (fechas, números, texto).

Renombrado de columnas.

Eliminación de nulos y registros corruptos.

Eliminación/filtrado de duplicados.

Creación de columnas condicionales.

Combinación/anexo de consultas según necesidad.

Al finalizar, los datos quedaron limpios y consistentes para ser modelados.

 Modelado de Datos

Se utilizó un esquema Estrella (Star Schema):

Tabla de hechos

Sales: contiene ventas (montos, cantidad, fechas, claves externas).

Tablas dimensión

Products

Customers

Stores

DateTable (tabla calendario generada por DAX)

Tabla Calendario

Generada con DAX:

DateTable =
ADDCOLUMNS (
    CALENDAR (DATE(2020,1,1), DATE(2025,12,31)),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "MMMM"),
    "Month Number", MONTH([Date]),
    "Quarter", "Q" & FORMAT([Date], "Q")
)


 Marcada como Tabla de Fechas
 Relacionada en modo 1:M con la tabla de hechos

 Medidas DAX Implementadas

Ejemplos de medidas utilizadas:

Total Ventas = SUM(sales[TotalAmount])

Cantidad Vendida = SUM(sales[Quantity])

Ventas Año Anterior =
CALCULATE(
    [Total Ventas],
    SAMEPERIODLASTYEAR(DateTable[Date])
)


Estas medidas se usan para tarjetas KPI, gráficos y comparaciones temporales.

 Dashboard en Power BI

El informe incluye:

 Visuales requeridos

Gráfico de barras

Gráfico de líneas (tendencias)

Mapa (ventas por ciudad o país)

KPI (basado en medidas DAX)

Tarjetas para métricas clave

 Segmentadores (Slicers)

Año

Mes

Categoría

Ciudad / País

 Interactividad

Todos los visuales reaccionan entre sí mediante filtros cruzados.

 Entregables

Este repositorio incluye:

informe_powerbi.pbix → archivo final del dashboard

sales.csv, products.csv, customers.csv, stores.csv y date table


Tecnologías Utilizadas

Power BI Desktop

Power Query

DAX

GitHub

Autoría

Proyecto desarrollado por [NOELIA BELEN BAEZ] como parte del laboratorio de análisis de datos con Power BI.
