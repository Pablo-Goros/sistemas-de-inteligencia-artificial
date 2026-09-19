---
title: "Algoritmos genéticos"
aliases: ["genetic algorithms", "aptitud", "fitness", "crossover", "mutación"]
sources: ["OFF-001", "OFF-009", "EXT-001"]
related: ["mejoramiento-iterativo", "optimizacion-matematica"]
prerequisites: ["mejoramiento-iterativo"]
---

# Algoritmos genéticos

## Overview

Un algoritmo genético es un método de optimización inspirado en evolución y selección natural. Mantiene una población de soluciones codificadas, las evalúa y genera nuevas generaciones mediante selección, crossover y mutación. [OFF-001, pp. 49-50]

## Core concepts

- Un individuo es una solución candidata codificada; sus partes pueden interpretarse como genes y la población reúne individuos. [OFF-001, pp. 49-51]
- La función de aptitud o fitness evalúa la calidad de cada individuo y guía la selección de progenitores. [OFF-001, pp. 50-52]
- Crossover combina material de dos progenitores. El apunte presenta cruces de un punto, dos puntos, anular y uniforme. [OFF-001, pp. 53-54]
- La mutación introduce cambios aleatorios en los individuos y ayuda a preservar diversidad; el reemplazo de la población regula cuánto se conserva y cuánto se renueva. [OFF-001, pp. 54-55]

## How it works

Se inicializa una población, se calcula el fitness, se seleccionan progenitores, se aplican crossover y mutación, y se construye la siguiente generación. El ciclo se repite hasta alcanzar un criterio de terminación. [OFF-001, pp. 50-55]

## Aplicación práctica

El TP 2 usa la aproximación de una imagen mediante triángulos como caso de diseño: exige definir individuo, genes y fitness, justificar cruza, mutación y criterio de parada, e implementar varias estrategias de selección y supervivencia. También pide reportar métricas como fitness, error y generaciones para defender la implementación. [OFF-009, pp. 2-4]

## Relationships

Como el [mejoramiento iterativo](mejoramiento-iterativo.md), un algoritmo genético optimiza una función, pero trabaja con una población y no con una única solución vecina. La [optimización matemática](optimizacion-matematica.md) ofrece otra familia de métodos para ajustar objetivos.

## Exam relevance

Hay que distinguir individuo, gen, fitness, selección, crossover y mutación, y poder describir el ciclo de generación de una población. [OFF-001, pp. 49-55]

## Sources

- [OFF-001, pp. 49-55]
- [OFF-009, pp. 2-4]
- [EXT-001, pp. 17-22]
