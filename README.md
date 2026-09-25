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

El Business Intelligence (BI), o inteligencia empresarial, comprende un conjunto de procesos y herramientas tecnológicas que permiten recopilar, integrar y analizar datos para convertirlos en información útil, la cual se emplea en la toma de decisiones. Su propósito es facilitar que las organizaciones entiendan mejor su desempeño, identifiquen patrones y detecten problemas u oportunidades a partir de datos confiables (IBM, s. f.).

La implementación de BI permite elaborar reportes, indicadores y visualizaciones que presentan información y facilitan su interpretación. Así, los responsables de una empresa pueden tomar decisiones fundamentadas en evidencia y no únicamente en percepciones o experiencias previas. Además, BI permite realizar un seguimiento del comportamiento histórico de las operaciones y comparar sus resultados entre diferentes periodos, áreas o categorías.

En el sector aéreo, Business Intelligence puede utilizarse para analizar grandes volúmenes de información relacionada con vuelos, rutas, aeropuertos, horarios, retrasos y cancelaciones. A partir de este análisis, una aerolínea puede identificar las rutas con mayores problemas de puntualidad, los horarios en los que se producen más demoras y las causas que afectan con mayor frecuencia sus operaciones. Por lo tanto, la aplicación de BI contribuye a convertir los registros operativos de los vuelos en información relevante para mejorar la planificación y apoyar la toma de decisiones.

### 1.2. Data warehouse

Un data warehouse o almacén de datos es un sistema diseñado para recopilar, integrar y almacenar información proveniente de distintas fuentes con el propósito de facilitar su análisis. A diferencia de una base de datos operacional, que registra las actividades diarias de una organización, un data warehouse conserva información histórica y se orienta a la elaboración de reportes y al apoyo en la toma de decisiones (IBM, s. f.; Oracle, 2023).

Entre sus principales características se encuentra su orientación a temas, porque organiza los datos según áreas relevantes para la organización; su integración, debido a que reúne información de diferentes fuentes utilizando formatos consistentes; su variación en el tiempo, porque conserva datos históricos; y su carácter no volátil, ya que la información almacenada se mantiene estable para su consulta y análisis.

### 1.3. Data Mart

Un Data Mart es una base de datos analítica orientada a un área, proceso o tema específico de una organización. A diferencia de un data warehouse, que puede integrar información de distintas áreas empresariales, un Data Mart contiene un conjunto más delimitado de datos y busca responder necesidades concretas de análisis. Esta especialización facilita el acceso a la información relevante y permite realizar consultas enfocadas en un determinado proceso de negocio (IBM, s. f.).

Un Data Mart puede obtener sus datos de un data warehouse, pero también puede construirse directamente a partir de fuentes internas o externas. Su información suele organizarse mediante un modelo dimensional compuesto por una tabla de hechos y distintas tablas de dimensiones, lo que permite analizar las medidas desde diferentes perspectivas.

### 1.4. Modelamiento multidimensional

El modelamiento multidimensional es una técnica utilizada para organizar los datos de forma que puedan ser consultados y analizados con facilidad. Su diseño parte de un proceso de negocio y separa la información en hechos, que representan eventos o métricas de negocio, y dimensiones, que proporcionan el contexto necesario para analizarlos, como el tiempo, la ubicación o la organización involucrada (Kimball Group, s. f.).

Para elaborar un modelo multidimensional, primero se selecciona el proceso de negocio y luego se define la granularidad, es decir, qué representa cada fila de la tabla de hechos. Después se identifican las dimensiones y las medidas asociadas al proceso. Esta organización permite filtrar, agrupar y resumir grandes cantidades de datos desde distintas perspectivas.

#### 1.4.1. Modelo estrella

El modelo estrella está conformado por una tabla de hechos central conectada directamente con diferentes tablas de dimensiones, por lo que sus relaciones adoptan una forma similar a una estrella. La tabla central almacena los eventos y medidas del proceso analizado, mientras que las dimensiones contienen la información descriptiva empleada para filtrar y agrupar los resultados.

Este diseño facilita la comprensión del modelo, reduce la complejidad de las consultas y permite analizar las medidas desde distintas perspectivas. Además, las dimensiones suelen estar desnormalizadas, lo que significa que sus atributos descriptivos se conservan en una misma tabla para simplificar las consultas analíticas (Microsoft, s. f.).

#### 1.4.2. Tabla de hechos y granularidad

La tabla de hechos es la tabla central de un modelo estrella. En ella se registran los eventos correspondientes a un proceso de negocio y las medidas que se desean analizar, como cantidades, importes, costos o duraciones. También contiene claves foráneas que permiten relacionar cada evento con sus respectivas dimensiones (Kimball, 2008).

La granularidad define exactamente qué representa cada fila de la tabla de hechos. Por ejemplo, una fila podría representar una venta completa o un producto individual dentro de una venta. Esta definición debe realizarse antes de seleccionar las dimensiones y las medidas, ya que todos los datos de la tabla de hechos deben corresponder al mismo nivel de detalle.

Una granularidad correctamente definida permite interpretar las medidas de manera consistente y evita combinar información perteneciente a distintos niveles de análisis.

#### 1.4.3. Tablas de dimensiones

Las tablas de dimensiones almacenan la información descriptiva que permite interpretar y analizar los registros de la tabla de hechos. Sus atributos responden preguntas como quién, qué, cuándo, dónde y cómo ocurrió un evento. Estas tablas se utilizan para filtrar, clasificar y agrupar las medidas.

Las dimensiones también pueden contener jerarquías que permiten analizar la información con distintos niveles de detalle. Por ejemplo, una dimensión de fecha podría incluir la jerarquía año, trimestre, mes y día, permitiendo pasar de una visión general a una más detallada.

