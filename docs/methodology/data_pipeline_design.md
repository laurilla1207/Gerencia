# 🔄 Diseño del Pipeline de Datos
## Descripción
Define la arquitectura y flujos de procesamiento de datos utilizados en el proyecto.
- ### Ingesta y transformación de datos:
- Las imagenes se obtuvieron desde la pagina web de Google Images y datasets públicos del sitio web https://public.roboflow.com/object-detection/hard-hat-workers.
- Las transformaciones realizadas fueron la eliminación de imágenes corruptas,redimensionamiento a 640x640 píxeles y corrección de etiquetas incorrectas.

- ### Almacenamiento y disponibilidad:
- Los documentos de este proyecto se almacenaron el el repositorio Github y en Google Drive.
- Google Colab se utilizo para el procesamiento de notebooks de entrenamiento.
  
- ### Plan de monitoreo del pipeline.
- El codigo fuente incluye un script de validacion de formato de etiquetado de imagenes.
- Se realiza la evaluacion del modelo validando que los valores de las metricas esten acordes al resultado de rendimiento esperado.
