---
title: "Reglas de Oja y Sanger"
aliases: ["regla de Oja", "regla de Sanger"]
sources: ["OFF-020"]
related: ["aprendizaje-no-supervisado", "analisis-componentes-principales", "autovalores-y-autovectores", "perceptron-simple"]
prerequisites: ["perceptron-simple", "analisis-componentes-principales"]
---

# Reglas de Oja y Sanger

## Overview

Las reglas de Oja y Sanger son métodos neuronales de aprendizaje no supervisado para calcular componentes principales de forma iterativa. Oja obtiene la primera componente; Sanger extiende el método para obtener varias. [OFF-020, pp. 5, 12, 17]

## Core concepts

- La regla de Hebb actualiza los pesos usando la entrada y la salida de una neurona lineal. Las diapositivas explican que esa actualización puede crecer sin límite y volver inestable el aprendizaje. [OFF-020, pp. 7-9]
- Oja agrega un término que limita la norma de los pesos. La actualización presentada es <code>w ← w + η y(x - y w)</code>, con salida <code>y = wᵀx</code>; el algoritmo recorre entradas centradas y repite las actualizaciones. [OFF-020, pp. 10-12, 16]
- La clase afirma que, tras varias iteraciones, Oja converge al autovector asociado al mayor autovalor y con él se construye la primera componente principal. También indica que la norma de <code>w</code> permanece acotada. [OFF-020, p. 12]
- Sanger extiende Oja y permite obtener varias componentes principales. La diapositiva correspondiente atribuye la convergencia de sus vectores a la matriz de covarianzas. [OFF-020, p. 17]
- Las diapositivas nombran la matriz de correlaciones al describir la convergencia de Oja y la matriz de covarianzas al describir Sanger. Mantengo esa atribución por separado porque el material no explica en esas páginas las condiciones que relacionan ambas formulaciones. [OFF-020, pp. 12, 17]

## How it works

Para cada entrada <code>x</code>, se calcula <code>y = wᵀx</code> y se actualiza <code>w</code> con <code>w ← w + η y(x - y w)</code>. La clase presenta pesos iniciales aleatorios y una tasa de aprendizaje que disminuye, o un valor inicial pequeño; recomienda estandarizar las entradas cuando no se conoce el autovalor. [OFF-020, pp. 14-16]

## Relationships

Estas reglas ofrecen una vía iterativa para el [análisis de componentes principales](analisis-componentes-principales.md). Oja converge al autovector principal descrito en [autovalores y autovectores](autovalores-y-autovectores.md), mientras que Sanger extiende la extracción a varias componentes. Ambas aparecen dentro del [aprendizaje no supervisado](aprendizaje-no-supervisado.md) y usan una neurona lineal relacionada con el [perceptrón simple](perceptron-simple.md).

## Sources

- [OFF-020, pp. 5, 7-17]
