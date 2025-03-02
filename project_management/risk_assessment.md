# ⚠️ Evaluación de Riesgos
## Descripción
En este documento se identifican los posibles riesgos que podrían afectar el éxito del proyecto.


### Análisis de riesgos

| **ID** | **Riesgo** | **Probabilidad** | **Impacto** | **Estrategia de Mitigación** |
|--------|------------|-----------------|------------|--------------------------|
| R1 | Imágenes insuficientes o de mala calidad | Alta | Alta | Capturar datos adicionales en diferentes condiciones y aplicar técnicas de aumento de datos. |
| R2 | Desequilibrio en el dataset (más imágenes con casco que sin casco) | Media | Alta | Aplicar técnicas de balanceo de clases como sobremuestreo o generación de datos sintéticos. |
| R3 | Baja precisión del modelo en condiciones de poca luz o ángulos inusuales | Media | Alta | Entrenar con imágenes variadas y mejorar el preprocesamiento con técnicas de normalización. |
| R4 | Alto tiempo de inferencia en dispositivos de baja potencia | Media | Media | Optimizar el modelo con técnicas de cuantización y reducir tamaño de red. |
| R5 | Detección errónea en entornos con objetos similares a cascos | Alta | Media | Refinar etiquetas del dataset y mejorar el postprocesamiento del modelo. |
