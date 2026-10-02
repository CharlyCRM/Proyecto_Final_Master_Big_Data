# Del tráfico aéreo al análisis de datos

Este fue mi proyecto final del máster de Big Data, Análisis de Datos y Machine Learning. El caso propone trabajar para una agencia ficticia, Tokio School Viajes, y estudiar un histórico de pasajeros del aeropuerto de San Francisco.

Empiezo revisando el CSV y sus tipos de datos. Después comparo aerolíneas, regiones y periodos, preparo una copia para cargarla en Cassandra y construyo regresiones con PySpark. El repositorio conserva ese recorrido, desde los cuadernos hasta los informes y la presentación final.

[Ver el proyecto en mi portfolio](https://carlos-ramirez-martin.up.railway.app/es/projects/big-data-analysis/)

## Por dónde empezar

Si quieres conocer el enfoque sin ejecutar código, empieza por el PDF **03 - Científico** y la **04 - Presentación**. Si prefieres seguir el análisis, los cuadernos están en [notebooks/](notebooks/):

- [Exploración y limpieza](notebooks/1.0-crm-initial-data-exploration.ipynb): carga con PySpark, definición del esquema y primeros resúmenes de aerolíneas y regiones.
- [Análisis y regresión](notebooks/2.0-crm-initial-data-analitic.ipynb): estadísticas, visualizaciones y modelos que utilizan calendario, aerolínea y región.
- [Preparación para Cassandra](notebooks/datanull.ipynb): tratamiento de valores ausentes y exportación del CSV con una columna de identificación.

El archivo utilizado está en [data/](data/). Los PDF de la raíz recogen la configuración del entorno, las tareas técnicas de Cassandra y PySpark, los resultados y su presentación. `Big Data_Proyecto Final.pdf` es el enunciado académico, no una descripción de una aplicación en producción.

## Qué muestra el trabajo

El análisis compara recuentos de pasajeros entre aerolíneas y regiones, revisa su evolución y prueba modelos de regresión lineal. Combina PySpark, scikit-learn, NumPy, pandas, Matplotlib y Seaborn; la parte de almacenamiento se documenta con Cassandra.

Cada fila del dataset es un registro agregado, no un vuelo individual. Por eso, contar filas por región no equivale a contar vuelos, y una media por registro no es un total anual de pasajeros.

## Cómo leer sus resultados

Es un trabajo académico, no un sistema validado para planificar rutas o anticipar la demanda de una agencia. Las regresiones de PySpark usan una separación aleatoria 80/20, no un test temporal. Las rectas ajustadas sobre secuencias describen los datos usados en el ajuste, sin demostrar capacidad para predecir el futuro.

Una parte del ejercicio calcula correlaciones después de asignar índices numéricos a categorías. Esos índices no tienen un orden natural, así que los valores de esa matriz no deben leerse como una medida fiable de asociación entre categorías. Los cuadernos explican esta limitación junto al cálculo.

También conviene revisar la cobertura de los años antes de compararlos y no atribuir un significado a `Adjusted Passenger Count` o a la categoría de precio `other` sin consultar su definición. Mantengo las salidas originales; la revisión de documentación aclara su lectura, no recalcula el análisis ni modifica los informes entregados.

## Abrir los cuadernos

Puedes leerlos directamente en GitHub. Para ejecutarlos necesitas Jupyter, Java y un entorno compatible con PySpark, además de las librerías importadas en cada cuaderno. La configuración original está descrita en el PDF **01 - Configuración**; el repositorio no incluye un entorno de dependencias fijado que garantice una instalación automática actual.

Revisa antes las rutas: los cuadernos de PySpark buscan el CSV en `work/data/` y el de Cassandra conserva rutas absolutas del entorno original. Algunas celdas escriben archivos o sobrescriben exportaciones. Ejecuta sobre una copia de trabajo y adapta las rutas a tu entorno, sin apuntarlas a documentos originales que quieras conservar.

Este proyecto no tiene demo desplegada ni API pública. GitHub permite consultar los cuadernos, datos e informes, pero no ejecuta el análisis.

## Autoría y materiales

Carlos Ramírez Martín. Los informes y cuadernos corresponden a mi trabajo final; el enunciado pertenece al centro de formación. El repositorio no incluye una licencia de redistribución explícita para todo el material: su publicación no implica que los datos o documentos docentes tengan licencia MIT.
