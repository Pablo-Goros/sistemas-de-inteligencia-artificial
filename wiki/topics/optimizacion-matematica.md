---
title: "Optimización matemática"
aliases: ["optimización", "gradiente descendente", "gradient descent", "SGD", "simplex"]
sources: ["OFF-001", "OFF-012", "EXT-001"]
related: ["aprendizaje-automatico", "aprendizaje-supervisado", "mejoramiento-iterativo"]
prerequisites: []
---

# Optimización matemática

## Overview

La optimización matemática busca parámetros que minimicen o maximicen una función objetivo, posiblemente bajo restricciones. En IA permite ajustar pesos y parámetros libres para reducir una función de costo. [OFF-001, pp. 59-63]

## Core concepts

- Para una función diferenciable, gradiente nulo y Hessiano semidefinido positivo son condiciones necesarias de mínimo local; un Hessiano definido positivo da la condición suficiente presentada. [OFF-012, pp. 18-19]
- Una dirección de decrecimiento tiene producto interno negativo con el gradiente. Momentum combina direcciones recientes para suavizar el zigzag; Newton usa el Hessiano y los métodos cuasi-Newton aproximan su inversa para reducir ese costo. [OFF-012, pp. 24, 28-30]
- En SGD se estima el gradiente con una parte de los datos; los mini-batches usan subconjuntos de patrones. AdaGrad adapta la actualización por coordenada y Adam mantiene estimaciones de primer y segundo momento. [OFF-012, pp. 42-48]

- Un problema de optimización especifica una función objetivo y, cuando corresponde, restricciones; el método simplex trata problemas lineales con restricciones. [OFF-001, pp. 61-62]
- En optimización no lineal, el gradiente indica la dirección de mayor crecimiento local. El gradiente descendente actualiza en sentido contrario para reducir el costo. [OFF-001, pp. 63-65]
- El Hessiano describe curvatura; un punto con gradiente nulo y Hessiano definido positivo es un mínimo local bajo la condición suficiente presentada. [OFF-001, p. 64]
- Momentum, métodos conjugados, Newton, cuasi-Newton y gradiente descendente estocástico modifican cómo se elige la dirección o la información usada en cada actualización. [OFF-001, pp. 65-68]

## How it works

El esquema iterativo actualiza `xk+1 = xk + αk dk` a partir de una dirección `dk` y un paso `αk`. El paso puede ser fijo o elegirse mediante una búsqueda unidimensional; si es demasiado grande puede impedir la convergencia y si es demasiado pequeño la vuelve lenta. [OFF-012, pp. 22-25]

Partiendo de `xk`, se calcula una dirección de descenso y un paso `αk`, y se obtiene `xk+1`. En el caso estocástico, el gradiente se estima con muestras o lotes, lo que permite trabajar con conjuntos de datos grandes. [OFF-001, pp. 65, 67-68]

## Relationships

El [aprendizaje automático](aprendizaje-automatico.md) formula el entrenamiento como ajuste de parámetros; el [aprendizaje supervisado](aprendizaje-supervisado.md) usa estos métodos para adaptar redes y regresores.

## Exam relevance

Es importante interpretar función objetivo, restricciones, gradiente, Hessiano y tasa de aprendizaje, y comparar gradiente descendente, Newton y variantes estocásticas. [OFF-001, pp. 61-68]

## Sources

- [OFF-001, pp. 59-68]
- [OFF-012, pp. 11-31, 38-48]
- [EXT-001, pp. 23-25]
