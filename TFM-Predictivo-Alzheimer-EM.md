# Modelado Predictivo en Alzheimer y Esclerosis Múltiple mediante Deep Learning

Este repositorio contiene la implementación y el análisis de un modelo de aprendizaje profundo diseñado para predecir la evolución de enfermedades neurodegenerativas (Alzheimer y Esclerosis Múltiple) utilizando datos clínicos longitudinales. El proyecto se centra en la precisión predictiva y, fundamentalmente, en la interpretabilidad de las decisiones del modelo (XAI) para su potencial aplicación clínica.

## Equipo Investigador
*   **Daniel López Montero**
*   **Aleix Martí i Moral**
*   **Pau Chamarro López**

*Trabajo desarrollado en el contexto del Máster Universitario en Inteligencia Artificial.*

## Arquitectura y Metodología

El núcleo del sistema está construido sobre **PyTorch** y utiliza una arquitectura de **Red Neuronal Recurrente (RNN) monocapa** optimizada para capturar la dependencia temporal de los historiales médicos de los pacientes.

### Detalles Técnicos y Experimentación
*   **Arquitectura:** RNN monocapa.
*   **Inicialización de Pesos:** Durante la visualización y ajuste de hiperparámetros, el análisis de convergencia demostró que la inicialización de **He** presenta muchas más fluctuaciones en este entorno específico, lo cual influyó en la configuración final de los pesos.
*   **Métrica de Evaluación:** El rendimiento del modelo se evalúa principalmente utilizando el Error Absoluto Medio (**MAE**).

### Prevención de *Data Leakage*
El manejo de datos longitudinales en medicina requiere un control estricto para evitar la fuga de datos entre los conjuntos de entrenamiento y prueba. Para garantizar que los registros de un mismo paciente no aparezcan en ambos subconjuntos simultáneamente, el pipeline de entrenamiento implementa una validación cruzada estricta utilizando **`GroupKFold`**.

## Interpretabilidad (Explainable AI - XAI)

Para evitar el efecto de "caja negra" y proporcionar herramientas útiles a los profesionales médicos, el modelo integra técnicas de atribución de características.
*   **Integrated Gradients:** Se emplea este método para cuantificar y trazar el impacto de cada variable de entrada (biomarcadores, datos demográficos, etc.) sobre la predicción final de la red neuronal.

## Seguimiento y Visualización del Proyecto

En el directorio `/scripts` se incluyen herramientas de visualización desarrolladas con **Matplotlib**. Estas utilidades no solo sirven para la representación de los datos clínicos, sino que el repositorio incluye scripts específicos diseñados para generar gráficas de seguimiento que ilustran el desglose de intervenciones y la carga de trabajo de cada miembro del equipo durante el desarrollo del proyecto.
