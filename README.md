# ⚙️ Optimización del Proceso de Recuperación de Oro (Gold Recovery)

### 📈 Resultado Clave
| Métrica | Objetivo | Valor Final (Mejor Modelo) |
| :--- | :--- | :--- |
| **sMAPE Final** | Minimizar | **[Tu Valor Final aquí]** |

---

## 🎯 Descripción del Problema

El objetivo del proyecto es crear un **modelo de regresión** capaz de predecir la cantidad recuperada de concentrados de oro (Au) en las etapas de flotación primaria (*rougher*) y de purificación final.

La predicción precisa es vital para la optimización de los procesos de la planta metalúrgica, buscando maximizar la eficiencia de la recuperación de metales valiosos.

El desafío principal radica en manejar tres conjuntos de datos con diferentes características (entrenamiento, prueba y fuente completa) y trabajar con datos de series de tiempo donde la disponibilidad de características varía entre los conjuntos de entrenamiento y prueba.

---

## ✅ Solución Propuesta

Se implementó un pipeline integral de Data Science y Machine Learning que incluyó:

1.  **Limpieza y Preprocesamiento Intensivo** para manejar valores ausentes y anomalías en las concentraciones de metales (Au, Ag, Pb).
2.  **Validación de Datos** mediante el cálculo de la métrica de recuperación (*recovery*) de la etapa *rougher* y comparación con los datos proporcionados.
3.  **Evaluación de Modelos de Regresión** (p. ej., Regresión Lineal, Árboles de Decisión, Random Forest) utilizando **Validación Cruzada** (*Cross-Validation*) para asegurar la solidez.
4.  **Optimización bajo la Métrica sMAPE**, la cual fue implementada como una función personalizada.

---

## 📊 Resultados Principales

El mejor rendimiento se obtuvo con el modelo **[Tu Mejor Modelo: por ejemplo, RandomForestRegressor]** después de un riguroso preprocesamiento y ajuste.

### Métrica sMAPE Final

Se calcula el sMAPE final ponderado:
$$\text{sMAPE Final} = 0.25 \times \text{sMAPE Rougher} + 0.75 \times \text{sMAPE Final}$$

| Modelo | sMAPE Rougher | sMAPE Final | **sMAPE Ponderado Final** |
| :--- | :--- | :--- | :--- |
| **[Tu Mejor Modelo]** | [Valor] | [Valor] | **[Valor Final]** |
| Regresión Lineal (Base) | [Valor] | [Valor] | [Valor] |

### Hallazgos Clave del Análisis de Datos

* **Validación de Recuperación:** El cálculo propio de la recuperación de la etapa *rougher* mostró un EAM (Error Absoluto Medio) de **[Tu EAM aquí]**, confirmando que la fórmula de recuperación es correcta.
* **Concentración de Metales:** El análisis reveló que la concentración de **Oro (Au)** aumenta significativamente en cada etapa (materia prima → flotación → limpieza final), mientras que la de Plata (Ag) tiende a disminuir.
* **Detección de Anomalías:** Se identificaron y eliminaron valores atípicos (anomalías) en las concentraciones totales de las sustancias en las etapas *rougher* y *final*, ya que los valores de concentración cero introducen ruido o indican datos corruptos.

---

## 🛠️ Metodología

### 1. Preparación de Datos
* **Alineación de Conjuntos:** Se identificaron las características ausentes en el conjunto de prueba, eliminando las columnas objetivo (`*output.recovery`, `*output.tail`) del conjunto de entrenamiento para garantizar la alineación.
* **Manejo de Valores Ausentes (NaN):** Se aplicó el método **Forward Fill (`ffill`)** a los datos de entrenamiento y prueba por separado. Dado que los datos están indexados por tiempo y los valores cercanos en el tiempo son similares, `ffill` es la estrategia más adecuada.
* **Escalado:** Las características numéricas fueron escaladas (aunque no estrictamente necesario para modelos basados en árboles, es una buena práctica).

### 2. Función sMAPE Personalizada
Se implementó la función sMAPE (Symmetric Mean Absolute Percentage Error) y la función sMAPE final ponderada, tal como se requiere para la evaluación del proyecto.

$$\text{sMAPE} = \frac{1}{N} \sum_{i=1}^{N} \frac{|\hat{y}_i - y_i|}{(|\hat{y}_i| + |y_i|)/2} \times 100\%$$

### 3. Modelado y Evaluación
* Se utilizaron modelos de regresión, incluyendo **[Tu Modelo Base]** y **[Tu Mejor Modelo]**.
* Los modelos se entrenaron con las características disponibles en ambos conjuntos (entrenamiento y prueba).
* Se utilizó **Validación Cruzada (Cross-Validation)** con el *scorer* sMAPE personalizado para seleccionar el modelo y los hiperparámetros óptimos.

---

## 📂 Estructura del Proyecto

/ ├── datasets/ │ ├── gold_recovery_train.csv │ ├── gold_recovery_test.csv │ └── gold_recovery_full.csv ├── notebooks/ │ └── gold_recovery_modeling.ipynb # Notebook con el análisis y modelado completo ├── README.md # Documentación del proyecto └── src/ # (Opcional, si modularizaste el código) └── metrics.py # (Para la función sMAPE)

## 💻 Tecnologías Utilizadas

* **Lenguaje:** Python
* **Librerías Clave:**
    * **Pandas & NumPy:** Manipulación de datos y cálculos.
    * **Scikit-learn:** Modelado de regresión (`LinearRegression`, `RandomForestRegressor`, etc.), validación cruzada y preprocesamiento (`StandardScaler`).
    * **Matplotlib & Seaborn:** Visualizaciones para el análisis de concentraciones y distribución de partículas.
 
## 💡 Conclusiones y Aprendizajes

* **Importancia del Preprocesamiento:** El manejo adecuado de datos de series de tiempo (usando `ffill`) y la eliminación de anomalías de concentración fueron pasos esenciales, ya que una mala imputación o valores extremos arruinan la capacidad predictiva.
* **Impacto de la Métrica:** La métrica sMAPE, sensible a errores relativos, castiga fuertemente las predicciones inexactas cuando los valores reales son cercanos a cero. Esto obligó a elegir modelos robustos que manejen bien los valores pequeños.
* **Diseño de la Prueba Final:** El proceso de modelado requirió un cuidado especial al seleccionar características, ya que el conjunto de prueba es limitado. Este es un desafío común en escenarios industriales donde los datos de tiempo real no están disponibles inmediatamente.
