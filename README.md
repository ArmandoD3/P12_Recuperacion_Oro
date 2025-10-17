# 🏭 Predicción de la Recuperación de Oro de un Proceso Industrial
## 📝 Descripción del Proyecto
Este proyecto aborda un problema de regresión para optimizar los procesos de producción de la planta minera Zyfra. El objetivo es desarrollar un modelo de machine learning que prediga la cantidad de oro recuperado del mineral en dos etapas clave del proceso de flotación: la etapa rougher (flotación primaria) y la etapa final (limpieza).El éxito del modelo se mide por el sMAPE final ponderado, que otorga un 75% de importancia a la precisión de la predicción en la etapa final.
## Puntos clave: 
Análisis de datos para identificar anomalías (concentraciones de metales cercanas a cero).
Preprocesamiento de datos con manejo de valores nulos (usando ffill y bfill).
Modelado con el entrenamiento y evaluación de modelos de regresión lineal y de conjunto (árboles de decisión y bosques aleatorios).

# 🛠️ Tecnologías Usadas
Python: Lenguaje de programación principal.
Pandas: Manipulación y análisis de datos.
NumPy: Soporte para arrays y cálculos numéricos.
Scikit-learn: Implementación de modelos de machine learning (Regresión Lineal, Random Forest) y técnicas de validación (GridSearchCV).
Matplotlib/Seaborn: Visualización de datos para análisis exploratorio y comprobación de limpieza.
