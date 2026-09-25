---
title: "Aprendizaje supervisado"
aliases: ["supervised learning"]
sources: ["OFF-001", "OFF-002", "OFF-003", "OFF-004", "OFF-011", "EXT-001"]
related: ["aprendizaje-automatico", "evaluacion-de-modelos", "optimizacion-matematica", "perceptron-simple", "perceptron-multicapa", "retropropagacion", "aprendizaje-profundo"]
prerequisites: ["aprendizaje-automatico", "optimizacion-matematica"]
---

# Aprendizaje supervisado

## Overview

En el aprendizaje supervisado se conocen los pares de entrada y salida esperada. El modelo ajusta sus parámetros para aproximar ese mapeo y luego producir predicciones para entradas nuevas. [OFF-001, pp. 27-29] [EXT-001, p. 13]

## Core concepts

- La clasificación y la regresión son tareas de aprendizaje supervisado. [OFF-011, p. 12]
- Una neurona calcula una combinación ponderada de entradas y aplica una función de activación. El [perceptrón simple](perceptron-simple.md) escalón produce una frontera lineal; por eso no puede resolver directamente problemas no linealmente separables como XOR. [OFF-001, pp. 69-80] [OFF-002, pp. 21-31]
- El [perceptrón multicapa](perceptron-multicapa.md) compone capas de neuronas y funciones no lineales, lo que permite construir fronteras más expresivas. [OFF-001, pp. 81-84] [OFF-004, pp. 3-15]
- La propagación hacia adelante calcula la salida; la [retropropagación](retropropagacion.md) calcula cómo contribuyen los parámetros al error y permite actualizarlos mediante descenso del gradiente. [OFF-001, pp. 84-90] [OFF-004, pp. 19-33, 39-50]
- El entrenamiento puede ser incremental, por lotes o mediante mini-lotes; momentum, RMSProp, Adam y tasas adaptativas son variantes de optimización tratadas por el apunte. [OFF-001, pp. 88-92]

## How it works

Para cada entrada se calcula una salida, se compara con la etiqueta mediante una función de costo, se propaga el error hacia las capas anteriores y se actualizan los pesos. El proceso se repite sobre el conjunto de entrenamiento. [OFF-001, pp. 84-90] [OFF-004, pp. 19-33]

## Example

Para resolver XOR, una red multicapa puede combinar regiones separadas por neuronas ocultas hasta producir una clasificación final no lineal. [OFF-001, pp. 81-83]

## Relationships

La [evaluación de modelos](evaluacion-de-modelos.md) mide si el mapeo aprendido generaliza. La [optimización matemática](optimizacion-matematica.md) fundamenta la actualización de pesos; el [aprendizaje profundo](aprendizaje-profundo.md) extiende la idea mediante redes más profundas.

## Exam relevance

Conviene explicar separabilidad lineal, arquitectura MLP, forward propagation, backpropagation y diferencias entre entrenamiento incremental y por lotes. [OFF-001, pp. 71-92]

## Sources

- [OFF-001, pp. 69-92]
- [OFF-002, pp. 21-46]
- [OFF-003, pp. 8-26]
- [OFF-004, pp. 3-58]
- [OFF-011, p. 12]
- [EXT-001, pp. 26-34]
