---
title: "Búsqueda en espacios de estados"
aliases: ["búsqueda", "state-space search", "A*", "heurística"]
sources: ["OFF-001", "OFF-008", "EXT-001"]
related: ["agentes-y-ambientes", "mejoramiento-iterativo", "optimizacion-matematica"]
prerequisites: ["agentes-y-ambientes"]
---

# Búsqueda en espacios de estados

## Overview

La búsqueda resuelve problemas modelados como estados, acciones y transiciones: parte de un estado inicial y explora caminos hasta un estado objetivo, procurando respetar un criterio de costo. El desafío es hacerlo con recursos finitos, evitando enumerar todas las posibilidades. [OFF-001, pp. 33, 35-37]

## Core concepts

- Un problema bien formado especifica estados, estado inicial, acciones, modelo de transición, función de costo y condición de solución. [OFF-001, p. 35]
- Un nodo representa una secuencia de transiciones y puede contener un estado; por eso un mismo estado puede aparecer en varios nodos con costos acumulados diferentes. La frontera contiene nodos candidatos y el conjunto explorado ayuda a evitar ciclos. [OFF-001, pp. 37-38]
- Una búsqueda es completa si encuentra una solución alcanzable y óptima si encuentra la de menor costo según el criterio elegido. [OFF-001, p. 36]
- Las búsquedas no informadas usan solo el modelo del problema: BFS expande por menor profundidad, UCS por menor costo acumulado y DFS por mayor profundidad. Sus garantías dependen de supuestos sobre ramificación y costos. [OFF-001, pp. 38-39]
- Una heurística `h(n)` estima el costo restante. Es admisible si nunca sobreestima el costo real; A* ordena la frontera con `f(n) = G(n) + h(n)` y puede ser completo y óptimo bajo las condiciones indicadas por la cátedra. [OFF-001, pp. 39-42]

## How it works

El algoritmo general mantiene una frontera y un conjunto de nodos explorados: extrae un nodo, verifica si es objetivo, genera sucesores y reordena la frontera según la estrategia. BFS, UCS, DFS, Greedy y A* se diferencian principalmente en ese criterio de ordenamiento. [OFF-001, pp. 38-40]

## Example

Sokoban se presenta como un problema de búsqueda: las cajas, paredes, trabajador y destinos forman el estado; las acciones son movimientos válidos. Sus deadlocks muestran por qué una representación y una heurística adecuadas importan. [OFF-001, p. 43]

## Aplicación práctica

El TP 1 pide proponer una representación de estado, dos heurísticas admisibles no triviales y métodos de búsqueda para el 8-puzzle. Luego requiere implementar un motor para Sokoban o GridWorld con BFS, DFS, Greedy y A*, y comparar costo de solución, nodos expandidos, frontera y tiempo de procesamiento. [OFF-008, pp. 2-4]

## Relationships

Los métodos de [mejoramiento iterativo](mejoramiento-iterativo.md) modifican soluciones sin mantener el mismo árbol de búsqueda. La [optimización matemática](optimizacion-matematica.md) aporta funciones objetivo y métodos para ajustar parámetros.

## Exam relevance

Se debe poder definir completitud, optimalidad, frontera, estados repetidos y heurística admisible, además de comparar BFS, UCS, DFS y A* bajo sus supuestos. [OFF-001, pp. 36-42]

## Sources

- [OFF-001, pp. 35-43]
- [OFF-008, pp. 2-4]
- [EXT-001, pp. 5-10]
