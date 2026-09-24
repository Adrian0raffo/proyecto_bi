# Proyecto Final: Análisis del desempeño operativo de los vuelos domésticos de American Airlines, con énfasis en retrasos, cancelaciones y desvíos

**Curso:** Business Intelligence

## Integrantes

- Luciana Carpio
- Sofía Briceño
- Gustavo Barrantes
- Adriano Raffo

---

## 1. Marco teórico

### 1.1. Business Intelligence

El **Business Intelligence (BI)**, o inteligencia empresarial, comprende un conjunto de procesos y herramientas tecnológicas que permiten recopilar, integrar y analizar datos para convertirlos en información útil, la cual se emplea en la toma de decisiones. Su propósito es facilitar que las organizaciones entiendan mejor su desempeño, identifiquen patrones y detecten problemas u oportunidades a partir de datos confiables. La implementación de BI permite elaborar reportes, indicadores y visualizaciones que presentan información y facilitan su interpretación. Así, los responsables de una empresa pueden tomar decisiones fundamentadas en evidencia y no únicamente en percepciones o experiencias previas. BI también permite realizar un seguimiento del comportamiento histórico de las operaciones y comparar sus resultados entre diferentes periodos, áreas o categorías.

### 1.2. Data warehouse

Un **data warehouse**, o almacén de datos, es un sistema diseñado para recopilar, integrar y almacenar información proveniente de distintas fuentes con el propósito de facilitar su análisis. A diferencia de una base de datos operacional, que registra las actividades diarias de una organización, un data warehouse conserva información histórica y se orienta a la elaboración de reportes y al apoyo en la toma de decisiones.

Algunas de sus principales características son:

- **Orientado a temas:** organiza los datos según áreas relevantes para la organización.
- **Integrado:** reúne información proveniente de diferentes fuentes utilizando formatos consistentes.
- **Variante en el tiempo:** conserva datos históricos para analizar su evolución.
- **No volátil:** la información almacenada se mantiene estable y disponible para su consulta.

### 1.3. Modelamiento multidimensional

El **modelamiento multidimensional** es una técnica utilizada para organizar los datos de forma que puedan ser consultados y analizados con facilidad. Su diseño parte de un proceso de negocio y separa la información en:

- **Hechos:** representan eventos o métricas de negocio.
- **Dimensiones:** proporcionan el contexto necesario para analizar los hechos, como el tiempo, la ubicación o la empresa involucrada.

Para elaborar un modelo multidimensional, primero se selecciona el proceso de negocio y luego se define la granularidad, es decir, qué representa cada fila de la tabla de hechos. Después se identifican las dimensiones y las medidas asociadas al proceso. Esta organización permite filtrar, agrupar y resumir grandes cantidades de datos desde distintas perspectivas.

#### 1.3.1. Modelo estrella

El **modelo estrella** está conformado por una tabla de hechos central conectada directamente con diferentes tablas de dimensiones, lo cual forma una figura similar a una estrella.

La tabla central almacena los eventos y medidas del proceso analizado, mientras que las dimensiones contienen la información descriptiva empleada para filtrar y agrupar los resultados. Su diseño facilita la comprensión del modelo, reduce la complejidad de las consultas y permite analizar las medidas desde distintas perspectivas.

Además, las dimensiones suelen estar desnormalizadas; es decir, sus atributos descriptivos se conservan en una misma tabla para simplificar el análisis.

#### 1.3.2. Tabla de hechos y granularidad

La **tabla de hechos** es la tabla central de un modelo estrella. En ella se registran los eventos correspondientes a un proceso de negocio y las medidas que se desean analizar, como cantidades, importes, costos o duraciones. También contiene claves foráneas que permiten relacionar cada evento con sus respectivas dimensiones.

La **granularidad** define exactamente qué representa cada fila de la tabla de hechos. Por ejemplo, una fila podría representar una venta completa o un producto individual dentro de una venta.

Esta definición debe realizarse antes de seleccionar las dimensiones y medidas, ya que todos los datos de la tabla deben corresponder al mismo nivel de detalle. Una granularidad correctamente definida permite interpretar las medidas de manera consistente y evita combinar información perteneciente a distintos niveles de análisis.

#### 1.3.3. Tablas de dimensiones

Las **tablas de dimensiones** almacenan la información descriptiva que permite interpretar y analizar los registros de la tabla de hechos. Sus atributos responden preguntas como quién, qué, cuándo, dónde y cómo ocurrió un evento.

Estas tablas se utilizan para:

- Filtrar la información.
- Clasificar los registros.
- Agrupar las medidas.
- Analizar los datos desde diferentes perspectivas.

Además, pueden contener jerarquías que permiten examinar la información con distintos niveles de detalle. Por ejemplo, una dimensión de tiempo podría tener una jerarquía compuesta por año, trimestre, mes y día.

