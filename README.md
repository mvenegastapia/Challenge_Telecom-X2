# Proyecto End-to-End: Análisis y Predicción de Fuga de Clientes (Churn)

Este repositorio documenta un proyecto completo de ciencia de datos para analizar y predecir la fuga de clientes (churn) en una empresa de telecomunicaciones. El proyecto abarca desde la limpieza de datos y el análisis exploratorio (EDA) hasta la construcción, evaluación e interpretación de modelos de Machine Learning.

---

## 📝 Descripción del Proyecto

A partir de un conjunto de datos en formato JSON, se realiza un pipeline completo de ciencia de datos. La primera fase se centra en un **análisis exploratorio profundo** para entender las características y comportamientos de los clientes que abandonan la empresa. La segunda fase se enfoca en construir un **modelo predictivo** capaz de identificar con antelación a los clientes en riesgo de cancelación, permitiendo a la empresa tomar acciones proactivas.

---

## 🎯 Objetivos

1.  **Análisis Exploratorio:**
    * Identificar el perfil del cliente que cancela el servicio.
    * Descubrir los factores y servicios clave que influyen en la decisión de abandono.
2.  **Modelado Predictivo:**
    * Construir un modelo de Machine Learning robusto para predecir la probabilidad de churn de un cliente.
    * Evaluar el rendimiento del modelo con métricas de negocio relevantes (especialmente el `recall`).
    * Interpretar las decisiones del modelo para validar los hallazgos del análisis exploratorio.
3.  **Estrategia de Negocio:**
    * Generar un conjunto de recomendaciones accionables para la gerencia, con el fin de reducir la tasa de churn.

---

## 💻 Tecnologías Utilizadas

* **Análisis de Datos:** Pandas, NumPy
* **Visualización:** Plotly, Matplotlib, Seaborn
* **Machine Learning:** Scikit-learn
* **Interpretabilidad de Modelos:** SHAP
* **Entorno de Desarrollo:** Google Colab

---

## 🔬 Método de Análisis

El proyecto se dividió en dos fases metodológicas:

### Fase 1: Análisis Exploratorio de Datos (EDA)
* **Limpieza y Estandarización:** Se realizó una limpieza exhaustiva de los datos, incluyendo la corrección de tipos de datos, el manejo de valores nulos e inconsistentes, y la estandarización de categorías (ej. unificar `"No internet service"` a `"No"`).
* **Visualización Interactiva:** Se utilizaron gráficos de Plotly para explorar la relación entre cada variable y el `Churn`, calculando tasas de cancelación para cada segmento.
* **Análisis de Interacciones:** Se estudió la combinación de factores, como el tipo de contrato junto con el servicio de internet, y la relación entre la antigüedad y los cargos mensuales.

### Fase 2: Modelado Predictivo (Machine Learning)
* **Preprocesamiento:** Se transformaron todas las variables a un formato numérico mediante mapeo de variables binarias y One-Hot Encoding para las multi-categoría.
* **División y Escalado:** Los datos se dividieron en conjuntos de entrenamiento (80%) y prueba (20%), aplicando estratificación. Las características numéricas fueron escaladas con `StandardScaler`.
* **Entrenamiento:** Se entrenaron dos modelos de clasificación: **Regresión Logística** y **Random Forest**.
* **Evaluación:** Se evaluaron los modelos utilizando una matriz de confusión, reportes de clasificación (precision, recall, F1-score) y la métrica AUC. La **Regresión Logística** fue seleccionada como el mejor modelo debido a su mayor `recall` (0.52 vs 0.46) y AUC (0.84 vs 0.82).
* **Interpretación:** Se utilizaron los **coeficientes del modelo** y la librería **SHAP** para entender el impacto y la dirección de cada variable en las predicciones, confirmando los hallazgos del EDA.

---

## 💡 Hallazgos y Resultados del Modelo

El modelo de **Regresión Logística** demostró ser el más efectivo, alcanzando un **AUC de 0.84** y una capacidad para identificar correctamente al **52% de los clientes que realmente cancelaron (`recall`)**.

El análisis de importancia de características, tanto del EDA como de los modelos, reveló de forma consistente los siguientes factores como los más influyentes en el `Churn`:

1.  **`account_Contract`:** El contrato **mes a mes** es el predictor #1 de abandono.
2.  **`customer_tenure`:** La **baja antigüedad** es el segundo factor más importante.
3.  **`internet_InternetService`:** Tener **Fibra Óptica** aumenta significativamente la probabilidad de cancelación.
4.  **Cargos (`account_Charges...`):** Los cargos mensuales y totales son altamente relevantes.
5.  **`internet_TechSupport`:** La **ausencia de soporte técnico** es un factor clave, especialmente para clientes con Fibra Óptica.

---

## 🚀 Plan de Acción Estratégico

Basado en la evidencia recolectada, se proponen las siguientes acciones gerenciales:

1.  **Rediseñar la Oferta de Valor de Fibra Óptica:**
    * **Acción:** Crear paquetes de Fibra Óptica donde el **Soporte Técnico se incluya por defecto** durante el primer año.
    * **Objetivo:** Aumentar el valor percibido del servicio y reducir la frustración técnica inicial.

2.  **Fomentar la Lealtad a Largo Plazo:**
    * **Acción:** Lanzar una **campaña de migración** para incentivar a los clientes de `Month-to-month` a cambiarse a contratos anuales a cambio de un beneficio claro (ej. un mes gratis).
    * **Objetivo:** Aumentar la "fricción" de salida y estabilizar la base de clientes.

3.  **Implementar un Programa de "Blindaje" para Clientes Nuevos:**
    * **Acción:** Crear un **programa de *onboarding* proactivo de 90 días** para clientes nuevos, especialmente los de Fibra Óptica, con seguimiento y un canal de soporte prioritario.
    * **Objetivo:** Construir confianza y lealtad desde el primer día para superar la etapa de alta sensibilidad al precio.
