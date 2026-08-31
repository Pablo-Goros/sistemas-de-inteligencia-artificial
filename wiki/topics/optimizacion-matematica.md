---
title: "Optimización matemática"
aliases: ["optimización", "gradiente descendente", "gradient descent", "SGD", "simplex"]
sources: ["OFF-001", "EXT-001"]
related: ["aprendizaje-automatico", "aprendizaje-supervisado", "mejoramiento-iterativo"]
prerequisites: []
---

# Optimización matemática

## Overview

La optimización matemática busca parámetros que minimicen o maximicen una función objetivo, posiblemente bajo restricciones. En IA permite ajustar pesos y parámetros libres para reducir una función de costo. [OFF-001, pp. 59-63]

## Core concepts

- Un problema de optimización especifica una función objetivo y, cuando corresponde, restricciones; el método simplex trata problemas lineales con restricciones. [OFF-001, pp. 61-62]
- En optimización no lineal, el gradiente indica la dirección de mayor crecimiento local. El gradiente descendente actualiza en sentido contrario para reducir el costo. [OFF-001, pp. 63-65]
- El Hessiano describe curvatura; un punto con gradiente nulo y Hessiano definido positivo es un mínimo local bajo la condición suficiente presentada. [OFF-001, p. 64]
- Momentum, métodos conjugados, Newton, cuasi-Newton y gradiente descendente estocástico modifican cómo se elige la dirección o la información usada en cada actualización. [OFF-001, pp. 65-68]

## How it works

Partiendo de `xk`, se calcula una dirección de descenso y un paso `αk`, y se obtiene `xk+1`. En el caso estocástico, el gradiente se estima con muestras o lotes, lo que permite trabajar con conjuntos de datos grandes. [OFF-001, pp. 65, 67-68]

## Relationships

El [aprendizaje automático](aprendizaje-automatico.md) formula el entrenamiento como ajuste de parámetros; el [aprendizaje supervisado](aprendizaje-supervisado.md) usa estos métodos para adaptar redes y regresores.

## Exam relevance

Es importante interpretar función objetivo, restricciones, gradiente, Hessiano y tasa de aprendizaje, y comparar gradiente descendente, Newton y variantes estocásticas. [OFF-001, pp. 61-68]

## Sources

- [OFF-001, pp. 59-68]
- [EXT-001, pp. 23-25]
