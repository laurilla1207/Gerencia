# 📜 Detección de Empleados sin Casco en Áreas de Trabajo

# Objetivo General
Desarrollar un modelo de reconocimiento de imágenes que identifique automaticamente empleados que no usan casco de seguridad en áreas de trabajo.
# Objetivos Específicos
- Recopilar y preprocesar un dataset de imágenes con empleados usando y sin usar casco.
- Entrenar un modelo de machine learning basado en YOLO v11.
- Evaluar la precisión y rendimiento del modelo en escenarios de prueba.

## Alcance
El proyecto abarcará el desarrollo de un modelo de reconocimiento de imágenes enfocado en detectar la ausencia de casco en empleados en entornos de trabajo donde su uso es obligatorio. Las principales características y limitaciones del proyecto incluyen:
La creación de un dataset con imágenes de empleados con y sin casco desde diferentes ángulos y condiciones de iluminación.
Preprocesamiento de las imágenes para mejorar la calidad del dataset incluyendo el redimensionamiento, anotación y balanceo de clases.
Entrenamiento de un modelo de deep learning basado en YOLO V11.
Evaluación del modelo mediante métricas como precisión recall y F1-score, para asegurar un rendimiento optimo.

## **Justificación de la Metodología**

### Comparación de Metodologías Aplicables

Para el desarrollo de este proyecto, se llevó a cabo una evaluación de distintas metodologías de ciencia de datos con el objetivo de seleccionar la más adecuada. A continuación, se presenta una comparación de las opciones más relevantes:

| Metodología  | Características principales | Ventajas | Limitaciones |
|-------------|-----------------------------|----------|--------------|
| **CRISP-DM** | Proceso estructurado en seis fases: comprensión del negocio, comprensión de los datos, preparación de los datos, modelado, evaluación y despliegue. | Flexible, iterativa y ampliamente utilizada en la industria. | Puede ser generalista en algunos casos. |
| **KDD** | Enfocada en la extracción de conocimiento a partir de grandes volúmenes de datos. | Muy útil en análisis exploratorios. | No está optimizada específicamente para visión por computadora. |
| **TDSP** | Metodología de Microsoft diseñada para la implementación colaborativa en ciencia de datos. | Ideal para grandes equipos y entornos empresariales. | Requiere herramientas y ecosistemas de Azure. |

### Justificación Basada en la Naturaleza del Proyecto

Tras la evaluación de estas opciones, se determinó que **CRISP-DM** es la metodología más adecuada para la ejecución del proyecto, ya que proporciona un marco sólido y adaptable a sus necesidades. Entre sus principales ventajas se destacan:

- **Orden y claridad en cada fase:** Permite estructurar el desarrollo de manera eficiente, desde la recopilación de datos hasta la implementación del modelo de detección.
- **Apropiado para visión por computadora:** Dado que el proyecto se centra en la detección de objetos mediante deep learning, es fundamental contar con una metodología que contemple una fase robusta de **preprocesamiento de datos**.
- **Iteración y mejora continua:** CRISP-DM facilita un enfoque progresivo, permitiendo realizar ajustes y optimizar el modelo con base en los resultados obtenidos.
- **Integración con tecnologías avanzadas:** La metodología se alinea con el uso de **YOLO v11**, favoreciendo la organización del flujo de trabajo en el desarrollo del modelo.

### Cronograma de trabajo
 ![](https://drive.google.com/uc?export=view&id=1Ol7RH8Jm3Xs90ixwyDtzuTP0UGiBjZwH)

Para ver en tiempo real: 

[![Notion](https://img.shields.io/badge/Notion-Cronograma-blue?logo=notion)](https://statuesque-stay-3a5.notion.site/Cronograma-de-Trabajo-19aa98e9a80580daa2e9d243a09fdbe9)
