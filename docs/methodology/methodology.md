# 📜 Justificación de la Metodología
## Descripción
Para lograr los objetivos propuestos, se optó por la metodología OSEMN, que facilita la gestión integral de proyectos de ciencia de datos con un enfoque práctico y flexible:

### 1.	Obtención de Datos: 
Se recopilaron imágenes de empleados en distintas situaciones, garantizando una muestra variada.
### 2.	Scrub (Limpieza de Datos): 
Se llevaron a cabo procesos de balanceo de clases, aumentación de datos y etiquetado manual para mejorar la calidad del conjunto.
### 3.	Exploración: 
A través de análisis estadísticos y visualizaciones, se identificaron patrones y posibles sesgos en el dataset.
### 4.	Modelado: 
Se entrenó un modelo basado en YOLO v11, ajustando hiperparámetros y configuraciones para maximizar el rendimiento.
### 5.	Interpretación: 
Se evaluaron los resultados aplicando diversas métricas de desempeño y, a partir de ellas, se introdujeron mejoras iterativas en el modelo.
Adicionalmente, se compararon brevemente otras metodologías como CRISP-DM, KDD y TDSP, para finalmente seleccionar OSEMN por su estructura amigable con proyectos de visión por computadora.

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
