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
| **OSEMN** | Se basa en cinco fases: Obtener, Scrub (limpiar), Explorar, Modelar y iNterpretar. | Práctica, sencilla y bien adaptada a proyectos de análisis de datos. | Puede carecer de un enfoque específico en despliegue y mantenimiento. |


### Justificación Basada en la Naturaleza del Proyecto

Tras la evaluación de estas opciones, se determinó que OSEMN es la metodología más adecuada para la ejecución del proyecto, ya que proporciona un enfoque práctico y orientado al análisis de datos. Entre sus principales ventajas se destacan:

- **Estructura clara y enfocada en datos**: OSEMN permite seguir un flujo lógico desde la obtención de datos hasta su interpretación, facilitando la organización del trabajo.
- **Adecuado para visión por computadora**: La fase de limpieza y exploración de datos es crucial para proyectos de deep learning, asegurando datos de alta calidad antes del modelado.
- **Iteración y mejora continua**: Permite refinar el modelo mediante análisis y ajustes progresivos.
- **Flexibilidad y compatibilidad con tecnologías avanzadas**: Se adapta bien al uso de herramientas como YOLO v11, optimizando la gestión del flujo de trabajo en la detección de objetos.

La aplicación de OSEMN garantizará un desarrollo estructurado y eficiente del modelo de detección, maximizando la calidad de los resultados obtenidos.

### Cronograma de trabajo
 ![](https://drive.google.com/uc?export=view&id=1sYjFE7jnxTS8x-xafkRviiQBGHDkv0hc)

Para ver en tiempo real: 

[![Notion](https://img.shields.io/badge/Notion-Cronograma-blue?logo=notion)](https://statuesque-stay-3a5.notion.site/Cronograma-de-Trabajo-19aa98e9a80580daa2e9d243a09fdbe9)

### Metodología (OSMN)
 ![](https://drive.google.com/uc?export=view&id=1S_SqL5EHEZ05_y5nGsyNKLaPq4AAnuX5)

### Análisis de riesgos

| **ID** | **Riesgo** | **Probabilidad** | **Impacto** | **Estrategia de Mitigación** |
|--------|------------|-----------------|------------|--------------------------|
| R1 | Imágenes insuficientes o de mala calidad | Alta | Alta | Capturar datos adicionales en diferentes condiciones y aplicar técnicas de aumento de datos. |
| R2 | Desequilibrio en el dataset (más imágenes con casco que sin casco) | Media | Alta | Aplicar técnicas de balanceo de clases como sobremuestreo o generación de datos sintéticos. |
| R3 | Baja precisión del modelo en condiciones de poca luz o ángulos inusuales | Media | Alta | Entrenar con imágenes variadas y mejorar el preprocesamiento con técnicas de normalización. |
| R4 | Alto tiempo de inferencia en dispositivos de baja potencia | Media | Media | Optimizar el modelo con técnicas de cuantización y reducir tamaño de red. |
| R5 | Detección errónea en entornos con objetos similares a cascos | Alta | Media | Refinar etiquetas del dataset y mejorar el postprocesamiento del modelo. |

### 📊 Análisis de datos y Resultados

Después de realizar el entrenamiento y validación del modelo, pudimos obtener los siguientes resultados: 

| Métrica            | Valor   |
|--------------------|--------:|
| **Precisión**     | 0.9363  |
| **Recall**        | 0.9155  |
| **F1-score**      | 0.9255  |
| **mAP (IoU@0.5)** | 0.6611  |
| **mAP (IoU@0.5:0.95)** | 0.6547 |

- **Precisión:** Un 93.63% de los casos clasificados como positivos realmente pertenecen a la clase correcta.
- **Recall:** (Sensibilidad) un 91.55% de las instancias reales positivas fueron correctamente identificadas.
- **F1-score:** F1-score de 92.55% indica un buen equilibrio entre precisión y recall.
- **mAP (Mean Average Precision)**: mAP de ~65% indica que hay margen de mejora en la detección y localización de objetos.

### 📊 Conclusiones y Recomendaciones
El modelo propuesto demuestra su utilidad en la detección automatizada de empleados sin casco, lo que se traduce en un avance para la seguridad laboral y prevención de accidentes. Los resultados obtenidos, con una F1-score por encima del 90%, validan el enfoque adoptado.
No obstante, es importante mencionar ciertas áreas de oportunidad:
•	Ampliación del Dataset: Recoger más imágenes y situaciones distintas (entornos nocturnos, diferentes tipos de casco, industrias variadas) para robustecer la red.
•	Optimización del Modelo: Evaluar la implementación de versiones más ligeras de YOLO o aplicar técnicas como pruning y cuantización, especialmente para la ejecución en dispositivos de bajo rendimiento.
•	Refinamiento en el Postprocesamiento: Explorar algoritmos avanzados de filtrado para reducir falsos positivos, particularmente en entornos llenos de objetos similares al casco.
En conjunto, este proyecto sienta bases sólidas para futuros desarrollos en la intersección de la seguridad industrial y la ciencia de datos. Con la integración de analíticas más complejas y la posibilidad de desplegar el modelo en sistemas de videovigilancia en tiempo real, se abre la puerta a soluciones escalables que contribuyan al bienestar de los trabajadores y a la prevención de riesgos en el entorno laboral.

