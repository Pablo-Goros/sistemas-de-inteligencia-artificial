---
title: "Mapas autoorganizados de Kohonen"
aliases: ["Kohonen", "SOM", "mapa de Kohonen", "self-organizing map"]
sources: ["OFF-017"]
related: ["aprendizaje-no-supervisado", "normalizacion-de-datos"]
prerequisites: ["aprendizaje-no-supervisado"]
---

# Mapas autoorganizados de Kohonen

## Overview

Un mapa autoorganizado (*self-organizing map*, SOM) aprende sin etiquetas y ubica entradas en una grilla de neuronas. Cada neurona representa una región de los datos; las neuronas próximas en la grilla tienden a representar entradas similares. [OFF-017, pp. 4, 10-16]

## Core concepts

- La red tiene una capa de salida organizada como grilla rectangular o hexagonal. Cada neurona posee un vector de pesos de la misma dimensión que la entrada y actúa como su representante. [OFF-017, pp. 6, 11-16]
- En cada iteración se elige la neurona ganadora (*best matching unit*): es la que tiene el vector de pesos más cercano a la entrada según una medida de similitud. La clase muestra distancia euclídea como ejemplo. [OFF-017, pp. 24-25, 29]
- El aprendizaje es competitivo: una entrada activa a la ganadora y las unidades de su vecindario también actualizan sus pesos. [OFF-017, pp. 8-10, 26-27]
- La clase recomienda estandarizar las variables para que sus escalas no dominen la medida de similitud. También advierte que una inicialización inadecuada puede dejar neuronas que nunca ganan y que no presenta una regla general para elegir el tamaño de la grilla. [OFF-017, pp. 18-22, 29-30, 38]

## How it works

1. Se define una grilla de <code>k × k</code> neuronas y se inicializa un vector de pesos <code>W_j</code> para cada neurona.
2. Para cada entrada <code>x</code>, se busca la ganadora <code>j* = argmin_j d(x, W_j)</code>.
3. Se define un vecindario alrededor de la ganadora mediante un radio <code>R(i)</code>. La clase indica que el radio puede reducirse hasta uno o mantenerse constante.
4. Para cada neurona <code>j</code> dentro del vecindario se actualiza <code>W_j(i+1) = W_j(i) + η(i)(x - W_j(i))</code>; fuera del vecindario, los pesos quedan iguales. La tasa de aprendizaje <code>η(i)</code> tiende a cero. Se repiten las iteraciones sobre las entradas. [OFF-017, pp. 24-28]

## Example

La matriz U (*Unified Distance Matrix*) representa, para cada neurona, la distancia euclídea promedio entre su vector de pesos y los de sus neuronas vecinas. La clase propone observar distancias pequeñas como indicio de que el mapa organiza adecuadamente las regiones próximas. [OFF-017, p. 36]

## Relationships

Kohonen es un método de [aprendizaje no supervisado](aprendizaje-no-supervisado.md). La [normalización de datos](normalizacion-de-datos.md) importa porque las escalas de las variables afectan las distancias que determinan la neurona ganadora.

## Sources

- [OFF-017, pp. 4-16, 18-22, 24-30, 33-38]
