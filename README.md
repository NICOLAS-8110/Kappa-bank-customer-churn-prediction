<img width="1280" height="640" alt="WhatsApp Image 2026-11-17 at 3 00 46 PM (9)" src="https://github.com/user-attachments/assets/97b80bec-383c-478e-b11e-dd4b27546fd8" />


# 🏦 Κ Proyecto Kappa | Predicción de Abandono de Clientes en Beta Bank

## 📋 Descripción
**Beta Bank** identificó un problema de negocio relevante: cada mes una parte de sus clientes abandona la entidad financiera. Debido a que retener clientes existentes suele ser más rentable que captar nuevos usuarios, el banco busca desarrollar un sistema capaz de anticipar qué clientes presentan riesgo de abandono.

En este proyecto se construyeron y evaluaron modelos de Machine Learning para predecir la cancelación de clientes utilizando información demográfica, financiera y de comportamiento bancario. El objetivo principal fue maximizar el valor de la métrica **F1 Score** y desarrollar un modelo robusto capaz de identificar correctamente a los clientes con mayor probabilidad de abandonar el banco.

## 🎯 Objetivos
- ✅ Analizar la calidad, estructura e integridad del conjunto de datos.
- ✅ Preparar y transformar las variables para el entrenamiento de modelos predictivos.
- ✅ Estudiar el desequilibrio de clases de la variable objetivo.
- ✅ Entrenar distintos algoritmos de clasificación (Regresión Logística, Árbol de Decisión y Random Forest).
- ✅ Comparar el desempeño utilizando las métricas **F1 Score** y **ROC-AUC**.
- ✅ Aplicar técnicas de balanceo de clases (Sobremuestreo y Submuestreo).
- ✅ Optimizar hiperparámetros para maximizar el rendimiento.
- ✅ Seleccionar el modelo más robusto.
- ✅ Evaluar el modelo final sobre un conjunto de prueba independiente ($\text{F1} \ge 0.59$).

## 🛠️ Herramientas y Habilidades Utilizadas
* **Lenguaje:** Python
* **Librerías:** Pandas, NumPy, Scikit-Learn y Matplotlib
* **Entorno:** Jupyter Notebook
* **Técnicas:** Clasificación supervisada, Codificación One-Hot, Escalado (`StandardScaler`), Tratamiento de clases desbalanceadas (Oversampling/Undersampling) y Optimización de hiperparámetros.

## 📊 Fuente de Datos y Variables
El proyecto utiliza un dataset histórico con información de 10,000 clientes:
* **Archivo utilizado:** `Churn.csv`
* **Información del cliente:** `CustomerId`, `Surname`, `Age`, `Gender`, `Geography`.
* **Información financiera:** `CreditScore`, `Balance`, `EstimatedSalary`.
* **Relación con el banco:** `Tenure`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`.
* **Variable objetivo:** `Exited` (`1 = El cliente abandonó el banco`, `0 = El cliente permanece`).

## ⚙️ Metodología
1. **Limpieza de datos:** Se identificaron valores ausentes en la variable `Tenure` (reemplazados por la mediana, equivalente a ~5 años) y se eliminaron columnas sin valor predictivo (`CustomerId`, `RowNumber`, `Surname`).
2. **Análisis de desequilibrio:** Se detectó una fuerte asimetría en la variable objetivo (~79.6% clase 0 vs. ~20.4% clase 1).
3. **Transformación:** Aplicación de *One-Hot Encoding* (`drop_first=True`) en variables categóricas y `StandardScaler` en variables numéricas.
4. **Partición de datos:** División estructurada en **60% Entrenamiento, 20% Validación y 20% Prueba**.
5. **Modelado y balanceo:** Entrenamiento comparativo evaluando múltiples arquitecturas y aplicando técnicas de sobremuestreo (*oversampling*) para corregir el desequilibrio.

## 💡 Modelos Evaluados y Comparativa
| Modelo | Puntuación F1 (Validación) | ROC-AUC |
| :--- | :--- | :--- |
| **Regresión Logística** | 0.331 | 0.759 |
| **Árbol de Decisión** (`max_depth = 6`) | 0.570 | 0.684 |
| **Bosque Aleatorio** (`max_depth = 15`, `n_estimators = 300`) | 0.589 | 0.844 |
| **Bosque Aleatorio + Sobremuestreo** (Modelo Final) | **0.613** | **0.843** |
| **Bosque Aleatorio + Submuestreo** | 0.582 | 0.846 |

## 🧪 Evaluación Final (Conjunto de Prueba)
El modelo seleccionado (**Random Forest con Oversampling**) fue evaluado sobre datos totalmente independientes no vistos durante el entrenamiento:
* **F1 Score:** `0.601`
* **ROC-AUC:** `0.855`

*Este resultado supera exitosamente el requisito mínimo establecido para el proyecto ($\text{F1} \ge 0.59$), demostrando una excelente capacidad para distinguir entre clientes activos y en riesgo de fuga.*

## 📈 Visualizaciones Desarrolladas
* Distribución de clases de la variable objetivo y análisis del desequilibrio.
* Curvas ROC comparativas para Regresión Logística, Árbol de Decisión, Bosque Aleatorio y estrategias de balanceo.

## 📂 Archivos Principales
* `kappa_bank_customer_churn_prediction.ipynb` (o `Κ_Proyecto_Kappa___Predicción_de_Abandono_de_Clientes_en_Beta_Bank.ipynb`)
* `Churn.csv`

## 🏁 Conclusión
El desarrollo de este proyecto permitió a Beta Bank contar con una herramienta predictiva altamente confiable para anticipar la cancelación de clientes. La experimentación demostró que el tratamiento del desequilibrio de clases mediante técnicas de sobremuestreo fue determinante para potenciar la detección de la clase minoritaria sin sacrificar la capacidad de discriminación global. El modelo final (**Random Forest con Oversampling**), al alcanzar un **F1 Score de 0.601** y un **ROC-AUC de 0.855** en prueba, proporciona al banco una base sólida para implementar campañas de retención proactivas y mitigar la pérdida de ingresos.
