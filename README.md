# Sentilytics: Clasificación de sentimiento y priorización de reseñas negativas en español

## Descripción del Proyecto
Sentilytics es un sistema de Procesamiento del Lenguaje Natural (PLN) diseñado para clasificar automáticamente reseñas de usuarios en español como positivas (1) o negativas (0). El objetivo operativo principal no es la proporción global de aciertos (*accuracy*), sino detectar la insatisfacción: enviar las quejas urgentes a una cola de revisión humana limitando la carga excesiva de falsas alarmas.

## Dataset
Se utilizó el dataset `mteb/SpanishSentimentClassification` obtenido desde Hugging Face, dividido internamente de forma estratificada en entrenamiento (720), validación (154) y test interno (155). 

* **Desbalance de clases:** 82.7% reseñas positivas y 17.3% negativas.
* El proyecto prioriza métricas orientadas a la clase minoritaria (negativa): **Recall negativo y F1 negativo**.

## Avances del Proyecto

* **APF1 (Baseline):** Implementación de una representación léxica (TF-IDF) + Regresión Logística con pesos balanceados (`class_weight="balanced"`).
* **APF2 (Contextual Congelado):** Generación de embeddings contextuales usando **Sentence-BERT** (`paraphrase-multilingual-MiniLM-L12-v2`) sobre el texto original + Regresión Logística.
* **APF3 (Pendiente - Proyecto Final):** Fine-tuning de un Transformer preentrenado en español (BETO) con cabeza de clasificación de dos salidas.

## Estructura del Repositorio

* `grupo1apf1.ipynb` : Notebook ejecutable del baseline (TF-IDF). Contiene la limpieza de datos, particiones inmutables y la selección del umbral de decisión operativo.
* `grupo1apf2.ipynb` : Notebook ejecutable de Sentence-BERT. Compara el rendimiento contextual frente al baseline sobre las mismas particiones.
* `grupo1_evaluacion_final.ipynb` : Notebook reservado para la auditoría y evaluación independiente final sobre el conjunto de test. *(Bloqueado hasta el cierre del APF3 para evitar fuga de datos).*
* `requirements.txt` : Archivo con las dependencias necesarias para ejecutar los entornos.

## Resultados Actuales (Fase de Validación)
Comparación de los modelos bajo el mismo criterio de negocio (maximizar recall negativo con precisión mínima de 0.60, fijando un umbral de decisión en P(Negativa) ≥ 0.48):

* **TF-IDF + LR:** Recall Negativo: 0.77 | F1 Negativo: 0.69
* **Sentence-BERT + LR:** Recall Negativo: 0.96 | F1 Negativo: 0.82

## Instalación y Requisitos
Para instalar las dependencias necesarias, ejecutar:
\`\`\`bash
pip install -r requirements.txt
\`\`\`

## Integrantes del Equipo

Angel Jesus Lopez Cardenas

Arnie Adriano Flores Jeampool

Jesus Francisco Ayquipa Ayquipa

Evers Alarcon Carmona
