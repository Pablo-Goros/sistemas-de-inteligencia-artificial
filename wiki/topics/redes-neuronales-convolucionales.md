---
title: "Redes neuronales convolucionales"
aliases: ["CNN", "convolutional neural network", "convolución", "pooling"]
sources: ["OFF-001", "EXT-001"]
related: ["aprendizaje-profundo", "aprendizaje-supervisado"]
prerequisites: ["aprendizaje-supervisado", "aprendizaje-profundo"]
---

# Redes neuronales convolucionales

## Overview

Una red neuronal convolucional (CNN) incorpora operaciones que explotan la estructura local de imágenes y otras señales. Sus capas detectan patrones y los combinan jerárquicamente antes de una salida de clasificación o regresión. [OFF-001, pp. 173-181]

## Core concepts

- La convolución aplica un kernel sobre regiones locales; padding controla el tratamiento de bordes y el tamaño espacial de la salida. [OFF-001, pp. 174-175]
- Las capas convolucionales aprenden filtros; pooling reduce la resolución y resume activaciones, y las capas finales conectadas con Softmax producen probabilidades de clase. [OFF-001, pp. 178-181]
- La retropropagación ajusta los filtros y el resto de parámetros según el error de salida. [OFF-001, p. 181]
- ResNet y UNet aparecen como arquitecturas reutilizables; las conexiones residuales y la organización encoder-decoder permiten construir redes profundas o tareas de segmentación. [OFF-001, pp. 183-185]

## How it works

La imagen atraviesa filtros locales, funciones de activación y pooling; las representaciones intermedias se vuelven progresivamente más abstractas y la parte final las transforma en una salida. El entrenamiento usa backpropagation para modificar los filtros. [OFF-001, pp. 178-183]

## Relationships

Las CNN son una especialización del [aprendizaje profundo](aprendizaje-profundo.md) y suelen entrenarse como modelos de [aprendizaje supervisado](aprendizaje-supervisado.md).

## Exam relevance

Conviene explicar kernel, convolución, padding, pooling, capas finales, backpropagation y la motivación de las conexiones residuales. [OFF-001, pp. 174-185]

## Sources

- [OFF-001, pp. 173-185]
- [EXT-001, pp. 46-48]
