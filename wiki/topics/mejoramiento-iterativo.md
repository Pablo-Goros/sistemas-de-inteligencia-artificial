---
title: "Mejoramiento iterativo"
aliases: ["búsqueda local", "hill climbing", "simulated annealing", "beam search"]
sources: ["OFF-001", "EXT-001"]
related: ["busqueda-en-espacios-de-estados", "algoritmos-geneticos", "optimizacion-matematica"]
prerequisites: ["busqueda-en-espacios-de-estados"]
---

# Mejoramiento iterativo

## Overview

Los algoritmos de mejoramiento iterativo parten de una solución y la modifican mediante perturbaciones para mejorar una función objetivo. Trabajan sobre soluciones vecinas y son útiles cuando explorar todo el espacio resulta demasiado costoso. [OFF-001, pp. 43-45]

## Core concepts

- Hill Climbing elige sucesivamente una solución vecina de mejor valuación, pero puede quedar atrapado en máximos locales. [OFF-001, p. 45]
- Simulated Annealing agrega una temperatura que controla la estocasticidad: al comienzo puede aceptar movimientos que empeoran la función para explorar, y reduce gradualmente esa posibilidad. [OFF-001, p. 46]
- Beam Search conserva los mejores `k` nodos entre caminos y los compara conjuntamente; puede perder diversidad si todos convergen hacia la misma región. [OFF-001, pp. 46-47]
- La tensión entre explorar alternativas y explotar la mejor solución conocida aparece de forma explícita en estos métodos. [OFF-001, p. 46]

## How it works

En un problema como el viajante de comercio se toma una ruta inicial, se evalúa, se generan permutaciones vecinas y se conserva una alternativa según la estrategia. Simulated Annealing decide aceptar una alternativa peor con una probabilidad que depende de la diferencia y la temperatura. [OFF-001, pp. 44-46]

## Relationships

La [búsqueda en espacios de estados](busqueda-en-espacios-de-estados.md) conserva una frontera de nodos y busca un objetivo; el mejoramiento iterativo opera directamente sobre soluciones y su función objetivo. Los [algoritmos genéticos](algoritmos-geneticos.md) introducen una población y operadores evolutivos.

## Exam relevance

Conviene comparar Hill Climbing, Simulated Annealing y Beam Search por representación de la solución, mecanismo de selección, manejo de óptimos locales y uso de memoria. [OFF-001, pp. 45-47]

## Sources

- [OFF-001, pp. 43-47]
- [EXT-001, pp. 11-12]
