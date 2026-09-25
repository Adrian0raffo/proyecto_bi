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

## 2. Descripción de la empresa y problemática

### 2.1. Descripción de la empresa
La empresa elegida para desarrollar el proyecto es American Airlines, cuya principal actividad consiste en proveer servicios de transporte aéreo comercial de pasajeros y carga a nivel nacional e internacional. La compañía cuenta con una extensa red de destinos y complementa sus operaciones con servicios como el programa de fidelización AAdvantage, las salas Admirals Club y su división logística American Airlines Cargo. Asimismo, forma parte de la alianza internacional oneworld. 

Para sostener esta amplia cobertura, American Airlines basa su estructura logística en un modelo de red de centros de conexión (Hub and Spoke), mediante la cual coordina miles de despegues diarios desde aeropuertos estratégicos. Entre ellos se encuentran Dallas/Fort Worth, Charlotte, Chicago, Miami, Nueva York, Los Ángeles, Filadelfia, Phoenix y Washington. La dimensión de estas operaciones permite mantener una amplia cobertura, pero también genera una elevada interdependencia entre vuelos, aeronaves, aeropuertos y horarios. 

Así, debido a esta elevada magnitud de operaciones, la compañía genera grandes volúmenes de datos relacionados con vuelos, rutas, aeropuertos, horarios, retrasos y cancelaciones. Esta información resulta adecuada para aplicar herramientas de Business Intelligence que permitan evaluar el desempeño operativo e identificar patrones asociados con problemas de puntualidad. Aunque American Airlines realiza vuelos nacionales e internacionales, el presente proyecto analizará únicamente sus operaciones domésticas dentro de Estados Unidos, debido a que la fuente seleccionada corresponde a los registros publicados por el Bureau of Transportation Statistics. 

### 2.2. Problemática
El sector aeronáutico presenta una alta sensibilidad al tiempo, por lo cual la puntualidad constituye un aspecto importante del desempeño de una aerolínea. Los retrasos, las cancelaciones y los desvíos pueden alterar la programación de aeronaves y tripulaciones, afectar el uso de la infraestructura aeroportuaria y generar inconvenientes para los pasajeros. Según el Bureau of Transportation Statistics, un vuelo se considera retrasado cuando llega o sale 15 minutos o más después del horario programado. 

- **Impacto en la eficiencia operativa:** Las demoras durante la salida, el vuelo o la llegada pueden incrementar el tiempo total de una operación y afectar la utilización de aeronaves y tripulaciones. Asimismo, las cancelaciones y los retrasos prolongados pueden requerir ajustes en la programación y generar gastos adicionales para la aerolínea. Aunque la base empleada no contiene los costos monetarios ocasionados por estas situaciones, sí permite analizar variables operativas como el tiempo de taxi, la duración del vuelo, los minutos de retraso y el número de cancelaciones.
- **Impacto en la puntualidad:** Las interrupciones en el servicio pueden generar un efecto dominó. Por ejemplo, un retraso inicial causado por la llegada tardía de una aeronave puede afectar los vuelos posteriores programados para ese avión y sus respectivas tripulaciones. El Bureau of Transportation Statistics clasifica las causas de demora en cinco categorías generales: factores atribuibles a la aerolínea, clima extremo, Sistema Nacional de Aviación, seguridad y llegada tardía de la aeronave anterior.
- **Impacto en los pasajeros:** Los retrasos y las cancelaciones prolongan el tiempo de espera, pueden ocasionar la pérdida de conexiones y obligar a modificar los itinerarios de los pasajeros. Estas situaciones pueden afectar negativamente su experiencia de viaje. Sin embargo, debido a que la base seleccionada no contiene encuestas de satisfacción ni información individual de los pasajeros, este impacto será considerado como una consecuencia de la problemática y no como una variable medida directamente en el proyecto. 

American Airlines realiza una gran cantidad de vuelos domésticos en Estados Unidos, cuyo desempeño operativo puede verse afectado por retrasos, cancelaciones y desvíos. Estos eventos varían según factores como la fecha, el horario, la ruta, los aeropuertos involucrados y las causas de demora. Debido al elevado volumen de registros y a la diversidad de variables operativas, resulta difícil identificar patrones y determinar qué factores concentran los mayores problemas mediante consultas convencionales.

Por ello, existe la necesidad de integrar y organizar esta información mediante una solución de Business Intelligence que permita analizar el desempeño operativo de los vuelos domésticos de American Airlines. La solución facilitará el seguimiento de indicadores de puntualidad, retrasos, cancelaciones y desvíos, así como la identificación de los periodos, rutas, aeropuertos y causas que presentan mayores incidencias. De esta manera, se proporcionará información que pueda apoyar la planificación y la toma de decisiones operativas.

### 2.3. Objetivo general
Diseñar e implementar una solución de Business Intelligence para analizar el proceso operativo de la aerolínea American Airlines, estructurada mediante un modelo en estrella e integrada con los registros del Bureau of Transportation Statistics, con el fin de transformar grandes volúmenes de datos operativos en información analítica que permita identificar patrones de retraso, rutas y aeropuertos críticos, franjas horarias con mayor incidencia y causas de interrupción, apoyando la toma de decisiones orientadas a mejorar la puntualidad y la eficiencia operativa. 

### 2.4. Objetivos específicos
- **Consolidar y preparar la fuente de datos operativa:** Extraer, limpiar y transformar los registros de vuelos del Bureau of Transportation Statistics para construir una base de datos analítica estandarizada, validando posibles inconsistencias y valores faltantes.
- **Analizar los patrones temporales de demoras:** Identificar las franjas horarias del día y los días de la semana con mayor promedio de retrasos y mayor frecuencia de vuelos demorados por más de 15 minutos.
- **Evaluar el comportamiento operativo por rutas y aeropuertos:** Determinar las rutas de origen a destino y los aeropuertos que concentran el mayor tiempo promedio de retraso en las llegadas y la mayor tasa de cancelaciones de vuelos.
- **Analizar las causas de las interrupciones:** Clasificar los minutos de demora según causas atribuibles a la aerolínea, clima, Sistema Nacional de Aviación, seguridad o llegada tardía de aeronaves, evaluando la participación de esta última causa en los retrasos registrados por la compañía.
- **Diseñar el Data Mart multidimensional y los tableros de control:** Construir un modelo dimensional en estrella con al menos ocho dimensiones y desarrollar tableros de control interactivos que faciliten el monitoreo del desempeño operativo y la puntualidad para apoyar la toma de decisiones.

### 2.5. Preguntas de negocio

#### Análisis por tiempo y horarios
- ¿Cuáles son las franjas horarias del día en las que se registran los mayores minutos promedio de demora en la salida?
- ¿En qué días de la semana se concentra la mayor cantidad de vuelos retrasados por más de 15 minutos?

#### Análisis por ubicación y rutas
- ¿Qué rutas presentan el mayor tiempo promedio de retraso en la llegada?
- ¿Qué aeropuertos de origen registran la mayor proporción de vuelos cancelados respecto del total de salidas programadas?

#### Análisis por causas de demora
- ¿Qué causa acumula el mayor volumen de minutos de retraso entre factores atribuibles a la aerolínea, clima, Sistema Nacional de Aviación, seguridad y llegada tardía de aeronaves?
- ¿Qué proporción del total de minutos de demora clasificados por causa corresponde a la llegada tardía de la aeronave anterior?

#### Análisis de cancelaciones y desvíos
- ¿Cuáles son las causas de cancelación más frecuentes?
- ¿En qué rutas, aeropuertos y periodos se registra la mayor proporción de vuelos desviados?

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
