---
title: "Aprendizaje automático"
aliases: ["machine learning", "ML", "generalización", "pipeline"]
sources: ["OFF-001", "OFF-002", "OFF-011", "EXT-001"]
related: ["optimizacion-matematica", "aprendizaje-supervisado", "aprendizaje-no-supervisado", "aprendizaje-por-refuerzo", "ciencia-de-datos"]
prerequisites: ["introduccion-inteligencia-artificial", "optimizacion-matematica"]
---

# Aprendizaje automático

## Overview

El aprendizaje automático ajusta parámetros de un algoritmo para identificar relaciones o mapeos entre datos. El objetivo no es solo ajustar el conjunto conocido, sino generalizar a muestras nuevas. [OFF-001, pp. 27-29, 103-105]

## Core concepts

- El mapa de técnicas oficial ubica clasificación y regresión dentro del aprendizaje supervisado; clustering, reglas de asociación y reducción de dimensionalidad dentro del no supervisado; y redes neuronales/aprendizaje profundo, ensembles y aprendizaje por refuerzo como otras familias de Machine Learning. [OFF-011, p. 12]

- La matriz de datos `X` organiza muestras en filas y variables en columnas; una muestra puede tener una etiqueta `Y`. Las transformaciones convierten datos crudos en características más útiles. [OFF-001, pp. 27-28]
- Los parámetros libres se ajustan mediante optimización; los hiperparámetros pertenecen al algoritmo y no se ajustan mediante la función de costo principal. [OFF-001, p. 28]
- El aprendizaje supervisado conoce entradas y salidas; el no supervisado conoce entradas pero busca estructura; el aprendizaje por refuerzo usa interacción y recompensa. [OFF-001, p. 28] [EXT-001, p. 13]
- El pipeline de Machine Learning articula el problema, los datos, su transformación, el entrenamiento y la evaluación. [OFF-001, pp. 103-105]

## How it works

Se define el mapeo o tarea, se preparan los datos, se elige un modelo, se ajustan sus parámetros con una función de costo y se comprueba su comportamiento en datos no usados para el ajuste. La separación entre entrenamiento y prueba permite evaluar generalización. [OFF-001, pp. 28, 103-105]

## Relationships

La [optimización matemática](optimizacion-matematica.md) proporciona el mecanismo de ajuste. Las variantes [supervisada](aprendizaje-supervisado.md), [no supervisada](aprendizaje-no-supervisado.md) y por [refuerzo](aprendizaje-por-refuerzo.md) se diferencian por la información disponible para aprender.

## Exam relevance

Se debe poder distinguir parámetros de hiperparámetros, aprendizaje de generalización, y las tres modalidades de aprendizaje. [OFF-001, pp. 27-29]

## Sources

- [OFF-001, pp. 27-29, 103-105]
- [OFF-011, pp. 4, 8, 12-14]
- [EXT-001, pp. 3, 13, 23-25]
