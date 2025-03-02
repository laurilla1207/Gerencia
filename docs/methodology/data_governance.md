# 📜 Gobernanza de Datos
## Descripción
A Continuacion se detalla el manejo de los datos en el proyecto para asegurar su calidad, organizacion y seguridad. 

### Normas y estándares aplicados.
- Usamos imágenes en formatos comunes (.jpg, .png) para evitar problemas de compatibilidad.
- Las etiquetas de los objetos se guardan en archivos .txt en formato YOLO, asegurando que el modelo las entienda bien.
- Uso del archivo data.yaml que le indica al modelo dónde encontrar los datos

### Privacidad y seguridad de datos.
- Solo las personas autorizadas pueden modificar el dataset.
- Los archivos se almacenaron en Google Drive en lugar de discos locales.
- Uso de repositorios privados en GitHub, así evitamos accesos no deseados.

### Control y auditoría de datos.
- Us des Git para rastrear cambios en los archivos y saber quién que usuario los modifico.
- Antes de entrenar el modelo se valida si hay archivos faltantes como imágenes o etiquetas.
