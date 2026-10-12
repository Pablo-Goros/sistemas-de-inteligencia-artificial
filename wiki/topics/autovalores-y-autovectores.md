---
title: "Autovalores y autovectores"
aliases: ["eigenvalue", "eigenvector"]
sources: ["OFF-018", "OFF-019", "OFF-020"]
related: ["analisis-componentes-principales", "reglas-de-oja-y-sanger", "optimizacion-matematica"]
prerequisites: []
---

# Autovalores y autovectores

## Overview

Un autovector de una matriz es un vector no nulo cuya dirección se conserva al aplicar la transformación; el autovalor asociado indica el factor de escala. La materia usa estos conceptos para construir componentes principales. [OFF-018, pp. 8-10] [OFF-019, pp. 21-23]

## Core concepts

- Para una matriz <code>A</code>, un vector <code>v ≠ 0</code> es autovector con autovalor <code>λ</code> cuando <code>Av = λv</code>. [OFF-018, pp. 8-9]
- La condición equivale a <code>(A - λI)v = 0</code>. Para que exista una solución no trivial, se resuelve el polinomio característico <code>det(A - λI) = 0</code>; sus raíces son los autovalores. [OFF-018, p. 10]
- Para cada autovalor, se resuelve <code>(A - λI)v = 0</code> para encontrar los autovectores correspondientes. [OFF-018, p. 11]
- En PCA, los autovectores de la matriz de covarianzas o correlaciones forman las cargas de las componentes, y cada autovalor expresa la varianza de su componente. [OFF-019, pp. 21-23]

## How it works

Se calcula el polinomio característico y se hallan sus raíces. Luego, para cada raíz <code>λ</code>, se resuelve el sistema homogéneo <code>(A - λI)v = 0</code> y se obtiene un vector no nulo asociado. [OFF-018, pp. 10-14]

## Relationships

El [análisis de componentes principales](analisis-componentes-principales.md) usa autovectores como cargas y ordena las componentes por sus autovalores. Las reglas de [Oja y Sanger](reglas-de-oja-y-sanger.md) presentan el cálculo iterativo de una o varias componentes principales.

## Sources

- [OFF-018, pp. 8-14]
- [OFF-019, pp. 21-23]
- [OFF-020, pp. 12, 17]
