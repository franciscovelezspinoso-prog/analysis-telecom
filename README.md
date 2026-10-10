# analysis-telecom
# ConnectaTel Analysis – Sprint 7

Este repositorio contiene el proyecto final del Sprint 7: un análisis del comportamiento de los clientes de **ConnectaTel**, una empresa de telecomunicaciones en Latinoamérica, con datos registrados hasta 2024.

## 🧠 Objetivo del proyecto

- Identificar y corregir problemas de calidad de datos (nulos, valores centinela y fechas imposibles).
- Resumir el uso de cada cliente (mensajes, llamadas y minutos de llamada).
- Analizar distribuciones y outliers según el tipo de plan.
- Segmentar a los clientes por nivel de uso y por edad.
- Generar un análisis ejecutivo con hallazgos y recomendaciones para mejorar la oferta de planes.

## 📂 Contenido del repositorio

- `notebooks/S7_Version-Estudiante-Project-ConnectaTel.ipynb`
  → Notebook principal con limpieza, análisis exploratorio, visualizaciones, outliers, segmentación y conclusiones.
- `README.md`
  → Este archivo.

## 🗃️ Datasets utilizados

| Archivo | Contenido | Filas |
|---|---|---|
| `plans.csv` | Planes Básico y Premium: precio mensual, mensajes, minutos y GB incluidos, y costo por extra | 2 |
| `users_latam.csv` | Datos de los usuarios: edad, ciudad, fecha de registro, plan y fecha de baja | 4,000 |
| `usage.csv` | Registros de uso: tipo (llamada o mensaje), fecha, duración y longitud | 40,000 |

## 🔎 Etapas del análisis

1. **Carga y exploración:** carga de los tres datasets, revisión de estructura, tipos de datos y vista previa.
2. **Calidad de datos:** detección de nulos, valores centinela (`-999` en `age`, `?` en `city`) y fechas fuera de rango (año 2026).
3. **Limpieza:** `age` con -999 imputada con la mediana; `city` inválida y fechas imposibles marcadas como nulas; nulos de `duration` y `length` conservados, porque dependen del tipo de registro (MAR).
4. **Resumen por usuario:** agregación de `usage` por `user_id` (mensajes, llamadas y minutos) y unión con `users`.
5. **Distribuciones y outliers:** histogramas por plan, boxplots y límites por método IQR. Los outliers se mantuvieron por ser consumos plausibles.
6. **Segmentación:** `grupo_uso` (Bajo uso, Uso medio, Alto uso) y `grupo_edad` (Joven, Adulto, Adulto Mayor).
7. **Análisis ejecutivo:** hallazgos, implicaciones y recomendaciones en formato Contexto–Hallazgo–Implicación.

## ▶ Cómo abrir el notebook en Google Colab

Haz clic en el siguiente botón:



O bien:

1. Abre el archivo `.ipynb` en GitHub.
2. Haz clic en **Open in Colab** (si tienes la extensión) o copia la URL del archivo en `colab.research.google.com` → **GitHub**.

## 🔁 Guía de reproducción

1. Abre `notebooks/S7_Version-Estudiante-Project-ConnectaTel.ipynb`.
2. Ten disponibles los tres archivos CSV (`plans.csv`, `users_latam.csv` y `usage.csv`).
3. El notebook los lee desde la carpeta `/datasets/`. Si lo ejecutas en Colab, sube los CSV al entorno y ajusta las rutas de la celda de carga, por ejemplo `pd.read_csv('plans.csv')`.
4. Ejecuta las celdas en orden, de arriba hacia abajo.
5. Librerías necesarias: `pandas`, `numpy`, `seaborn` y `matplotlib`.

## 📌 Conclusión principal

Básico y Premium muestran el mismo patrón de uso de llamadas y mensajes, y el consumo está muy por debajo de lo incluido en ambos planes. Esto sugiere replantear la propuesta de valor de Premium y evaluar un plan de entrada más económico. El detalle completo está en la sección **Paso 7** del notebook
