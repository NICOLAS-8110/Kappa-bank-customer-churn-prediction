<img width="1280" height="640" alt="WhatsApp Image 2026-11-17 at 3 00 46 PM (9)" src="https://github.com/user-attachments/assets/97b80bec-383c-478e-b11e-dd4b27546fd8" />


# 🏦 Κ Proyecto Kappa | Predicción de Abandono de Clientes en Beta Bank

## 📋 Descripción
**Beta Bank** identificó un problema de negocio relevante: cada mes una parte de sus clientes abandona la entidad financiera. Debido a que retener clientes existentes suele ser más rentable que captar nuevos usuarios, el banco busca desarrollar un sistema capaz de anticipar qué clientes presentan riesgo de abandono.

En este proyecto se construyeron y evaluaron modelos de Machine Learning para predecir la cancelación de clientes utilizando información demográfica, financiera y de comportamiento bancario. El objetivo principal fue maximizar el valor de la métrica **F1 Score** y desarrollar un modelo capaz de identificar correctamente a los clientes con mayor probabilidad de abandonar el banco.

## 🎯 Objetivos
- ✅ Analizar la calidad y estructura del conjunto de datos.
- ✅ Preparar y transformar las variables para el entrenamiento de modelos predictivos.
- ✅ Estudiar el desequilibrio de clases de la variable objetivo.
- ✅ Entrenar distintos modelos de clasificación (Regresión Logística, Árbol de Decisión y Random Forest).
- ✅ Comparar el desempeño utilizando F1 Score y ROC-AUC.
- ✅ Aplicar técnicas de equilibrio de clases (como `class_weight='balanced'` y sobremuestreo).
- ✅ Optimizar hiperparámetros mediante bucles de validación para maximizar el desempeño.
- ✅ Seleccionar el modelo más robusto.
- ✅ Evaluar el modelo final sobre datos independientes de prueba ($\text{F1} \ge 0.59$).

## 🛠️ Herramientas y Habilidades Utilizadas
* **Lenguaje:** Python
* **Librerías:** Pandas, NumPy, Scikit-Learn y Matplotlib
* **Entorno:** Jupyter Notebook (`kappa_bank_customer_churn_prediction.ipynb`)
* **Técnicas:** Clasificación supervisada, Codificación One-Hot, Escalado de características, Tratamiento de clases desbalanceadas y Optimización de hiperparámetros.

## 📊 Fuente de Datos y Variables
El proyecto utiliza un dataset histórico con información de 10,000 clientes:
* **Archivo utilizado:** `Churn.csv`
* **Información del cliente:** `CustomerId`, `Surname`, `Age`, `Gender`, `Geography`.
* **Información financiera:** `CreditScore`, `Balance`, `EstimatedSalary`.
* **Relación con el banco:** `Tenure`, `NumOfProducts`, `HasCrCard`, `IsActiveMember`.
* **Variable objetivo:** `Exited` (`1 = El cliente abandonó el banco`, `0 = El cliente permanece`).

## ⚙️ Metodología
1. **Limpieza de datos:** Sustitución de valores ausentes en `Tenure` utilizando la mediana (~5 años) y eliminación de columnas sin valor predictivo (`CustomerId`, `RowNumber`, `Surname`).
2. **Transformación:** Aplicación de *One-Hot Encoding* (`drop_first=True`) y estandarización numérica con `StandardScaler`.
3. **División de los datos:** Partición estructurada en **60% Entrenamiento, 20% Validación y 20% Prueba**.
4. **Entrenamiento y optimización:** Evaluación comparativa de modelos baseline, pruebas con pesos de clases balanceados y optimización iterativa de hiperparámetros (`n_estimators` y `max_depth`).

## 💡 Modelos Evaluados y Comparativa
| Enfoque / Modelo | F1 Score (Validación) |
| :--- | :--- |
| **Árbol de Decisión** (Base) | 0.5036 |
| **Regresión Logística** (Base) | 0.0878 |
| **Bosque Aleatorio** (Base) | 0.5869 |
| **Árbol de Decisión** (`class_weight='balanced'`) | 0.5963 |
| **Regresión Logística** (`class_weight='balanced'`) | 0.4470 |
| **Bosque Aleatorio** (`class_weight='balanced'`) | **0.6235** *(Mejor combinación: n_estimators=100, max_depth=10)* |

## 🧪 Evaluación Final (Conjunto de Prueba)
El modelo óptimo seleccionado (**Random Forest con `class_weight='balanced'`**, `n_estimators=100`, `max_depth=10`) fue evaluado sobre el conjunto de prueba independiente:
* **F1 Score del modelo final:** `0.5973`
* **Métrica ROC-AUC:** `0.8548` (~0.86)

*Este resultado cumple y supera exitosamente el requisito mínimo establecido por el proyecto ($\text{F1} \ge 0.59$).*

## 📈 Visualizaciones y Análisis Desarrollados
* Análisis de distribución de la variable objetivo y detección de desequilibrio (~20.37% de abandonos frente a ~79.63% de permanencia).
* Evaluación mediante curvas de rendimiento y optimización de hiperparámetros.

## 📂 Archivos Principales
* `kappa_bank_customer_churn_prediction.ipynb`
* `Churn.csv`

## 🏁 Conclusión
El proyecto permitió desarrollar un modelo predictivo altamente confiable para anticipar la fuga de clientes en Beta Bank. A través de la preparación adecuada de los datos, la codificación de variables y la corrección del desequilibrio de clases mediante el ajuste de pesos (`class_weight='balanced'`), el modelo **Random Forest optimizado** logró un **F1 Score de 0.5973** y un **ROC-AUC de 0.86** en el conjunto de prueba, superando el umbral mínimo exigido. Esto proporciona a Beta Bank una herramienta sólida para implementar campañas de retención eficaces y mitigar la pérdida de clientes.
