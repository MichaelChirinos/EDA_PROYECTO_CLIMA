# 🌫️ EDA – Análisis de Calidad del Aire (Índice IMECA)

## 📌 Descripción del Proyecto
Este proyecto se enfoca en la limpieza, preprocesamiento y análisis exploratorio de datos históricos de calidad del aire, específicamente del Índice Metropolitano de la Calidad del Aire (IMECA), para distintas zonas geográficas.

El objetivo principal es consolidar y preparar estos datos para futuros análisis de tendencias, patrones de contaminación y posibles modelos predictivos.

---

## 📂 Origen de los Datos
Los datos provienen de múltiples archivos Excel organizados por año (1996 – 2022).  
Cada archivo contiene mediciones horarias de diversos contaminantes para diferentes zonas:

- Noroeste  
- Noreste  
- Centro  
- Suroeste  
- Sureste  

---

## 🧹 Pasos de Preprocesamiento y Limpieza de Datos

Se realizaron los siguientes procesos clave:

### 1. Carga y consolidación de datos  
Se cargaron múltiples archivos Excel (uno por año) y se concatenaron en un único DataFrame (`df_imeca`) para abarcar todo el período de estudio.

### 2. Unificación de columnas de fecha  
Las columnas `Fecha` y `FECHA` se unificaron en una sola columna utilizando `combine_first()`, priorizando los valores existentes y rellenando los nulos con la otra columna.

### 3. Unificación de columnas de ozono  
Las columnas de Ozono con nombres inconsistentes (por ejemplo, `Noroeste Ozono` y `Noroeste ozono`) se consolidaron en una sola columna por zona.

### 4. Creación de columna Fecha-Hora  
Las columnas `Fecha` y `Hora` se combinaron para crear una columna `Fecha-Hora` de tipo `datetime`, esencial para el análisis de series de tiempo.  
La columna `Hora` se convirtió previamente a tipo `timedelta`.

### 5. Eliminación de columnas redundantes  
Se eliminaron las columnas originales `Fecha`, `Hora` y las columnas duplicadas de Ozono para evitar redundancia.

### 6. Manejo de valores faltantes  
Los valores `-99` (marcadores de datos faltantes en el dataset original) fueron reemplazados por `NaN` para una gestión estándar en Pandas.

### 7. Reordenamiento de columnas  
La columna `Fecha-Hora` se movió al inicio del DataFrame para facilitar la navegación temporal.

### 8. Análisis de columnas PM25  
Se identificó que las columnas `PM25` presentan aproximadamente un **85% de valores faltantes**.  
Debido a la imposibilidad de una imputación efectiva, se planificó su eliminación.

---

## ⏳ Próximos Pasos

- Eliminación de columnas PM25  
- Imputación de valores faltantes restantes mediante interpolación lineal  
- Estandarización de nombres de columnas
- Extracción de variables temporales (año, mes, día de la semana, hora)  
- Análisis estadístico descriptivo  
---

## 🛠️ Herramientas Utilizadas
- Python  
- Pandas  
- NumPy  
- Google Colab  
- Matplotlib / Seaborn  
