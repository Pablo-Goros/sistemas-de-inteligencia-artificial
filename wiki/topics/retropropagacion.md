---
title: "Retropropagación"
aliases: ["backpropagation", "back propagation", "propagación hacia atrás"]
sources: ["OFF-004"]
related: ["perceptron-multicapa", "optimizacion-matematica", "aprendizaje-supervisado"]
prerequisites: ["perceptron-multicapa", "optimizacion-matematica"]
---

# Retropropagación

## Overview

La retropropagación es el algoritmo que permite calcular eficientemente cómo contribuye cada peso al error de un perceptrón multicapa, incluso en las capas ocultas. Combina la regla de la cadena con descenso del gradiente para ajustar los parámetros. [OFF-004, pp. 20-33]

## Core concepts

- Parte de una función de costo que compara la salida de la red con la salida esperada; la actualización sigue `Δw = -η ∂E/∂w`. [OFF-004, pp. 19-20, 27]
- En la capa de salida, la derivada del costo respecto de un peso se descompone mediante la regla de la cadena a través de la salida, su entrada neta y el peso. [OFF-004, pp. 39-43]
- En una capa oculta, el cálculo incorpora además la contribución al error de las neuronas de la capa siguiente; esa dependencia permite definir los deltas de las capas sin salida. [OFF-004, pp. 44-50]
- Las expresiones de las diapositivas se desarrollan para un único dato de entrada; deben extenderse al conjunto de datos de acuerdo con la estrategia de entrenamiento elegida. [OFF-004, pp. 39-50, 53]

## How it works

Primero se realiza una pasada hacia adelante para obtener activaciones y salida. Luego se calcula el error en la salida y se propagan hacia atrás los términos necesarios para las derivadas de cada capa. Finalmente, se acumulan o aplican las actualizaciones según el esquema online, mini-batch o batch. [OFF-004, pp. 12-14, 19-32, 53-54]

## Relationships

El algoritmo completa el entrenamiento del [perceptrón multicapa](perceptron-multicapa.md). La dirección y magnitud de sus actualizaciones dependen de [optimización matemática](optimizacion-matematica.md), en particular del descenso del gradiente.

## Exam relevance

La presentación introduce de manera explícita la regla de la cadena para capas ocultas y pregunta cómo se entrena la red; se debe poder explicar la diferencia entre el cálculo en la capa de salida y en una capa oculta. [OFF-004, pp. 16-32, 39-50]

## Sources

- [OFF-004, pp. 12-14, 19-32, 39-54]
