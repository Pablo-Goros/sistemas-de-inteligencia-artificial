---
title: "Redes generativas adversarias"
aliases: ["GAN", "Generative Adversarial Network", "generador", "discriminador", "colapso modal"]
sources: ["OFF-001", "EXT-001", "OFF-020"]
related: ["aprendizaje-profundo", "autoencoders", "optimizacion-matematica"]
prerequisites: ["aprendizaje-profundo", "optimizacion-matematica"]
---

# Redes generativas adversarias

## Overview

Una GAN contiene un Generador que produce muestras y un Discriminador que intenta distinguir muestras reales de generadas. Ambos se entrenan en oposición dentro de un juego minimax. [OFF-001, pp. 187-190]

## Core concepts

- El Generador recibe ruido y busca producir muestras cuya distribución se parezca a la de los datos originales. [OFF-001, pp. 187-189]
- El Discriminador clasifica muestras reales y artificiales; su objetivo es acertar, mientras que el del Generador es confundirlo. [OFF-001, pp. 188-189]
- El equilibrio ideal se interpreta como un equilibrio de Nash en el que el discriminador no puede distinguir mejor que al azar y la distribución generada coincide con la de los datos. [OFF-001, p. 190]
- El colapso modal ocurre cuando el Generador produce poca variedad y se concentra en soluciones que engañan al Discriminador. El orden y equilibrio del entrenamiento son críticos. [OFF-001, p. 190]

## How it works

Se alterna el entrenamiento del Discriminador y del Generador. El primero maximiza su capacidad de clasificación; el segundo minimiza la capacidad del discriminador para identificar sus muestras. [OFF-001, pp. 188-190]

## Aplicación práctica: temas de ensayo y debate

El TP6 incluye las GAN entre las áreas posibles para un ensayo de postura personal y propone lecturas sobre aplicaciones, generación de contenido sintético y escasez de datos. La consigna ofrece esos disparadores para elegir un tema; no exige entrenar una GAN ni establece que los datos sintéticos resuelvan siempre la falta de datos. Las condiciones del ensayo y debate se resumen en [introducción a la IA](introduccion-inteligencia-artificial.md). [OFF-020, pp. 2, 5]

## Relationships

Las GAN son modelos generativos de [aprendizaje profundo](aprendizaje-profundo.md). Los [autoencoders](autoencoders.md) también modelan representaciones y generación, pero parten de una reconstrucción y no de dos redes adversarias.

## Exam relevance

Hay que identificar los roles de Generador y Discriminador, formular la intuición minimax y explicar equilibrio y colapso modal. [OFF-001, pp. 187-190]

## Sources

- [OFF-001, pp. 187-190]
- [EXT-001, pp. 52-53]
- [OFF-020, pp. 2, 5]
