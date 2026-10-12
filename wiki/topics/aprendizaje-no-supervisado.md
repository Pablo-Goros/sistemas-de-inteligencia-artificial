---
title: "Aprendizaje no supervisado"
aliases: ["unsupervised learning"]
sources: ["OFF-001", "EXT-001", "OFF-016"]
related: ["aprendizaje-automatico", "aprendizaje-profundo", "autoencoders", "mapas-autoorganizados-de-kohonen", "analisis-componentes-principales", "reglas-de-oja-y-sanger"]
prerequisites: ["aprendizaje-automatico", "optimizacion-matematica"]
---

# Aprendizaje no supervisado

## Overview

En el aprendizaje no supervisado se observan entradas sin etiquetas de salida. La clase distingue tres tareas: agrupamiento (*clustering*), asociación y reducción de dimensionalidad. Cada una busca una estructura distinta en los datos y no requiere una variable de respuesta conocida. [OFF-001, p. 28] [OFF-016, pp. 4-5]

## Core concepts

- El *clustering* agrupa datos similares; la clase presenta aplicaciones como explorar patrones y detectar anomalías. [OFF-016, pp. 10-12]
- La asociación almacena y recupera información por su relación con otros datos; la clase da a Hopfield como ejemplo. [OFF-016, pp. 13-14]
- La reducción de dimensionalidad proyecta los datos en un espacio menor. PCA y autoencoders aparecen como ejemplos; sus mecanismos se desarrollan en [análisis de componentes principales](analisis-componentes-principales.md) y [autoencoders](autoencoders.md). [OFF-016, p. 15]
- Los mapas de Kohonen agrupan entradas por aprendizaje competitivo y organizan sus unidades en una grilla; el detalle está en [mapas autoorganizados de Kohonen](mapas-autoorganizados-de-kohonen.md). [OFF-001, pp. 119-122] [OFF-017, pp. 8-16]
- Hopfield funciona como memoria asociativa: patrones almacenados se comportan como atractores de una dinámica asociada a una función de energía. El apunte también señala limitaciones de capacidad y estabilidad. [OFF-001, pp. 123-128]
- Oja y Sanger aplican reglas neuronales para obtener componentes principales iterativamente; se desarrollan en [reglas de Oja y Sanger](reglas-de-oja-y-sanger.md). [OFF-001, pp. 129-132] [OFF-020, pp. 5, 12, 17]

## How it works

El procedimiento depende de la tarea: se comparan similitudes para agrupar, se buscan asociaciones entre datos o se construyen representaciones de menor dimensión. Kohonen y las reglas de Oja/Sanger son ejemplos neuronales tratados por la materia. [OFF-016, pp. 10-16] [OFF-017, pp. 24-28] [OFF-020, pp. 12, 16-17]

## Relationships

El [aprendizaje automático](aprendizaje-automatico.md) incluye esta modalidad junto con aprendizaje supervisado y por refuerzo. Los [autoencoders](autoencoders.md) y el [análisis de componentes principales](analisis-componentes-principales.md) reducen dimensionalidad; los [mapas de Kohonen](mapas-autoorganizados-de-kohonen.md) organizan datos en una grilla.

## Sources

- [OFF-001, pp. 109-132]
- [EXT-001, pp. 35-39]
- [OFF-016, pp. 4-16]
