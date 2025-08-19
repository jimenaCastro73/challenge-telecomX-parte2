# Predicción de Churn de Clientes - Challenge Telecom X (Parte 2)

Este repositorio contiene la segunda fase del proyecto de Ciencia de Datos para "Telecom X", centrada en la **construcción y evaluación de modelos de Machine Learning** para predecir la cancelación de clientes (*churn*). Este trabajo se basa en el conjunto de datos previamente limpiado y analizado en la Parte 1 del desafío.

## 🎯 Objetivo del Proyecto

El objetivo principal de esta fase fue desarrollar un modelo predictivo robusto capaz de **identificar con precisión a los clientes que tienen una alta probabilidad de cancelar su servicio**. El proyecto busca traducir los resultados del modelo en insights accionables y recomendaciones estratégicas para el negocio.

## 🚀 Metodología de Modelado

El proyecto siguió un pipeline de Machine Learning estructurado en las siguientes etapas:

1.  **Preparación de Datos para el Modelado:**
    *   **Carga de Datos:** Se cargó el conjunto de datos limpio de la fase anterior.
    *   **Selección de Características:** Se eliminaron columnas irrelevantes que no aportan valor predictivo (ej. `customerID`, variables redundantes).
    *   **Codificación (Encoding):** Se transformaron las variables categóricas (ej. `Contract`, `PaymentMethod`) a un formato numérico utilizando **One-Hot Encoding** para que fueran compatibles con los algoritmos.
    *   **Análisis de Desbalance:** Se verificó la proporción de la variable objetivo (`Churn`), confirmando un desbalance de clases (74.28% No Churn, 25.71% Sí Churn).

2.  **Análisis de Correlación y Variables Clave:**
    *   Se generó una **matriz de correlación** para identificar las relaciones lineales entre las características y la cancelación.
    *   Se realizaron **análisis dirigidos** con visualizaciones (boxplots y countplots) para profundizar en el impacto de las variables más importantes como `tenure`, `Contract` y `Charges.Monthly`.

3.  **Construcción y Entrenamiento de Modelos:**
    *   **División de Datos:** El conjunto de datos se dividió en 70% para entrenamiento y 30% para prueba, utilizando estratificación para mantener la consistencia en la distribución del churn.
    *   **Modelo A (Regresión Logística):** Se implementó dentro de un `Pipeline` que aplica **balanceo de clases (SMOTE)** y **normalización (MinMaxScaler)**, pasos necesarios para este tipo de algoritmo.
    *   **Modelo B (Random Forest):** Se entrenó un modelo basado en árboles, que no requiere normalización de datos.

4.  **Evaluación e Interpretación:**
    *   **Métricas de Rendimiento:** Los modelos se evaluaron en el conjunto de prueba utilizando **Accuracy, Precision, Recall, F1-Score** y la **Matriz de Confusión**.
    *   **Análisis de Overfitting:** Se comparó el rendimiento en los datos de entrenamiento y prueba para asegurar la capacidad de generalización de los modelos.
    *   **Importancia de las Características:** Se utilizó la métrica `feature_importances_` del Random Forest para cuantificar la relevancia de cada variable en la predicción.

## 🛠️ Tecnologías Utilizadas

*   **Lenguaje:** Python
*   **Bibliotecas de Machine Learning:**
    *   **Pandas & NumPy:** Manipulación de datos.
    *   **Scikit-learn:** Para la división de datos, preprocesamiento, construcción de modelos y métricas de evaluación.
    *   **Matplotlib & Seaborn:** Para la visualización de resultados (matrices de confusión, importancia de características, etc.).
*   **Entorno de Desarrollo:** Google Colaboratory.

## 🏆 Modelo Seleccionado y Rendimiento

Tras una evaluación comparativa, el modelo de **Regresión Logística** fue seleccionado como la solución más efectiva para este problema de negocio.

*   **Rendimiento Clave:** El modelo alcanzó un **Recall del 65%** para la clase "Sí Churn".
*   **Justificación:** A pesar de que el Random Forest obtuvo una precisión general ligeramente superior, el modelo de Regresión Logística es mucho más efectivo para la tarea crítica de **identificar a la mayoría de los clientes que están en riesgo de cancelar**. Además, demostró ser un modelo robusto y estable, sin signos de sobreajuste.

## 📊 Hallazgos y Recomendaciones Estratégicas

El modelo predictivo y el análisis de importancia de características confirmaron de manera concluyente los siguientes factores como los principales impulsores del churn:

1.  **Antigüedad (`tenure`) y Tipo de Contrato:** Son los predictores más fuertes. El riesgo es máximo para clientes con contrato **mes a mes** y **baja antigüedad**.
2.  **Costo del Servicio (`Charges.Monthly`):** Clientes con facturas mensuales elevadas son más propensos a cancelar.

**Recomendaciones para Reducir el Churn:**

*   **Fomentar el Compromiso a Largo Plazo:** Crear campañas para migrar a los clientes de "mes a mes" a planes anuales con incentivos.
*   **Fortalecer la Experiencia del Cliente Nuevo:** Implementar un programa de "onboarding" y seguimiento durante el primer año.
*   **Crear un Sistema de Alertas Proactivas:** Utilizar el modelo para identificar clientes con un alto score de probabilidad de churn y permitir que el equipo de retención actúe de manera preventiva.

## ✒️ Autor

*   **Jimena Mariel Castro Ramírez**
*   **GitHub:** [jimenaCastro73](https://github.com/jimenaCastro73)
