# 🔎 **Evaluación del Modelo**

## 📌 Descripción  
En esta seccion se evalua como funcionó el modelo después del entrenamiento. También comparamos los resultados con otros enfoques y explicamos por qué elegimos este modelo.  

## 📊 **Resultados de Evaluación**  
Después de las pruebas, estos fueron las metricas calculadas:  

- **mAP@0.5:** **0.6902** → Qué tan bien detecta los objetos con un umbral de IoU del 50%.  
- **mAP@0.5:0.95:** **0.6725** → Similar al anterior, pero considerando umbrales más exigentes.  
- **Precisión:** **94.29%** → De todas las detecciones, este porcentaje fue correcto.  
- **Recall:** **92.56%** → De todos los objetos reales, el modelo encontró este porcentaje.  
- **F1-score:** **0.9341** → Un balance entre precisión y recall, indicando un buen desempeño general.  

## 📌 **¿Qué significan estas metricas para el modelo?**  
✅ **Buen equilibrio entre precisión y recall** → El modelo hace bien su trabajo sin ser demasiado estricto ni demasiado permisivo.  
✅ **F1-score sólido** → La relación entre errores y aciertos es bastante estable.  
✅ **El mAP es bueno, pero puede mejorar** → Aunque los valores son altos, hay margen para optimizar la detección en situaciones más difíciles.  

### ✅ **En resumen:**  
El modelo está funcionando bastante bien, pero con algunos ajustes podemos hacerlo aún más preciso y confiable. 🚀  
