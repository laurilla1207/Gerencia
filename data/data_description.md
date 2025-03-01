# 📊 Datos en el Proyecto
## Descripción
Este documento explica qué tipo de datos se pueden manejar dentro del proyecto y su estructura esperada.
### Tipos de Datos Utilizados:
- **Datos procesados:** Las imágenes que han sido previamente estandarizadas, con el tamaño adecuado (640x640 píxeles) y en formato compatible (.jpg o .png).
- **Datos enriquecidos:** Cada imagen cuenta con un archivo .txt con coordenadas de los objetos detectados en formato YOLO.
- **Datos de validación:** Las imágenes y etiquetas están organizadas en tres subconjuntos y se usaron métricas como precisión, recall, F1-score y mAP para analizar el desempeño del modelo en la detección de cascos
  
- 📁 datasets/
- │── 📂 train/        # Imágenes y etiquetas para entrenamiento
- │    ├── images/
- │    ├── labels/
- │
- │── 📂 val/         # Imágenes y etiquetas para validación
- │    ├── images/
- │    ├── labels/
- │
- │── 📂 test/        # Imágenes y etiquetas para prueba
- │    ├── images/
- │    ├── labels/

### Formatos Utilizados:
- JPG(Imagenes)
- Txt(Etiquetas en formato YOL0).
- YAML(Archivo que define la estructura del dataset)
- PT(best.pt) Modelo Yolo Entrenado