Cada dimensión posee una clave que identifica de manera única sus registros y que se conecta con la tabla de hechos. En los modelos dimensionales suelen utilizarse claves sustitutas, generadas específicamente para el data warehouse o Data Mart, en lugar de depender únicamente de los identificadores de los sistemas de origen (Kimball Group, s. f.).

### 1.5. Proceso ETL

El proceso ETL comprende las etapas de extracción, transformación y carga de datos. En la extracción se obtiene la información desde las fuentes originales; durante la transformación, los datos se limpian, organizan, integran y adaptan a la estructura requerida; finalmente, en la carga, la información procesada se almacena en un data warehouse, Data Mart u otro repositorio de destino (IBM, s. f.).

Este proceso permite convertir datos provenientes de diferentes archivos o sistemas en información consistente y preparada para el análisis. Durante la transformación pueden realizarse actividades como la corrección de formatos, el tratamiento de valores nulos, la eliminación de duplicados, la validación de registros y la creación de campos derivados. De esta manera, ETL contribuye a mejorar la calidad y uniformidad de los datos utilizados en una solución de Business Intelligence.

### 1.6. Procesamiento analítico OLAP

El procesamiento analítico en línea u OLAP es una tecnología que permite analizar grandes volúmenes de información desde diferentes perspectivas. Se utiliza principalmente con datos almacenados en un data warehouse y facilita la ejecución rápida de consultas, comparaciones y cálculos complejos (IBM, 2021).

La información suele organizarse en estructuras multidimensionales conocidas como cubos OLAP. Estos contienen medidas numéricas y dimensiones que permiten observar un mismo resultado según diferentes criterios, como tiempo, ubicación o categoría.

OLAP también permite modificar el nivel de detalle del análisis. Por ejemplo, se puede pasar de una visión anual a una mensual, filtrar una categoría específica o comparar diferentes grupos. De esta manera, los usuarios pueden explorar la información e identificar tendencias o patrones que apoyen la toma de decisiones.

### 1.7. Indicadores de desempeño de vuelos

Los indicadores de desempeño de vuelos permiten medir la eficiencia y puntualidad de las operaciones aéreas. Entre los principales se encuentran el porcentaje de vuelos puntuales, los minutos promedio de retraso, la tasa de cancelación y la proporción de vuelos desviados.

El Bureau of Transportation Statistics considera que un vuelo presenta retraso cuando llega o sale 15 minutos o más después del horario programado. Asimismo, clasifica las causas de demora en cinco categorías: factores atribuibles a la aerolínea, clima extremo, Sistema Nacional de Aviación, llegada tardía de la aeronave anterior y seguridad (Bureau of Transportation Statistics, s. f.).

Estos indicadores permiten comparar el desempeño entre periodos, rutas, aeropuertos y aerolíneas. Su análisis facilita la identificación de patrones y factores que afectan la puntualidad, proporcionando información relevante para mejorar la planificación y la toma de decisiones operativas.

### 1.8. Aplicación de BI al análisis de operaciones aéreas

Las aerolíneas generan grandes cantidades de datos relacionados con vuelos, horarios, rutas, aeropuertos, retrasos, cancelaciones y desvíos. Business Intelligence permite integrar y analizar esta información para convertirla en indicadores que faciliten la evaluación del desempeño operativo y la toma de decisiones.

Mediante reportes y visualizaciones, es posible comparar la puntualidad entre periodos, identificar rutas o aeropuertos con retrasos frecuentes y analizar las principales causas de demora. El Bureau of Transportation Statistics recopila este tipo de información, incluyendo horarios programados y reales, cancelaciones, desvíos y minutos de retraso según su causa (Bureau of Transportation Statistics, s. f.).

De esta manera, la aplicación de BI en el transporte aéreo facilita la identificación de patrones y problemas recurrentes. La información obtenida puede apoyar la planificación de horarios, la asignación de recursos y el seguimiento del desempeño operativo de los vuelos.



## Bibliografía

Bureau of Transportation Statistics. (s. f.). *Reporting carrier on-time performance (1987–present)*. U.S. Department of Transportation. [https://www.transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ](https://www.transtats.bts.gov/DL_SelectFields.aspx?QO_fu146_anzr=b0-gvzr&gnoyr_VQ=FGJ)

IBM. (s. f.). *¿Qué es Business Intelligence (BI)?* [https://www.ibm.com/mx-es/think/topics/business-intelligence](https://www.ibm.com/mx-es/think/topics/business-intelligence)

IBM. (s. f.). *What is a data warehouse?* [https://www.ibm.com/think/topics/data-warehouse](https://www.ibm.com/think/topics/data-warehouse)

IBM. (2021, 30 de julio). *What is OLAP?* [https://www.ibm.com/think/topics/olap](https://www.ibm.com/think/topics/olap)

Kimball Group. (s. f.). *Dimensional modeling techniques*. [https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/)

Kimball, R. (2008, 5 de noviembre). *Fact tables*. Kimball Group. [https://www.kimballgroup.com/2008/11/fact-tables/](https://www.kimballgroup.com/2008/11/fact-tables/)

Microsoft. (s. f.). *Understand star schema and the importance for Power BI*. Microsoft Learn. [https://learn.microsoft.com/en-us/power-bi/guidance/star-schema](https://learn.microsoft.com/en-us/power-bi/guidance/star-schema)

Oracle. (2023, 8 de junio). *What is a data warehouse?* [https://www.oracle.com/database/what-is-a-data-warehouse/](https://www.oracle.com/database/what-is-a-data-warehouse/)

Link de la base de datos completa (drive): https://drive.google.com/file/d/1UJ-2yC9uMcpQJi6i4bS0GQAZNirMcL3X/view?usp=sharing
