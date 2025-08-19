# 🤖 Modelo Predictivo de Evasión de Clientes (Churn) - Telecom X

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?style=for-the-badge&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-2.x-blue.svg?style=for-the-badge&logo=pandas)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-blue.svg?style=for-the-badge&logo=scikit-learn)
![imblearn](https://img.shields.io/badge/imbalanced--learn-0.10%2B-blue.svg?style=for-the-badge)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/scysco/ONE-TelecomX_churn_analysis_II/blob/main/TelecomX_LATAM.ipynb)

---

## 📜 Tabla de Contenidos
1.  [Visión General del Proyecto](#-visión-general-del-proyecto)
2.  [Instalación y Dependencias](#-instalación-y-dependencias)
3.  [Flujo de Trabajo del Modelado](#-flujo-de-trabajo-del-modelado)
4.  [Resultados del Modelo Final](#-resultados-del-modelo-final)
5.  [Conclusión y Próximos Pasos](#-conclusión-y-próximos-pasos)
6.  [Cómo Utilizar este Repositorio](#-cómo-utilizar-este-repositorio)

---

## 🎯 Visión General del Proyecto
Este proyecto se centra en el desarrollo de un modelo de machine learning para predecir la evasión de clientes (churn) en la empresa de telecomunicaciones "Telecom X". Partiendo de un conjunto de datos previamente limpiado y analizado en una fase de Análisis Exploratorio (EDA), el objetivo de esta fase es construir, evaluar y seleccionar el clasificador con el mejor rendimiento para identificar a los clientes con mayor riesgo de cancelar su servicio.

---

## 🔧 Instalación y Dependencias
Para ejecutar el código de este notebook, necesitarás tener Python 3.10 o superior y las siguientes librerías. Se recomienda crear un entorno virtual.

```bash
pip install pandas numpy scikit-learn imbalanced-learn seaborn matplotlib jupyterlab
````

-----

## 📈 Flujo de Trabajo del Modelado

El proceso para la construcción del modelo siguió una metodología estructurada para garantizar resultados robustos y fiables:

1.  **Preparación de Datos**: Se cargó el dataset limpio (`telecom_churn_cleaned_data.csv`). Las variables categóricas fueron transformadas a un formato numérico mediante One-Hot Encoding.

2.  **Balanceo de Clases**: Se detectó un desbalance en la variable objetivo (`Churn`). Para corregirlo, se aplicó la técnica de sobremuestreo **SMOTE** al conjunto de datos, creando ejemplos sintéticos de la clase minoritaria para asegurar un entrenamiento equitativo.

3.  **Separación de Datos**: El dataset (ya balanceado) se dividió en un **80% para entrenamiento** y un **20% para prueba** utilizando `train_test_split`.

4.  **Entrenamiento y Evaluación de Modelos**: Se entrenaron y evaluaron dos tipos de modelos:

      * **Regresión Logística**: Un modelo lineal que requirió la estandarización de los datos.
      * **Random Forest**: Un modelo basado en árboles que no requirió estandarización.
        Ambos fueron evaluados con métricas como Precisión, Recall, F1-Score y la Matriz de Confusión.

-----

## 💡 Resultados del Modelo Final

### Selección del Modelo

El modelo de **Random Forest** fue seleccionado como el de mejor rendimiento, superando a la Regresión Logística en todas las métricas clave.

  * **Exactitud General**: **84%**
  * **Recall (para la clase "Churn")**: **84%**
  * **F1-Score (para la clase "Churn")**: **85%**

El alto **Recall** del 84% es el resultado más importante para el negocio, ya que indica que el modelo es capaz de **identificar correctamente a 84 de cada 100 clientes que realmente tienen la intención de cancelar su servicio**.

### Variables Más Importantes

El análisis de importancia de características del modelo Random Forest reveló que los predictores más influyentes son:

1.  **Antigüedad del Cliente (`tenure`)**
2.  **Gasto Mensual (`Charges.Monthly`)**
3.  **Gasto Total (`Charges.Total`)**
4.  **Tener un Contrato de Dos Años (`Contract_Two year`)**

Estos hallazgos confirman cuantitativamente las conclusiones del análisis exploratorio previo.

-----

## 🚀 Conclusión y Próximos Pasos

Hemos desarrollado con éxito un modelo de Random Forest robusto y de alto rendimiento, capaz de predecir la evasión de clientes con una alta tasa de detección. Este modelo proporciona una herramienta valiosa para que los equipos de retención actúen de manera proactiva.

**Próximos Pasos Sugeridos**:

1.  **Optimización de Hiperparámetros**: Realizar una búsqueda de hiperparámetros (ej. con `GridSearchCV`) para exprimir aún más el rendimiento del modelo Random Forest.
2.  **Serialización**: Guardar el modelo entrenado final en un archivo (`.pkl` o `.joblib`) para su uso futuro.
3.  **Implementación (Deployment)**: Crear una API (ej. con Flask o FastAPI) que envuelva al modelo para permitir que genere predicciones en tiempo real sobre nuevos clientes.

-----

## 💻 Cómo Utilizar este Repositorio

Hay dos maneras de ejecutar este análisis:

### 1\. Ejecución Local (con Jupyter)

Clona el repositorio en tu máquina local:

```bash
git clone https://github.com/scysco/ONE-TelecomX_churn_analysis_II.git
```

Navega a la carpeta del proyecto e instala las dependencias.

```bash
cd tu_repositorio
pip install -r requirements.txt
```

Inicia Jupyter Lab y abre el notebook:

```bash
jupyter lab
```

### 2\. Ejecución en la Nube (con Google Colab)

Puedes abrir y ejecutar este notebook directamente en Google Colab.

  * **Opción A (Recomendada)**: Haz clic en el botón "Open In Colab" que se encuentra en la parte superior de este README.

  * **Opción B (Manual)**:
    1.  Ve a [Google Colab](https://colab.research.google.com/).
    2.  Selecciona la pestaña "GitHub", pega la URL de tu repositorio y presiona Enter.
    3.  Selecciona el notebook de la lista para abrirlo.

<!-- end list -->