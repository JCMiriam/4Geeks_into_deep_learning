# 🐶🐱 Clasificador de Perros y Gatos con Deep Learning

Este proyecto utiliza redes neuronales convolucionales (CNNs) para clasificar imágenes como **perro** o **gato**, incluyendo procesamiento de imágenes, múltiples arquitecturas de modelos y evaluación final.

> ⚠️ **Importante**  
> Este repositorio **no contiene** los datos originales ni el modelo entrenado. Sin embargo, puedes ver y ejecutar todo el flujo desde los notebooks incluidos, por ejemplo, abriéndolos en GitHub Codespaces con Jupyter Notebook.

---

## 📁 Estructura del proyecto
```bash
📦root/
├── src/
│ ├── process-files.ipynb # Preprocesamiento y generación de datos
│ ├── rna.ipynb # Modelo base (pobre rendimiento)
│ ├── model-optimization.ipynb # Primer modelo optimizado
│ ├── second-optimization.ipynb # Segundo modelo optimizado (más complejo)
│ ├── check-final-model.ipynb # Clasificación y validación manual del modelo elegido
│ └── conclusion.ipynb # Comparativa entre modelos
├── models/ # Modelos (no incluidos)
├── data/
│ ├── raw/ # Imágenes sin procesar (no incluidas)
│ └── processed/ # Estructura organizada para entrenamiento (no incluida)
└── README.md
```

---

## 🚀 Instrucciones básicas
Este proyecto se debe revisar en codespace, ya que no se encuentran subidos en el repositorio los datos ni el modelo, debido al tamaño de los mismos. Sin embargo, puedes revisar todos los notebooks para ver el proceso de preparación de datos, entrenamiento y optimización del modelo, y las diferentes métricas realizadas. Abre los notebooks con Jupyter o Codespaces y sigue el flujo desde el preprocesamiento hasta la validación final.

---

## 🔁 Flujo de trabajo
1. process-files.ipynb
- Visualización de imágenes de perros y gatos
- Clasificación en carpetas por clase
- Conversión a arrays de tamaño uniforme
- Generación de conjuntos train y test con aumentación

2. rna.ipynb – Modelo base
- CNN profunda sin ajustes finos
- Accuracy ≈ 50% → comportamiento de clasificador aleatorio

3. model-optimization.ipynb – Primer modelo optimizado
- Arquitectura más ligera (3 bloques de convolución)
- Aumentación, Dropout y Adam(1e-4)
- Accuracy final ≈ 83.8%, con buena generalización

4. second-optimization.ipynb – Segundo modelo optimizado
- Batch Normalization, Dropout, regularización L2
- Mejor rendimiento de entrenamiento, pero sobreajuste final

5. conclusion.ipynb
- Comparación de los tres modelos
- Modelo 2 (primer optimizado) es el más consistente

6. check-final-model.ipynb – Validación manual
- Carga del modelo final (optimized-model.keras)
- Selección aleatoria de 100 imágenes no etiquetadas
- Clasificación automática en dogs y cats
- Revisión manual de aciertos/errores

---

## 📊 Resultados de prueba final
| Clase  | Total | Correctos | Errores | Precisión (%) |
| ------ | ----- | --------- | ------- | ------------- |
| Gatos  | 49    | 45        | 4       | 91.8%         |
| Perros | 51    | 45        | 6       | 88.2%         |

> ⚠️ Este test es solo una muestra pequeña. Para resultados fiables, se necesitaría clasificar todo el set de prueba.

---

## ✅ Requisitos
- Python ≥ 3.8
- TensorFlow ≥ 2.11
- Pillow
- matplotlib
- numpy
- Jupyter Notebook

---

## 📌 Notas
- Las imágenes originales para el entrenamiento del modelo son las pertenecientes a la competición de Kaggle [Dogs vs. Cats](https://www.kaggle.com/c/dogs-vs-cats/data). Deben colocarse en `data/raw/train` y `data/raw/test`
- Los modelos se entrenan desde cero y se guardan en la carpeta `models/`
- Los resultados pueden variar ligeramente según la ejecución y el entorno