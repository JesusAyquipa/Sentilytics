# Sentilytics: Clasificación de sentimiento y priorización de reseñas negativas en español

## Descripción del Proyecto
Sentilytics es un sistema de Procesamiento del Lenguaje Natural (PLN) diseñado para clasificar automáticamente reseñas de usuarios en español como positivas o negativas. El objetivo principal es apoyar a los equipos de atención al cliente y operaciones en los sectores de comercio, turismo y servicios, permitiéndoles identificar y priorizar la atención de opiniones negativas y quejas de manera eficiente.

## Dataset
Se utilizó el dataset `mteb/SpanishSentimentClassification` obtenido desde Hugging Face, el cual contiene reseñas en español general.
- **Distribución de clases (Entrenamiento):** 82.7% reseñas positivas y 17.3% negativas.
- El proyecto aborda este desbalance crítico priorizando métricas que evalúan el desempeño sobre la clase minoritaria (negativa).

## Estructura del Repositorio
- `Proyecto_2_corregido.ipynb`: Notebook principal ejecutable que contiene la limpieza de datos, el Análisis Exploratorio de Datos (EDA), el preprocesamiento y el entrenamiento del modelo de línea base (Baseline).
- `requirements.txt`: Archivo con las dependencias necesarias para ejecutar el proyecto.

## Instalación y Requisitos
Para reproducir este proyecto en un entorno local, asegúrate de tener Python 3.8 o superior instalado. Luego, instala las dependencias utilizando el siguiente comando en tu terminal:

pip install -r requirements.txt

## Modelo Baseline y Resultados
El modelo inicial implementado es una Regresión Logística entrenada sobre representaciones vectoriales TF-IDF (con unigramas y bigramas). Para manejar el desbalance de clases, se configuró el modelo con class_weight='balanced'.

Métricas destacadas (sobre conjunto de validación):

F1-Score (clase negativa): 0.62

Recall (clase negativa): 0.54

Precisión (clase negativa): 0.74

Balanced Accuracy: 0.75

Este baseline establece el punto de partida para futuras mejoras del proyecto (APF2 y APF3) mediante la implementación de embeddings o modelos basados en Transformers.

## Integrantes del Equipo

Angel Jesus Lopez Cardenas

Arnie Adriano Flores Jeampool

Jesus Francisco Ayquipa Ayquipa

Evers Alarcon Carmona
