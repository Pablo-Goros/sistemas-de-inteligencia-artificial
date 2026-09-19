---
title: "Perceptrón simple"
aliases: ["simple perceptron", "ADALINE", "Adaptive Linear Element", "neurona de McCulloch y Pitts"]
sources: ["OFF-002", "OFF-003", "OFF-010"]
related: ["aprendizaje-supervisado", "optimizacion-matematica", "perceptron-multicapa"]
prerequisites: ["aprendizaje-supervisado", "optimizacion-matematica"]
---

# Perceptrón simple

## Overview

El perceptrón simple modela una neurona como una combinación ponderada de entradas seguida de una función de activación. Sirve para aprender pesos y un bias a partir de ejemplos supervisados; su versión escalón clasifica únicamente problemas linealmente separables. [OFF-002, pp. 14-15, 21-24, 31-34]

## Core concepts

- Para una entrada `x`, la neurona calcula una suma ponderada y un término independiente: `h = Σᵢ xᵢwᵢ + w₀`; el peso `w₀` cumple el papel de bias o umbral. También puede incorporarse añadiendo una entrada constante `x₀ = 1`. [OFF-002, pp. 34, 43] [OFF-003, pp. 12-13]
- Con activación escalón, la salida es binaria. Su frontera de decisión es un hiperplano y separa las clases según el signo de la proyección sobre ese hiperplano. [OFF-002, pp. 15, 21-24]
- La variante lineal, ADALINE, usa la identidad como activación y produce valores reales, por lo que se presenta para ajuste de una relación lineal. [OFF-003, pp. 4-8]
- La variante no lineal reemplaza la activación por una sigmoidea, como `tanh(βh)` o la logística; el parámetro `β` modifica su forma. [OFF-003, pp. 23-26]
- Aprendizaje y generalización no son sinónimos: el primero ajusta el modelo sobre los datos disponibles; el segundo es su desempeño en datos que no participaron del entrenamiento. [OFF-002, pp. 44-46]

## How it works

En el perceptrón escalón se recorren ejemplos, se calcula la salida y se actualizan los pesos cuando difiere de la salida esperada. Para etiquetas `{-1, 1}`, la presentación expresa la corrección como `Δw = η(ζᵘ - oᵘ)xᵘ`; el bias se actualiza análogamente. [OFF-002, pp. 33-34, 42-44]

Para las versiones lineal y sigmoidea se usa el costo cuadrático y descenso del gradiente. Al evaluar un ejemplo, la actualización incluye la derivada de la activación: `Δw = η(ζᵘ - oᵘ)θ'(hᵘ)xᵘ`. El material identifica este formato, que actualiza al evaluar cada dato, como entrenamiento *online*. [OFF-003, pp. 12-21, 23-24]

## Example

Con dos características, la expresión `-x₁ + x₂ + 1 = 0` define una recta de decisión. Al añadir el bias, la frontera no queda restringida a pasar por el origen, lo que aporta flexibilidad al clasificador. [OFF-002, pp. 36, 43] [OFF-003, p. 13]

## Aplicación práctica

El TP 3 propone validar el perceptrón escalón con AND, el lineal ajustando una función como `y = x` y el no lineal ajustando `y = tanh(x)`. Para el caso de fraude pide comparar los perceptrones lineal y no lineal, observar subajuste o saturación, elegir uno para generalización y fundamentar métricas, partición y umbral de detección. [OFF-010, pp. 2-3]

## Relationships

Es un caso de [aprendizaje supervisado](aprendizaje-supervisado.md): necesita pares de entrada y salida esperada. Su ajuste por gradiente se apoya en [optimización matemática](optimizacion-matematica.md). La limitación de separabilidad del modelo escalón motiva el [perceptrón multicapa](perceptron-multicapa.md).

## Exam relevance

La siguiente clase pide explícitamente identificar el aporte de McCulloch y Pitts, los problemas resolubles con el perceptrón escalón, el mecanismo para hallar pesos y bias, y el efecto de reemplazar la activación por una lineal o sigmoidea. [OFF-004, p. 2]

## Sources

- [OFF-002, pp. 14-15, 21-24, 31-46]
- [OFF-003, pp. 4-26]
- [OFF-010, pp. 2-3]
