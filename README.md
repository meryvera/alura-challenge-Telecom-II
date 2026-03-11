# 📡 Telecom X – Parte 2: Predicción de Evasión (Churn)

## 🎯 Propósito del Proyecto
Este análisis busca resolver uno de los problemas más críticos de **Telecom X**: la pérdida de clientes. El objetivo principal es construir y evaluar modelos de **Machine Learning** que identifiquen automáticamente a los clientes con alta probabilidad de cancelar su suscripción (*Churn*), basándose en su comportamiento histórico y perfil financiero.

---

## 📂 Estructura y Organización
El proyecto se compone de los siguientes elementos clave:
* **TelecomX_LATAM.ipynb**: Notebook de Google Colab que contiene el pipeline completo (Preprocesamiento, Entrenamiento, Evaluación).
* **TelecomX_Data_Limpio.json**: Base de datos tratada en la Fase 1, con limpieza de nulos e inconsistencias corregidas.
* **Resultados**: Se incluyen matrices de confusión y gráficos de importancia de variables generados durante el análisis.

---

## 🛠️ Proceso de Preparación de Datos

### 1. Clasificación de Variables
Identificamos la naturaleza de nuestros datos para aplicar el tratamiento correcto:
* **Numéricas:** `customer_tenure`, `account_Charges_Monthly`, `account_Charges_Total` y `Cuentas_Diarias`.
* **Categóricas:** `customer_gender`, `customer_Partner`, `account_Contract`, `internet_InternetService`, entre otras.

### 2. Codificación (Encoding)
Como los modelos de ML no procesan texto, aplicamos **One-Hot Encoding** utilizando `pd.get_dummies()`. Esto transforma categorías como "Tipo de Contrato" en columnas binarias (0 y 1), evitando jerarquías falsas entre categorías.

### 3. Normalización y Estandarización
Para modelos sensibles a la escala (como la Regresión Logística), aplicamos `StandardScaler`. Esto asegura que variables con valores altos (como el Gasto Total) no tengan más peso que variables con rangos pequeños de forma artificial.

### 4. División del Dataset
Los datos se separaron en:
* **Entrenamiento (80%)**: Para ajustar los parámetros de los modelos.
* **Prueba (20%)**: Para validar el rendimiento real con datos no vistos.

---

## 📊 Insights y Visualizaciones (EDA)

Durante el análisis exploratorio, destacamos los siguientes hallazgos:

* **Impacto del Contrato:** Los clientes con contratos "Mes a mes" representan la gran mayoría del Churn.
* **Lealtad Temporal:** Existe una caída drástica en la evasión después de los primeros 12 meses de permanencia.
* **Relación de Cargos:** Los clientes que cancelan suelen tener una media de cargos mensuales superior a los que permanecen.



---

## 🤖 Modelado y Evaluación

Se implementaron dos enfoques distintos para asegurar robustez:
1.  **Regresión Logística:** Modelo lineal que permite interpretar la influencia de cada variable a través de sus coeficientes.
2.  **Random Forest:** Modelo basado en conjuntos de árboles, excelente para capturar relaciones no lineales y proporcionar la "importancia de las variables".

### Justificación de Métricas
Se priorizó el **Recall** y el **F1-Score** sobre la Exactitud, ya que para Telecom X es más costoso no detectar a un cliente que se va (Falso Negativo) que ofrecer una promoción a alguien que pensaba quedarse.



---

## 🚀 Instrucciones de Ejecución

1.  **Entorno:** Se recomienda el uso de **Google Colab** o Jupyter Notebook.
2.  **Bibliotecas Necesarias:**
    ```python
    pip install pandas numpy matplotlib seaborn scikit-learn
    ```
3.  **Carga de Datos:**
    * Subir el archivo `TelecomX_Data_Limpio.json` a la sesión de Colab.
    * Ejecutar las celdas en el orden establecido en el notebook.

---

**Analista Responsable:** [Tu Nombre]  
**Proyecto:** Telecom X - Data Science LATAM
