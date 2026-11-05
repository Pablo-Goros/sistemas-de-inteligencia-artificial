---
title: "Aprendizaje no supervisado"
aliases: ["unsupervised learning", "clustering", "PCA", "Kohonen", "Hopfield"]
sources: ["OFF-001", "EXT-001", "OFF-016", "OFF-017"]
related: ["aprendizaje-automatico", "aprendizaje-profundo", "autoencoders"]
prerequisites: ["aprendizaje-automatico", "optimizacion-matematica"]
---

# Aprendizaje no supervisado

## Panorama general

En el aprendizaje no supervisado se observan entradas sin etiquetas de salida. Los métodos buscan estructura interna, agrupamientos, representaciones de menor dimensión o patrones almacenables. [OFF-001, pp. 28, 109-114]

## Conceptos centrales

- Clustering agrupa muestras según similitud; las transformaciones de datos buscan representar mejor la estructura interna. [OFF-001, pp. 109-112]
- PCA transforma los datos usando direcciones asociadas a sus componentes principales para obtener una representación más compacta. [OFF-001, pp. 113-114]
- La clase de autoencoders conecta PCA y SVD con la reconstrucción lineal: con datos centrados y en la construcción ortonormal desarrollada, el código reproduce las proyecciones sobre componentes principales. Las activaciones no lineales motivan extender la reducción de dimensionalidad; la derivación y sus condiciones se detallan en [autoencoders](autoencoders.md). [OFF-016, pp. 8-16; OFF-017, pp. 2-3]
- La red de Kohonen o mapa autoorganizado aprende competitivamente y preserva relaciones topológicas en una grilla de unidades. [OFF-001, pp. 119-122]
- Hopfield funciona como memoria asociativa: patrones almacenados se comportan como atractores de una dinámica asociada a una función de energía. El apunte también señala limitaciones de capacidad y estabilidad. [OFF-001, pp. 123-128]
- Oja estabiliza el aprendizaje de una neurona lineal para extraer componentes; Sanger extiende la idea para extraer múltiples componentes. [OFF-001, pp. 129-132]

## Funcionamiento

Según el método, se calcula similitud o varianza, se actualizan representaciones o pesos sin usar etiquetas y se repite hasta que la estructura aprendida se estabiliza. En Kohonen compiten unidades y se actualizan la ganadora y su vecindad. [OFF-001, pp. 113-122]

## Relaciones

Los [autoencoders](autoencoders.md) aprenden representaciones mediante reconstrucción. El [aprendizaje automático](aprendizaje-automatico.md) incluye esta modalidad junto con aprendizaje supervisado y por refuerzo.

## Relevancia para evaluaciones

Hay que distinguir clustering, reducción de dimensionalidad, aprendizaje competitivo, memoria asociativa y extracción de componentes mediante Oja/Sanger. [OFF-001, pp. 109-132]

## Fuentes

- [OFF-001, pp. 109-132]
- [EXT-001, pp. 35-39]
- [OFF-016, pp. 8-16]
- [OFF-017, pp. 2-3]