Cada dimensión posee una clave que identifica de manera única sus registros y que se conecta con la tabla de hechos. En los modelos dimensionales suelen utilizarse **claves sustitutas**, generadas específicamente para el data warehouse, en lugar de depender únicamente de los identificadores de los sistemas de origen.

### 1.4. Procesamiento analítico OLAP

El **procesamiento analítico en línea (OLAP)** es una tecnología que permite analizar grandes volúmenes de información desde diferentes perspectivas. Se utiliza principalmente con datos almacenados en un data warehouse y facilita la ejecución rápida de consultas, comparaciones y cálculos complejos.

La información suele organizarse en estructuras multidimensionales conocidas como **cubos OLAP**. Estos contienen medidas numéricas y dimensiones que permiten observar un mismo resultado según diferentes criterios, como tiempo, ubicación o categoría.

OLAP también permite cambiar el nivel de detalle del análisis. Por ejemplo, se puede pasar de una visión anual a una mensual, filtrar una categoría específica o comparar diferentes grupos. De esta manera, los usuarios pueden explorar la información e identificar tendencias o patrones que apoyen la toma de decisiones.

### 1.5. Indicadores de desempeño de vuelos

Los **indicadores de desempeño de vuelos** permiten medir la eficiencia y puntualidad de las operaciones aéreas. Entre los principales se encuentran:

- Porcentaje de vuelos puntuales.
- Minutos promedio de retraso.
- Tasa de cancelación.
- Proporción de vuelos desviados.

El Bureau of Transportation Statistics considera que un vuelo presenta retraso cuando llega o sale **15 minutos o más después del horario programado**. Asimismo, clasifica las causas de demora en cinco categorías:

1. Responsabilidad de la aerolínea.
2. Clima extremo.
3. Sistema Nacional de Aviación.
4. Llegada tardía de la aeronave anterior.
5. Seguridad.

Estos indicadores permiten comparar el desempeño entre periodos, rutas, aeropuertos y aerolíneas. Su análisis facilita la identificación de patrones y factores que afectan la puntualidad, proporcionando información relevante para mejorar la planificación y la toma de decisiones operativas.

### 1.6. Aplicación de BI al análisis de operaciones aéreas

Las aerolíneas generan grandes cantidades de datos relacionados con vuelos, horarios, rutas, aeropuertos, retrasos y cancelaciones. Business Intelligence permite integrar y analizar esta información para convertirla en indicadores que faciliten la evaluación del desempeño operativo y la toma de decisiones.

Mediante reportes y visualizaciones, es posible comparar la puntualidad entre periodos, identificar rutas o aeropuertos con retrasos frecuentes y analizar las principales causas de demora. El Bureau of Transportation Statistics recopila este tipo de información, incluyendo horarios programados y reales, cancelaciones, desvíos y minutos de retraso según su causa.

De esta manera, la aplicación de BI en el transporte aéreo facilita la identificación de patrones y problemas recurrentes. La información obtenida puede apoyar la planificación de horarios, la asignación de recursos y el seguimiento de la puntualidad de las operaciones.



## Bibliografía

Bureau of Transportation Statistics. (s. f.). *Reporting carrier on-time performance (1987–present)*. U.S. Department of Transportation. [https://www.transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ](https://www.transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ)

IBM. (s. f.). *¿Qué es Business Intelligence (BI)?* [https://www.ibm.com/mx-es/think/topics/business-intelligence](https://www.ibm.com/mx-es/think/topics/business-intelligence)

IBM. (s. f.). *What is a data warehouse?* [https://www.ibm.com/think/topics/data-warehouse](https://www.ibm.com/think/topics/data-warehouse)

IBM. (2021, 30 de julio). *What is OLAP?* [https://www.ibm.com/think/topics/olap](https://www.ibm.com/think/topics/olap)

Kimball Group. (s. f.). *Dimensional modeling techniques*. [https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/)

Kimball, R. (2008, 5 de noviembre). *Fact tables*. Kimball Group. [https://www.kimballgroup.com/2008/11/fact-tables/](https://www.kimballgroup.com/2008/11/fact-tables/)

Microsoft. (s. f.). *Understand star schema and the importance for Power BI*. Microsoft Learn. [https://learn.microsoft.com/en-us/power-bi/guidance/star-schema](https://learn.microsoft.com/en-us/power-bi/guidance/star-schema)

Oracle. (2023, 8 de junio). *What is a data warehouse?* [https://www.oracle.com/database/what-is-a-data-warehouse/](https://www.oracle.com/database/what-is-a-data-warehouse/)

Link de la BD completa (drive): https://drive.google.com/file/d/1UJ-2yC9uMcpQJi6i4bS0GQAZNirMcL3X/view?usp=sharing
