# 🔧 Código Fuente del Proyecto
## Descripción
Esta carpeta contiene el código fuente del proyecto, incluyendo scripts de preprocesamiento, modelado y despliegue.

# 📌 **Código para Entrenamiento y Evaluación del Modelo YOLOv11**

Este script descarga y prepara los datos, entrena el modelo YOLOv11 y evalúa su desempeño.

---

## 🔹 **1. Instalación de Dependencias**
```python
!pip install gdown torch ultralytics

🔹 2. Importar Librerías
python
Copy
Edit
import gdown
import os
import torch
import yaml
import numpy as np
import shutil
import matplotlib.pyplot as plt
import seaborn as sns
from ultralytics import YOLO
from IPython.display import display
from PIL import Image
from sklearn.metrics import roc_curve, auc
🔹 3. Descarga y Preparación de Datos
python
Copy
Edit
file_id = "1lMC00LhK1HMoERpySn5BR5V0U9jLl-hf"
output_path = "/content/datasets.zip"

# Descargar dataset
gdown.download(f"https://drive.google.com/uc?id={file_id}", output_path, quiet=False)

# Verificar y descomprimir
if os.path.exists(output_path) and os.path.getsize(output_path) > 1000:
    print("✅ Archivo descargado con éxito. Procediendo a descomprimir...")
    !unzip -q "/content/datasets.zip" -d "/content/datasets"
else:
    print("❌ Error en la descarga. Verifica el enlace.")
🔹 4. Validación de Etiquetas
python
Copy
Edit
label_paths = ["/content/datasets/datasets/labels/train", "/content/datasets/datasets/labels/val"]

for path in label_paths:
    for file in os.listdir(path):
        if file.endswith(".txt"):
            file_path = os.path.join(path, file)
            with open(file_path, "r") as f:
                lines = f.readlines()
            new_lines = ["1 " + " ".join(line.split()[1:]) + "\n" if int(line.split()[0]) > 1 else line for line in lines]
            with open(file_path, "w") as f:
                f.writelines(new_lines)
print("✅ Todas las etiquetas inválidas han sido corregidas.")
🔹 5. Creación del Archivo data.yaml
python
Copy
Edit
data = {
    'path': './datasets',
    'train': 'images/train',
    'val': 'images/val',
    'nc': 2,
    'names': ['sin_casco', 'casco']
}
with open('/content/datasets/datasets/data.yaml', 'w') as file:
    yaml.dump(data, file, default_flow_style=False, sort_keys=False)
🔹 6. Entrenamiento del Modelo YOLOv11
python
Copy
Edit
model = YOLO("yolo11n.pt")
results = model.train(
    data="/content/datasets/datasets/data.yaml",
    epochs=90,
    imgsz=640,
    plots=True,
    batch=64,
    lr0=0.0005,
    optimizer="AdamW",
    patience=15
)
🔹 7. Evaluación del Modelo
python
Copy
Edit
model_afinado = YOLO('/content/runs/detect/train/weights/best.pt')
evaluation = model_afinado.val()
🔹 8. Mostrar Imagen de Entrenamiento
python
Copy
Edit
image_path = "/content/runs/detect/train/train_batch0.jpg"
display(Image.open(image_path))
🔹 9. Obtener Métricas Clave
python
Copy
Edit
def print_metrics(evaluation):
    print("📊 Resultados de evaluación:")
    print(f"🔹 mAP (IoU@0.5): {evaluation.box.maps[0]:.4f}")
    print(f"🔹 mAP (IoU@0.5:0.95): {evaluation.box.maps[1]:.4f}")
    print(f"🔹 Precisión: {evaluation.box.p.mean():.4f}")
    print(f"🔹 Recall: {evaluation.box.r.mean():.4f}")
    print(f"🔹 F1-score: {evaluation.box.f1.mean():.4f}")

print_metrics(evaluation)
🔹 10. Generación de Predicciones
python
Copy
Edit
preds = model_afinado('/content/datasets/datasets/images/test', conf=0.3)
🔹 11. Mostrar Ejemplo de Predicción
python
Copy
Edit
preds[11].show()
🔹 12. Graficar Matriz de Confusión
python
Copy
Edit
conf_matrix = evaluation.confusion_matrix.matrix
plt.figure(figsize=(6, 4))
sns.heatmap(conf_matrix, annot=True, fmt=".0f", cmap="Blues", xticklabels=["Sin Casco", "Casco"], yticklabels=["Sin Casco", "Casco"])
plt.xlabel("Predicción")
plt.ylabel("Real")
plt.title("Matriz de Confusión")
plt.show()
🔹 13. Calcular y Graficar Curva ROC
python
Copy
Edit
y_true, y_scores = [], []
for pred in preds:
    for box in pred.boxes:
        y_true.append(int(box.cls.item()))
        y_scores.append(float(box.conf.item()))

y_true = np.array(y_true)
y_scores = np.array(y_scores)

if len(y_true) > 0 and len(y_scores) > 0:
    fpr, tpr, _ = roc_curve(y_true, y_scores, pos_label=1)
    roc_auc = auc(fpr, tpr)
    plt.figure(figsize=(6, 5))
    plt.plot(fpr, tpr, color='blue', lw=2, label=f'Área bajo la curva (AUC) = {roc_auc:.2f}')
    plt.plot([0, 1], [0, 1], color='gray', linestyle='--')
    plt.xlabel("Tasa de Falsos Positivos (FPR)")
    plt.ylabel("Tasa de Verdaderos Positivos (TPR)")
    plt.title("Curva ROC - Evaluación YOLOv11")
    plt.legend(loc="lower right")
    plt.show()
else:
    print("⚠️ No se pudo generar la curva ROC debido a valores incorrectos.")
🔹 14. Comprimir y Descargar Resultados
python
Copy
Edit
shutil.make_archive("/content/runs", "zip", "/content/runs")
from google.colab import files
files.download("/content/runs.zip")
