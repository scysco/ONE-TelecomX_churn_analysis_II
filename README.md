# 📊 Análisis y Predicción de Evasión de Clientes (Churn) - Telecom X

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.x-blue.svg?style=for-the-badge&logo=pandas)
![Plotly](https://img.shields.io/badge/Plotly-5.x-blue.svg?style=for-the-badge&logo=plotly)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-blue.svg?style=for-the-badge&logo=scikit-learn)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](AQUÍ_VA_EL_ENLACE_A_TU_NOTEBOOK_EN_GITHUB)

---

## 📜 Tabla de Contenidos
1.  [Visión General del Proyecto](#-visión-general-del-proyecto)
2.  [Instalación y Dependencias](#-instalación-y-dependencias)
3.  [Diccionario de Datos](#-diccionario-de-datos)
4.  [Resumen del Análisis y Modelado](#-resumen-del-análisis-y-modelado)
5.  [Resultados y Conclusiones Principales](#-resultados-y-conclusiones-principales)
6.  [Recomendaciones Estratégicas](#-recomendaciones-estratégicas)
7.  [Cómo Utilizar este Repositorio](#-cómo-utilizar-este-repositorio)

---

## 🎯 Visión General del Proyecto
Este proyecto presenta un análisis de datos de extremo a extremo sobre un conjunto de datos de la empresa de telecomunicaciones "Telecom X". El proyecto se divide en dos fases principales:
1.  **Análisis Exploratorio de Datos (EDA)**: Para identificar los factores y perfiles de clientes más asociados con la evasión (churn).
2.  **Modelado Predictivo**: Para construir y evaluar un modelo de machine learning capaz de predecir qué clientes tienen una alta probabilidad de cancelar su servicio.

El objetivo final es proporcionar insights accionables para el negocio y una herramienta predictiva para reducir la tasa de evasión, que se identificó en un **26.54%**.

---

## 🔧 Instalación y Dependencias
Para ejecutar el análisis contenido en el notebook de Jupyter, necesitarás tener Python 3.10 o superior y las siguientes librerías instaladas. Se recomienda crear un entorno virtual.

```bash
pip install pandas numpy plotly scikit-learn imbalanced-learn seaborn matplotlib jupyterlab
````

-----

## 📖 Diccionario de Datos

A continuación se describen las columnas clave del dataset final utilizado para el modelado:

| Columna | Descripción | Tipo de Dato | Ejemplo |
|---|---|---|---|
| **`Churn`** | Variable objetivo. 1 si el cliente se fue, 0 si permanece. | `int64` | `1`, `0` |
| **`tenure`** | Meses de antigüedad del cliente en la compañía. | `int64` | `12`, `72` |
| **`Contract`** | Tipo de contrato del cliente. | `category` | `Month-to-month`, `One year` |
| **`InternetService`** | Tipo de servicio de internet contratado. | `category` | `Fiber optic`, `DSL`, `No` |
| **`TechSupport`** | Si el cliente tiene o no soporte técnico. | `category` | `Yes`, `No` |
| **`Charges.Monthly`**| Gasto mensual del cliente. | `float64` | `75.50` |
| **`Cuentas_Diarias`**| Gasto diario promedio del cliente. | `float64` | `2.48` |

-----

## 🔬 Resumen del Análisis y Modelado

El flujo de trabajo del proyecto siguió una metodología estructurada:

1.  **Limpieza y Preparación de Datos**: Se cargaron los datos desde un JSON, se normalizaron y se sometieron a un riguroso proceso de limpieza para manejar valores nulos, vacíos y tipos de datos incorrectos. Las variables fueron codificadas a formato numérico.
2.  **Análisis Exploratorio (EDA)**: Se desglosó la tasa de evasión por múltiples variables demográficas, de contratación y de servicios para identificar los factores de mayor impacto.
3.  **Balanceo de Clases**: Se utilizó la técnica **SMOTE** para corregir el desbalance en la variable objetivo, creando un conjunto de datos de entrenamiento robusto.
4.  **Entrenamiento y Evaluación de Modelos**: Se entrenaron y evaluaron dos modelos: **Regresión Logística** (con estandarización) y **Random Forest**.
5.  **Selección del Mejor Modelo**: Se compararon las métricas de rendimiento, seleccionando el modelo con la mejor capacidad para identificar a los clientes en riesgo.

-----

## 💡 Resultados y Conclusiones Principales

### Hallazgos del Análisis Exploratorio

  * El **tipo de contrato** es el factor más determinante, con una tasa de evasión del **42.71%** para clientes "Mes a Mes".
  * La falta de servicios clave como **Soporte Técnico** y **Seguridad en Línea** aumenta drásticamente el riesgo.
  * El pago con **Cheque Electrónico** está asociado a la tasa de churn más alta (45.26%).

### Resultados del Modelo Predictivo

  * El modelo **Random Forest** fue seleccionado como el de mejor rendimiento, con una **exactitud general del 84%**.
  * La métrica de negocio más importante, el **Recall** para la clase "Churn", fue del **84%**. Esto significa que el modelo **identifica correctamente a 84 de cada 100 clientes que realmente van a cancelar el servicio**.
  * El análisis de **importancia de variables** del modelo confirmó los hallazgos del EDA, destacando la antigüedad (`tenure`), el gasto (`Charges.Monthly` y `Charges.Total`) y el tipo de contrato como los predictores más fuertes.

-----

## 🚀 Recomendaciones Estratégicas

Las conclusiones del análisis y el modelo predictivo dan lugar a las siguientes recomendaciones:

1.  **Fidelizar Clientes "Mes a Mes"**: Crear campañas proactivas para migrar a clientes de alto riesgo a contratos de 1 o 2 años.
2.  **Empaquetar Servicios de Retención**: Ofrecer Soporte Técnico y Seguridad en Línea de forma atractiva a los clientes de Fibra Óptica.
3.  **Optimizar la Experiencia de Pago**: Incentivar el cambio de Cheque Electrónico a métodos de pago automáticos.
4.  **Operacionalizar el Modelo**: Implementar el modelo guardado (`modelo_churn_random_forest.pkl`) en un sistema de producción para generar alertas de riesgo de churn en tiempo real.

-----

## 💻 Cómo Utilizar este Repositorio

Hay dos maneras de ejecutar este análisis:

### 1\. Ejecución Local (con Jupyter)

Clona el repositorio en tu máquina local:

```bash
git clone https://github.com/scysco/ONE-TelecomX_churn_analysis_II.git
```

Navega a la carpeta del proyecto e instala las dependencias:

```bash
cd ONE-TelecomX_churn_analysis_II
pip install -r requirements.txt # (Asegúrate de crear un archivo requirements.txt)
```

Inicia Jupyter Lab y abre el notebook:

```bash
jupyter lab
```

### 2\. Ejecución en la Nube (con Google Colab)

Puedes abrir y ejecutar este notebook directamente en Google Colab sin necesidad de instalar nada.

  * **Opción A (Recomendada)**: Haz clic en el botón "Open In Colab" que se encuentra en la parte superior de este README.
      * **Nota**: Deberás reemplazar `AQUÍ_VA_EL_ENLACE_A_TU_NOTEBOOK_EN_GITHUB` en el código del botón con la URL directa a tu archivo `.ipynb` en tu repositorio de GitHub.
  * **Opción B (Manual)**:
    1.  Ve a [Google Colab](https://colab.research.google.com/).
    2.  Selecciona la pestaña "GitHub", pega la URL de tu repositorio y presiona Enter.
    3.  Selecciona el notebook de la lista para abrirlo.

<!-- end list -->