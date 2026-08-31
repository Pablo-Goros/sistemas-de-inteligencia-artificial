---
title: "Transformers"
aliases: ["Transformer", "attention", "self-attention", "embedding", "Encoder", "Decoder"]
sources: ["OFF-001", "EXT-001"]
related: ["aprendizaje-profundo", "autoencoders", "aprendizaje-supervisado"]
prerequisites: ["aprendizaje-profundo", "aprendizaje-supervisado"]
---

# Transformers

## Overview

Los Transformers son una arquitectura para procesar secuencias de tokens, especialmente texto. Su mecanismo central es la atención, que permite relacionar un token con otros tokens relevantes de la secuencia. [OFF-001, pp. 193-197]

## Core concepts

- La arquitectura general distingue Encoder y Decoder: el Encoder procesa entradas y el Decoder usa la entrada y la salida producida hasta ese momento. [OFF-001, pp. 195-196]
- La atención calcula relaciones entre Query, Key y Value; mediante productos, pesos y Softmax produce una combinación ponderada de valores. [OFF-001, pp. 196-198]
- En el Encoder la atención puede considerar la entrada completa; en el Decoder se restringe a tokens previos de la secuencia de salida. [OFF-001, p. 196]
- Tokenization divide el texto en componentes y los embeddings codifican tokens como números para que la red pueda procesarlos. [OFF-001, pp. 199-200]
- El apunte los presenta como una respuesta a dificultades de redes recurrentes y LSTM relacionadas con secuencias largas y gradientes vanishing/exploding. [OFF-001, pp. 193-195]

## How it works

Se tokeniza la entrada, se generan embeddings, se calculan puntuaciones de atención y se combinan los Values con esos pesos. El Decoder termina con una capa lineal y Softmax para seleccionar el próximo token; el entrenamiento ajusta los pesos mediante ejemplos supervisados. [OFF-001, pp. 196-200]

## Relationships

Los Transformers son una arquitectura de [aprendizaje profundo](aprendizaje-profundo.md) para secuencias y comparten con otras redes el ajuste por [aprendizaje supervisado](aprendizaje-supervisado.md). Su atención puede verse como un promedio ponderado por similitud. [OFF-001, pp. 197-198]

## Exam relevance

Conviene explicar Encoder/Decoder, Query-Key-Value, Softmax, tokenización, embedding y la diferencia entre atención del Encoder y del Decoder. [OFF-001, pp. 195-200]

## Sources

- [OFF-001, pp. 193-200]
- [EXT-001, pp. 49-51]
