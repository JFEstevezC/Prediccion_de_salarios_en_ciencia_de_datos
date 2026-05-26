# 📘 IA1 - Predicción y Análisis de Salarios en Ciencia de Datos

![Portada](Portada.jpeg)

**Curso:** *Inteligencia Artificial I — 2025-1*  
**👥 Equipo:**  
- Jairo Armando Cardozo Mendoza — *2224637*  
- Jose Fernando Estévez Cárdenas — *2224646*  
- Rances Alejandro Ramirez Morillo — *2234514*  

---

## 🗂️ Contenidos
- [Dataset](#dataset)
- [Preguntas a responder](#preguntas-a-responder)
  - [Antes del EDA (conceptual)](#antes-del-eda-conceptual)
  - [Después del EDA (resumen)](#después-del-eda-resumen)
- [Hipótesis inicial y modelos planeados](#hipótesis-inicial-y-modelos-planeados)
- [Tecnologías](#tecnologías-a-utilizar)
- [Resumen de modelos utilizados](#resumen-de-modelos-utilizados)
- [Flujo del proyecto](#flujo-del-proyecto)
- [Video](#video)

---

## 📊 Dataset

- **Nombre:** *Data Science Salaries 2024*  
- **Fuente externa:** Kaggle  
  - **Enlace:** https://www.kaggle.com/datasets/yusufdelikkaya/datascience-salaries-2024/data  
  - **Descarga:**  
    1. Crear cuenta en Kaggle  
    2. Ingresar al enlace  
    3. Clic en *Download Dataset*  
    4. Colocar el archivo `.csv` dentro de `/data/`

- **Ubicación en Google Drive:**  
  - [Enlace al dataset en Drive](https://drive.google.com/file/d/1_8c6R9e31gYUGCfC9TXeRSF0m8Zg0um-/view?usp=sharing)

- **Tamaño:** `14,838 registros × 11 columnas`

---

## ❓ Preguntas a responder

### Antes del EDA (conceptual)

> **Problema y relevancia:**  
> El mercado de trabajo en ciencia de datos es altamente variable: los salarios dependen del nivel de experiencia, tipo de empleo, ubicación y tamaño de la empresa. Contar con un modelo predictivo permite a profesionales y empresas tomar mejores decisiones salariales.

> **Objetivo del análisis:**  
> Analizar las relaciones entre las variables del dataset, identificar los factores que más influyen en el salario, y construir modelos de Machine Learning y Deep Learning capaces de predecir el salario en USD (`salary_in_usd`).

> **Métricas o indicadores:**  
> - MAE (Mean Absolute Error) en USD  
> - RMSE (Root Mean Squared Error)  
> - R² (Coeficiente de determinación)  
> - Silhouette Score y ARI para clustering  

> **Motivación de la elección:**  
> Es un problema con impacto real en el mercado laboral y permite aplicar de forma práctica técnicas de regresión, clustering y reducción de dimensionalidad vistas en el curso.

---

### Después del EDA (resumen)

📌 **Datos utilizados (máx. 50 palabras):**  
> Dataset con información de empleos en ciencia de datos entre 2020 y 2024, que incluye nivel de experiencia, tipo de contrato, cargo, ubicación del empleado y la empresa, modalidad de trabajo remoto, y salario en USD. Adecuado para regresión y análisis no supervisado.

📌 **Información contenida (máx. 100 palabras):**  
> Contiene 11 variables numéricas y categóricas: año del salario (`work_year`), nivel de experiencia (`experience_level`: EN/MI/SE/EX), tipo de empleo (`employment_type`: FT/PT/CT/FL), cargo (`job_title`), salario original, moneda, salario en USD (`salary_in_usd`), residencia del empleado, porcentaje remoto (0/50/100), ubicación de la empresa y tamaño de la empresa (S/M/L). La variable objetivo es `salary_in_usd`. Permite análisis predictivo y exploratorio del mercado laboral en ciencia de datos.

📌 **Desafíos asociados a los datos (máx. 100 palabras):**  
> La variable `salary_in_usd` presenta alto sesgo positivo con outliers significativos. Las variables categóricas como `job_title` tienen alta cardinalidad. La clase dominante en `employment_type` es FT (Full-Time), lo que genera desbalance. La mayoría de registros provienen de empresas medianas con trabajadores senior, lo que puede sesgar los modelos. Para clustering, la baja separación entre grupos de `employment_type` en el espacio PCA implica un ARI bajo esperado, según lo anticipado en clase.

---

## 🧠 Hipótesis inicial y modelos planeados

### ✔ Hipótesis inicial
> Antes del análisis, el equipo asumía que:  
> - **Nivel de experiencia** (`experience_level`),  
> - **Cargo** (`job_title`),  
> - **Tipo de empleo** (`employment_type`), y  
> - **Tamaño de la empresa** (`company_size`)  
> serían los factores más determinantes del salario.

También se esperaba que **Random Forest** tuviera el mejor desempeño por su capacidad para manejar variables categóricas con alta cardinalidad.

### ✔ Modelos planeados
- **Regresión:** Decision Tree Regressor, Random Forest Regressor, SVR, Deep Learning (MLP)  
- **No supervisado:** K-Means, DBSCAN  
- **Dimensionalidad:** PCA  

---

## 🛠️ Tecnologías a utilizar
- **Lenguaje:** Python 🐍  
- **Librerías:**  
  - Pandas  
  - NumPy  
  - Matplotlib  
  - Scikit-learn  
  - TensorFlow / Keras  
- **Entorno:** Google Colab  
- **Acceso al notebook:** [Google Colab](https://drive.google.com/file/d/1_8c6R9e31gYUGCfC9TXeRSF0m8Zg0um-/view?usp=sharing)  
- **Repositorio:** [GitHub](https://github.com/JFEstevezC/Prediccion_de_salarios_en_ciencia_de_datos)

---

## 📦 Resumen de modelos utilizados

| Tipo                 | Modelos usados                                                               |
|----------------------|------------------------------------------------------------------------------|
| **Regresión**        | Decision Tree Regressor, Random Forest Regressor, SVR, Deep Learning (MLP)  |
| **No supervisado**   | K-Means, DBSCAN                                                              |
| **Dimensionalidad**  | PCA                                                                          |

---

### 🔍 Detalle de los modelos de regresión

| Modelo       | Descripción                                          | Métrica principal |
|--------------|------------------------------------------------------|-------------------|
| **DT**       | DecisionTreeRegressor — tuning: `max_depth`          | MAE (USD)         |
| **RF**       | RandomForestRegressor — tuning: `n_estimators`       | MAE (USD)         |
| **SVR**      | SVR — kernels: `linear`, `poly`, `rbf`               | MAE (USD)         |
| **DL Arch1** | MLP: input → [64, 128, 128] → 1                      | MAE (USD)         |
| **DL Arch2** | MLP: input → [64, 64, 128, 128, 256, 256] → 1       | MAE (USD)         |
| **DL Arch3** | MLP: input → [128, 128, 128] → 1                    | MAE (USD)         |

### 🔍 Detalle del clustering

| Método      | Parámetros clave              | Evaluación                     |
|-------------|-------------------------------|-------------------------------|
| **K-Means** | `n_clusters=4` (= num. clases) | Silhouette Score, ARI vs GT   |
| **DBSCAN**  | `eps` (por codo k-distancia), `min_samples=5` | Silhouette Score, ARI vs GT |

> **Ground Truth:** `employment_type` (FT, PT, CT, FL — 4 clases)  
> Las features se reducen a 2 componentes con **PCA** antes de aplicar clustering.

---

## 🚀 Flujo del proyecto

```
Dataset (Kaggle)
      ↓
  Limpieza y codificación
  (duplicados, nulos, LabelEncoder, OrdinalEncoder)
      ↓
  EDA (pie charts, histogramas, boxplots, IQR outliers)
      ↓
  Partición 80/20 + StandardScaler
      ↓
  ┌───────────────────────────────────┐
  │       MODELOS DE REGRESIÓN        │
  │  DT → RF → SVR → DL (MLP)        │
  │  Cross-Validation (k-fold)        │
  └───────────────────────────────────┘
      ↓
  ┌───────────────────────────────────┐
  │     APRENDIZAJE NO SUPERVISADO    │
  │  MinMaxScaler → PCA (→ 2D)        │
  │  K-Means (n=4) → DBSCAN           │
  │  Comparación: Original/KMeans/DBSCAN │
  └───────────────────────────────────┘
      ↓
  Resumen y comparación de resultados
```

---

## 🎥 Video
Video resumen del proyecto:

🔗 **[Enlace al video](#)**

---
