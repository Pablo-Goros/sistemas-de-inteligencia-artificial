---
title: "Análisis de componentes principales"
aliases: ["PCA", "Principal Component Analysis"]
sources: ["OFF-018", "OFF-019"]
related: ["aprendizaje-no-supervisado", "autovalores-y-autovectores", "reglas-de-oja-y-sanger", "normalizacion-de-datos"]
prerequisites: ["aprendizaje-no-supervisado", "autovalores-y-autovectores"]
---

# Análisis de componentes principales

## Overview

El análisis de componentes principales (PCA) transforma variables posiblemente correlacionadas en combinaciones lineales no correlacionadas. Al ordenar esas componentes por la variabilidad que explican, se puede representar el conjunto con menos dimensiones. [OFF-019, pp. 13-16, 21-23]

## Core concepts

- La covarianza muestral mide la asociación lineal entre dos variables; la correlación expresa esa asociación después de estandarizarlas. La matriz de covarianzas reúne las covarianzas entre pares de variables. [OFF-019, pp. 7-11]
- Las cargas (*loadings*) de las componentes son autovectores de la matriz de covarianzas o de correlaciones. Una componente se calcula como combinación lineal de las variables centradas; si se estandarizaron, la clase indica que no hace falta volver a restar la media. [OFF-019, pp. 20-22]
- El autovalor asociado a una componente es su varianza. Al ordenar los autovalores de mayor a menor, las primeras componentes retienen la mayor variabilidad y permiten reducir la dimensión. [OFF-019, pp. 22-23]
- Si las variables tienen escalas muy distintas, la clase recomienda estandarizarlas y usar la matriz de correlaciones. Cuando tienen las mismas unidades, presenta como posibles ambas alternativas: covarianzas o correlaciones. [OFF-019, pp. 25-27]

## How it works

La clase propone este procedimiento:

1. Construir la matriz de datos <code>X</code>, con variables en columnas.
2. Estandarizar las variables.
3. Calcular la matriz de correlaciones <code>S_x</code>.
4. Calcular autovalores y autovectores.
5. Ordenar los autovalores de mayor a menor.
6. Formar una matriz <code>V</code> con los autovectores de mayor autovalor.
7. Calcular las nuevas variables <code>Y</code> como combinaciones lineales de las originales. [OFF-018, pp. 10-11] [OFF-019, pp. 20-23, 32]

## Relationships

PCA es una técnica de [aprendizaje no supervisado](aprendizaje-no-supervisado.md) y reducción de dimensionalidad. Se apoya en [autovalores y autovectores](autovalores-y-autovectores.md); las reglas de [Oja y Sanger](reglas-de-oja-y-sanger.md) muestran una forma iterativa de obtener una o varias componentes. La [normalización de datos](normalizacion-de-datos.md) ayuda a evitar que las distintas escalas dominen el resultado.

## Sources

- [OFF-018, pp. 10-11]
- [OFF-019, pp. 7-11, 13-16, 20-32]
