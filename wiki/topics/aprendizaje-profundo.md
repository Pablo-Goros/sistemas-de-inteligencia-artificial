---
title: "Aprendizaje profundo"
aliases: ["deep learning", "DL", "aprendizaje de representación"]
sources: ["OFF-001", "EXT-001", "OFF-021"]
related: ["redes-neuronales-recurrentes", "modelos-de-difusion", "aprendizaje-supervisado", "autoencoders", "redes-neuronales-convolucionales", "redes-generativas-adversarias", "transformers"]
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

## Profundidad y dificultades de entrenamiento

La presentación organiza el aprendizaje profundo en cuatro pilares: composición de múltiples niveles, aprendizaje de representaciones, conjuntos de datos masivos y estandarizados, y GPU. La profundidad favorece la composición de características con valor semántico intermedio. [OFF-021, pp. 33, 107]

La capacidad de aproximar funciones con una capa oculta no garantiza que una red sea fácil de entrenar o que generalice bien. La presentación motiva arquitecturas profundas mediante estructura composicional, localidad a distintas escalas e invariancia a desplazamientos. También destaca el desvanecimiento o explosión de gradientes como dificultad de asignar crédito a lo largo de muchas transformaciones. [OFF-021, pp. 38-40]

Entre los enfoques presentados para afrontar estas dificultades figuran el preentrenamiento no supervisado por capas, las celdas LSTM, la inicialización Xavier, dropout y optimización sin Hessiano explícito. La diapositiva los enumera, sin establecer que sean intercambiables ni una solución universal. [OFF-021, p. 42]

Las [redes recurrentes](redes-neuronales-recurrentes.md) incorporan estado temporal; los [modelos de difusión](modelos-de-difusion.md) generan mediante un proceso inverso de eliminación de ruido. [OFF-021, pp. 55-57, 69-71]

## Relationships

Los [autoencoders](autoencoders.md) aprenden codificaciones y reconstrucciones; las [redes convolucionales](redes-neuronales-convolucionales.md) explotan estructura espacial; las [GAN](redes-generativas-adversarias.md) generan mediante competencia; los [Transformers](transformers.md) procesan secuencias con atención.

## Exam relevance

Es importante explicar qué agrega la profundidad, qué significa aprender una representación y por qué datos y hardware condicionan el aprendizaje profundo. [OFF-001, pp. 145-152]

## Sources

- [OFF-001, pp. 145-152]
- [EXT-001, pp. 40-48]
- [OFF-021, pp. 33, 38-42, 55-57, 69-71, 107]
