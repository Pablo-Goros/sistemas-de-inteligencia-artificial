---
title: "Normalización de datos"
aliases: ["normalización", "feature scaling", "estandarización", "z-score", "unit length scaling"]
sources: ["OFF-014"]
related: ["evaluacion-de-modelos", "aprendizaje-supervisado", "ciencia-de-datos"]
prerequisites: ["aprendizaje-supervisado"]
---

# Normalización de datos

## Overview

La normalización transforma las escalas de las variables de entrada. La clase presenta escalado min-max, estandarización y escalado por longitud unitaria como procedimientos distintos. [OFF-014, pp. 31-36]

## Core concepts

- El escalado min-max transforma un valor `x` al intervalo `[a,b]`: `x' = ((x - xmin)/(xmax - xmin))(b - a) + a`. Para `[0,1]`, queda `x' = (x - xmin)/(xmax - xmin)`. [OFF-014, p. 32]
- La estandarización centra cada variable en su media y la divide por su desvío estándar: `x' = (x - media(x))/s`. La clase también la llama *Z-score*. [OFF-014, p. 33]
- El escalado por longitud unitaria divide un vector por su norma L2: `x' = x/||x||`. [OFF-014, p. 36]

Estos procedimientos no son intercambiables: min-max establece un intervalo, Z-score expresa desviaciones respecto de la media y el escalado unitario normaliza la longitud del vector. La elección depende de qué escala se busca modificar.

## Relationships

La normalización es un paso de preparación de datos que puede acompañar el entrenamiento supervisado. Se distingue de la [evaluación de modelos](evaluacion-de-modelos.md), que mide el rendimiento sobre datos de entrenamiento y prueba.

## Sources

- [OFF-014, pp. 31-36]
