# Pipeline de Datos E-commerce - Arquitectura Medallion

## Objetivo del Proyecto

Construir un pipeline de datos automatizado bajo arquitectura Medallion utilizando servicios cloud de Microsoft Azure para integrar, transformar y disponibilizar información analítica proveniente de múltiples fuentes de datos.

El proyecto resuelve un caso de negocio orientado al análisis de ventas y rentabilidad por categoría de productos, permitiendo transformar datos crudos en información lista para reporting y toma de decisiones.


## 🏗️ Arquitectura del Pipeline (Medallion)

El flujo de datos se divide en tres capas principales:

### 🟤 Bronze (Raw)
- Ingesta de datos crudos.
- Recepción de archivos CSV y JSON.
- Persistencia sin modificaciones en Azure Blob Storage.

### ⚪ Silver (Clean)
- Limpieza y validación de datos.
- Eliminación de registros nulos.
- Conversión de tipos de datos.
- Consolidación de información mediante operaciones JOIN.

### 🟡 Gold (Business)
- Construcción de tablas analíticas.
- Cálculo de métricas de negocio.
- Generación de reportes y visualizaciones.

## Automatización

El pipeline fue orquestado mediante Azure Data Factory (ADF), utilizando triggers programados para ejecutar automáticamente el flujo ETL todos los días a las 08:00 AM.

La orquestación contempla:
- Ejecución secuencial de notebooks.
- Automatización de cargas.
- Integración entre Azure Data Factory y Azure Databricks.
- Ejecución programada sin intervención manual.

## Métricas del Proyecto

-  Registros procesados exitosamente: 20
-  Registros rechazados: 0
-  Facturación total procesada en la capa Gold: $ 3.240,92
-  Categorías procesadas: 4
   Validación de integridad de datos: 100%

## Controles de Calidad Implementados

Durante el procesamiento se implementaron controles de Data Quality para asegurar la confiabilidad de la información:

- Validación de registros nulos.
- Conversión y normalización de tipos de datos.
- Manejo de errores mediante tablas de auditoría.
- Validación de integridad en capas Silver y Gold.
- Filtrado de registros inválidos antes de la persistencia final.
- Persistencia de logs de registros rechazados.

##  Desafíos Técnicos

Durante el desarrollo se resolvieron diversos desafíos relacionados con infraestructura cloud y procesamiento distribuido:

- Aprovisionamiento de clusters en Azure Databricks.
- Restricciones de vCPUs en la región cloud seleccionada.
- Integración entre Azure Data Factory y Databricks mediante PAT Tokens.
- Conflictos de esquema en tablas Delta.
- Gestión de metadatos y persistencia Delta Lake.

---

## Tecnologías Utilizadas

- Microsoft Azure
- Azure Data Factory (ADF)
- Azure Databricks
- Apache Spark / PySpark
- Azure Blob Storage
- Delta Lake
- GitHub
- JSON / CSV
- Arquitectura Medallion

---

## Estructura del Repositorio

```text
/notebooks
    ├── bronze
    ├── silver
    └── gold

/data/sample
    ├── ventas.csv
    └── productos.json

/docs
    ├── informe_tecnico.pdf    
