# EDA_PROYECTO_CLIMA
Análisis de Datos de Calidad del Aire (Índice IMECA)
*Descripción del Proyecto
Este proyecto se enfoca en la limpieza, preprocesamiento y análisis exploratorio de datos históricos de calidad del aire, específicamente los índices IMECA (Índice Metropolitano de la Calidad del Aire), para varias zonas. El objetivo es consolidar y preparar estos datos para futuros análisis de tendencias, patrones de contaminación y modelado predictivo.

Origen de los Datos
Los datos provienen de múltiples archivos Excel, organizados por año (1996 a 2022), y contienen mediciones horarias de diversos contaminantes para diferentes zonas (Noroeste, Noreste, Centro, Suroeste, Sureste).

Pasos de Preprocesamiento y Limpieza de Datos
Se han realizado los siguientes pasos clave para limpiar y preparar el conjunto de datos:

Carga y Consolidación de Datos: Se cargaron múltiples archivos Excel (uno por año) y se concatenaron en un único DataFrame (df_imeca) para abarcar todo el período de estudio.
Unificación de Columnas de Fecha: Las columnas Fecha y FECHA (presentes en diferentes formatos y periodos) se unificaron en una sola columna Fecha utilizando combine_first(), priorizando los valores existentes y rellenando los nulos con la otra columna.
Unificación de Columnas de Ozono: De manera similar a las fechas, las columnas de Ozono con nombres inconsistentes (ej. Noroeste Ozono y Noroeste ozono) se consolidaron para tener una única columna representativa por zona.
Creación de Columna de Fecha y Hora Combinada: Las columnas Fecha y Hora se combinaron para crear una columna Fecha-Hora unificada de tipo datetime, esencial para el análisis de series de tiempo. La columna Hora se convirtió previamente a tipo timedelta.
Eliminación de Columnas Redundantes: Las columnas originales Fecha y Hora, así como las columnas de Ozono duplicadas ([zona] ozono), se eliminaron para evitar redundancia y mantener el DataFrame limpio.
Identificación y Manejo de Valores Faltantes: Se detectaron y reemplazaron los valores -99 (usados en el dataset original como marcadores de datos faltantes) por NaN (Not a Number) para una gestión estándar de los valores nulos en Pandas.
Reordenamiento de Columnas: La nueva columna Fecha-Hora se movió al inicio del DataFrame para facilitar la navegación y el entendimiento temporal de los datos.
Estrategia para Columnas PM25 y Otros Nulos: Se identificó que las columnas PM25 tienen un porcentaje muy alto de valores faltantes (aproximadamente 85%). Se ha planificado la eliminación de estas columnas debido a la imposibilidad de una imputación efectiva, mientras que los valores nulos restantes con un bajo porcentaje serán tratados mediante interpolación lineal.
Próximos Pasos (Pendientes)
Eliminación de columnas PM25.
Imputación de valores faltantes restantes mediante interpolación lineal.
Estandarización y limpieza de nombres de columnas (ej. minúsculas, sin acentos, guiones bajos).
Establecer la columna Fecha-Hora como índice del DataFrame para optimizar operaciones de series temporales.
Extracción de características temporales (año, mes, día de la semana, hora del día).
Análisis estadístico descriptivo y visualización de la distribución de los datos.
Visualización de tendencias de contaminantes clave a lo largo del tiempo.
