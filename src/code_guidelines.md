# 🔧 Código Fuente del Proyecto
## Descripción
Esta carpeta contiene el código fuente del proyecto elaborado en Python.

# 📌 **Código para Entrenamiento y Evaluación del Modelo YOLOv11**

Este script descarga y prepara los datos, entrena el modelo YOLOv11 y evalúa su desempeño.


```python
#Instalación de Dependencias
!pip install gdown torch ultralytics

#Importar Librerías
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

#Descarga y Preparación de Datos
file_id = "1lMC00LhK1HMoERpySn5BR5V0U9jLl-hf"
output_path = "/content/datasets.zip"

#Descargar dataset
gdown.download(f"https://drive.google.com/uc?id={file_id}", output_path, quiet=False)

#Verificar y descomprimir
if os.path.exists(output_path) and os.path.getsize(output_path) > 1000:
    print("✅ Archivo descargado con éxito. Procediendo a descomprimir...")
    !unzip -q "/content/datasets.zip" -d "/content/datasets"
else:
    print("❌ Error en la descarga. Verifica el enlace.")

#Validación de Etiquetas
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

#Creación del Archivo data.yaml
data = {
    'path': './datasets',
    'train': 'images/train',
    'val': 'images/val',
    'nc': 2,
    'names': ['sin_casco', 'casco']
}
with open('/content/datasets/datasets/data.yaml', 'w') as file:
    yaml.dump(data, file, default_flow_style=False, sort_keys=False)

#Entrenamiento del Modelo YOLOv11
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

#Evaluación del Modelo
model_afinado = YOLO('/content/runs/detect/train/weights/best.pt')
evaluation = model_afinado.val()

#Mostrar Imagen de Entrenamiento
image_path = "/content/runs/detect/train/train_batch0.jpg"
display(Image.open(image_path))

#Obtener Métricas Clave
def print_metrics(evaluation):
    print("📊 Resultados de evaluación:")
    print(f"🔹 mAP (IoU@0.5): {evaluation.box.maps[0]:.4f}")
    print(f"🔹 mAP (IoU@0.5:0.95): {evaluation.box.maps[1]:.4f}")
    print(f"🔹 Precisión: {evaluation.box.p.mean():.4f}")
    print(f"🔹 Recall: {evaluation.box.r.mean():.4f}")
    print(f"🔹 F1-score: {evaluation.box.f1.mean():.4f}")

print_metrics(evaluation)

#10. Generación de Predicciones
preds = model_afinado('/content/datasets/datasets/images/test', conf=0.3)

#11. Mostrar Ejemplo de Predicción
preds[11].show()

#Graficar Matriz de Confusión
conf_matrix = evaluation.confusion_matrix.matrix
plt.figure(figsize=(6, 4))
sns.heatmap(conf_matrix, annot=True, fmt=".0f", cmap="Blues", xticklabels=["Sin Casco", "Casco"], yticklabels=["Sin Casco", "Casco"])
plt.xlabel("Predicción")
plt.ylabel("Real")
plt.title("Matriz de Confusión")
plt.show()

#Calcular y Graficar Curva ROC
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
