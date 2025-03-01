# 🧹 Calidad de Datos
## Descripción
Este informe analiza la calidad de los datos utilizados en el entrenamiento del modelo YOLOv11, los problemas encontrados y las estrategias aplicadas para mejorar su precisión.
- 🔹 Inconsistencias en las etiquetas: Algunas imágenes tenían etiquetas de clase erroneas, es decir, la clase 2 o 3 cuando solo deberían existir 0 y 1.
- 🔹 El dataset contiene mas imágenes de un tipo de clase, es decir, más imágenes de casco que de sin casco, lo que puede afectar el rendimiento del modelo.
- 🔹 Iluminación y ángulos con poca variacion, lo que puede limitar la capacidad del modelo de detectar en entornos reales.

## 📌 Métodos Utilizados para Mejorar la Calidad del Dataset
✅ 1. Eliminación de datos corruptos o incompletos
- 🔹 Antes de entrenar el modelo, se verificaron que las imagenes existieran, se pudiera acceder a ellos y que las etiquetas tenian el formato adecuado.
- 🔹 Se revisaron y corrigieron etiquetas donde las clases no eran válidas.
