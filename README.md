# Foro PLN — Preprocesamiento para clasificar reseñas de hoteles en español

Baseline TF-IDF + regresión logística sobre *Andalusian Hotels' Reviews* (Kaggle, CC BY-NC 4.0).
El foco es documentar y justificar decisiones de preprocesamiento, no maximizar la métrica.

## Contenido
- `notebook.ipynb`: análisis completo en 7 tramos (reproducibilidad, auditoría, Unicode, emojis/números, stopwords y morfología, tokenización, baseline y sesgos).
- `post.txt`: borrador del post del foro, en texto plano.
- `AI_USAGE.md`: qué se hizo con IA y qué debe verificar el estudiante.
- `requirements.txt`: versiones fijadas del entorno.
- `experiments.jsonl`: registro de experimentos (semilla, hiperparámetros, métricas, hash de los datos).

## Datos
No se redistribuyen. Descarga `Balanced_AHR.csv` de
[Kaggle](https://www.kaggle.com/datasets/chizhikchi/andalusian-hotels-reviews-unbalanced)
y colócalo en `data/` (en la raíz del proyecto). Hash SHA-256 esperado:
`6d3abc198db111d2a40d738a97070535d3afc02a7d16a7e55cbe637d610529be`.

## Reproducir
Desde la raíz del proyecto (Python 3.14 probado; se espera 3.11+):

```bash
python -m venv .venv
.venv\Scripts\python.exe -m pip install -r assignments/foro-preprocesamiento/requirements.txt
.venv\Scripts\python.exe -m jupyter lab
```

Abre `assignments/foro-preprocesamiento/notebook.ipynb` y ejecuta todas las celdas. Semilla: 42.

### En Google Colab
1. Sube `notebook.ipynb` a Colab.
2. Ejecuta la celda de la sección 0: instala `emoji`, `tokenizers`, `nltk`, `psutil` y el modelo `es_core_news_sm`,
   y te pide subir `Balanced_AHR.csv` (guárdalo en `/content`).
3. Ejecuta el resto en orden.

Probado en simulación local con Python 3.12, pandas 2.2.2, numpy 2.0.2 y scikit-learn 1.6.1: las métricas coinciden
con las de Python 3.14; solo cambian los tiempos. **No se probó en Colab real.** Los tiempos y la memoria dependerán del hardware.

## Licencias
- Dataset: CC BY-NC 4.0 (M. Chizhikova; incluye texto del corpus COAH, Molina-González et al., 2014).
- Modelo `es_core_news_sm` de spaCy: GPL-3.0.
