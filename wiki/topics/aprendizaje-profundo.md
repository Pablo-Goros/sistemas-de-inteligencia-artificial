---
title: "Aprendizaje profundo"
aliases: ["deep learning", "DL", "aprendizaje de representación"]
sources: ["OFF-001", "EXT-001"]
related: ["aprendizaje-supervisado", "autoencoders", "redes-neuronales-convolucionales", "redes-generativas-adversarias", "transformers"]
prerequisites: ["aprendizaje-supervisado", "optimizacion-matematica"]
---

# Aprendizaje profundo

## Overview

El aprendizaje profundo utiliza redes neuronales con múltiples capas para aprender representaciones jerárquicas. El material de cátedra organiza su explicación alrededor de profundidad, aprendizaje de representación, datasets y GPUs. [OFF-001, pp. 145-152]

## Core concepts

- La profundidad permite componer transformaciones: capas tempranas pueden representar rasgos simples y capas posteriores rasgos más abstractos. [OFF-001, pp. 147-150]
- El aprendizaje de representación reduce la necesidad de diseñar manualmente todas las características de entrada. [OFF-001, p. 150]
- El desempeño práctico depende de datos y capacidad de cómputo; el apunte destaca datasets y GPUs como pilares del desarrollo moderno. [OFF-001, pp. 151-152]
- Autoencoders, CNN, GAN y Transformers son arquitecturas o familias especializadas que reutilizan entrenamiento por gradiente y representaciones aprendidas, pero resuelven tareas diferentes. [OFF-001, pp. 153-200]

## Relationships

Los [autoencoders](autoencoders.md) aprenden codificaciones y reconstrucciones; las [redes convolucionales](redes-neuronales-convolucionales.md) explotan estructura espacial; las [GAN](redes-generativas-adversarias.md) generan mediante competencia; los [Transformers](transformers.md) procesan secuencias con atención.

## Exam relevance

Es importante explicar qué agrega la profundidad, qué significa aprender una representación y por qué datos y hardware condicionan el aprendizaje profundo. [OFF-001, pp. 145-152]

## Sources

- [OFF-001, pp. 145-152]
- [EXT-001, pp. 40-48]
