---
title: "Perceptrón multicapa"
aliases: ["multilayer perceptron", "MLP", "red neuronal feed-forward"]
sources: ["OFF-004", "OFF-010"]
related: ["perceptron-simple", "retropropagacion", "aprendizaje-supervisado", "aprendizaje-profundo"]
prerequisites: ["perceptron-simple", "optimizacion-matematica"]
---

# Perceptrón multicapa

## Overview

Un perceptrón multicapa (MLP) combina neuronas en capas intermedias y una capa de salida. Esta composición permite modelar transformaciones más complejas que un perceptrón simple y se entrena ajustando sus pesos con propagación hacia adelante, una función de costo y retropropagación. [OFF-004, pp. 3-16, 33]

## Core concepts

- La arquitectura tiene una capa de entrada, una o más capas ocultas y una capa de salida; las neuronas de una capa usan las salidas de la capa anterior. [OFF-004, pp. 11-14]
- El teorema de aproximación universal presentado establece una capacidad de aproximación teórica para funciones continuas, pero no proporciona una receta para elegir una arquitectura ni garantiza que la solución sea práctica. [OFF-004, pp. 8-10, 60]
- La arquitectura debe definirse manualmente: el material señala que no hay una receta *a priori* para la mejor arquitectura. [OFF-004, p. 60]
- Los pesos deben inicializarse con valores aleatorios pequeños. Inicializarlos todos en cero produce un problema de simetría. [OFF-004, pp. 57-58]
- El bias puede representarse mediante una entrada constante por capa, de modo que se ajuste como un peso adicional. [OFF-004, pp. 63-70]

## How it works

En el *feed-forward pass*, cada neurona aplica su activación a la suma ponderada de las salidas de la capa anterior; las salidas intermedias se convierten en entradas de la siguiente capa hasta obtener la salida de la red. [OFF-004, pp. 12-14]

Durante el entrenamiento, se compara esa salida con el objetivo mediante una función de costo —el material menciona MSE— y se calcula una actualización de pesos por descenso del gradiente usando [retropropagación](retropropagacion.md). Las actualizaciones pueden ser online, por mini-lote o batch, según si se acumulan para uno, varios o todos los datos. [OFF-004, pp. 19-33, 53-56]

## Aplicación práctica

El TP 3 usa XOR para contrastar un MLP con el perceptrón escalón y recomienda calcular manualmente las arquitecturas `[2, 2, 1]` y `[2, 3, 2, 1]`. Para reconocimiento de dígitos exige explorar tasa de aprendizaje, arquitectura y mecanismos de optimización, ajustar parámetros e hiperparámetros sin usar el conjunto de test y analizar el efecto de más datos y ruido. [OFF-010, pp. 2, 4-5]

## Relationships

El MLP extiende el [perceptrón simple](perceptron-simple.md) con capas ocultas. [Retropropagación](retropropagacion.md) permite atribuir el error a los parámetros de esas capas; las redes con más capas se conectan con [aprendizaje profundo](aprendizaje-profundo.md).

## Exam relevance

El material destaca poder explicar qué optimiza una red neuronal, el cálculo *feed-forward*, la diferencia entre modalidades online/mini-batch/batch, la inicialización aleatoria y el papel del bias. [OFF-004, pp. 12-14, 53-58, 61, 63-70]

## Sources

- [OFF-004, pp. 3-70]
- [OFF-010, pp. 2, 4-5]
