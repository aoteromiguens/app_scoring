# 🚀 Análisis Inteligente del Riesgo de Crédito

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/aoteromiguens/app_scoring/blob/main/notebooks/scoring.ipynb)

Este repositorio contiene el código, los modelos pre-entrenados y la interfaz de inferencia interactiva del proyecto, desarrollado como trabajo final para la Tecnicatura en Data Science. 

Las entidades financieras enfrentan múltiples desafíos para evaluar correctamente el riesgo de crédito en un contexto cambiante, lidiando con evaluaciones ineficientes, falta de personalización y altas tasas de morosidad. Proponemos una solución mediante Ciencia de Datos y Machine Learning para lograr una gestión de riesgo eficiente, interpretable y con mitigación de sesgos.

## 🧠 Arquitectura de Modelos (Score Híbrido)

El sistema no depende de un único algoritmo, sino que utiliza un ensamble de modelos para calcular un **Score Temporal** ponderado y determinar el Nivel de Riesgo Final del cliente:

*   **Preprocesamiento:** `mi_scaler_limpio.joblib` para la estandarización de variables.
*   **Modelo Predictivo Base:** `random_forest_model_base.joblib` (Ponderación del 50% en el score final).
*   **Segmentación de Clientes (Clustering):** 
    *   `modelo_kmeans_k3.joblib` (Ponderación del 30%).
    *   `modelo_kmeans_k2.joblib` (Ponderación del 20%).
*   **Detección de Patrones Extremos:** `dbscan_classifier_for_inference.joblib` actúa como un filtro prioritario para clasificar automáticamente perfiles atípicos como "ALTO EXTREMO" o "BAJO PREMIUM".

## ⚙️ Cómo probar la herramienta

El entorno está configurado para ejecutarse de manera transparente en Google Colab, incluyendo una interfaz gráfica de usuario.

1. Hacé clic en el botón **Open in Colab** en la parte superior de este documento.
2. En el menú superior de Colab, seleccioná `Entorno de ejecución` > `Ejecutar todas`.
3. El notebook descargará el repositorio, cargará los archivos `.joblib` automáticamente y desplegará la interfaz de usuario.
4. Ingresá los datos del cliente (Salario Mensual, Historial de Crédito, EMI Total, etc.) y hacé clic en **"Calcular Riesgo"**. 
5. El sistema generará el Score y dibujará un termómetro de riesgo analítico.

## 📊 Variables Analizadas

La herramienta permite el ingreso interactivo de datos clave para la inferencia dinámica:
*   Salario Mensual y Balance Mensual.
*   EMI Total Mensual e Historial de Crédito en Meses.
*   Cantidad Total de Productos e Inversiones Mensuales.
*   Tasa de Interés y Consultas de Crédito en el último año.
*   *Feature Engineering Automático:* El sistema calcula internamente métricas como el ratio `EMI_to_Income` y la `Product_Density`.


## 👥 Equipo de Desarrollo

Este proyecto fue desarrollado en conjunto para el trabajo final de la Tecnicatura en Data Science por:
*   **Mariana Cecilia Guzman ** - https://www.linkedin.com/in/mariana-guzm%C3%A1n-453b52190/ | https://github.com/MarianaGuz  
*   **Alejandro Otero Miguens** - https://www.linkedin.com/in/alejandro-otero-miguens-842926217 | https://github.com/aoteromiguens


## 📁 Estructura del Repositorio

```text
├── models/
│   ├── mi_scaler_limpio.joblib
│   ├── random_forest_model_base.joblib
│   ├── modelo_kmeans_k2.joblib
│   ├── modelo_kmeans_k3.joblib
│   └── dbscan_classifier_for_inference.joblib
├── notebooks/
│   └── scoring.ipynb
└── README.md

