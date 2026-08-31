---
title: "Autoencoders"
aliases: ["autoencoder", "autoasociador", "VAE", "variational autoencoder"]
sources: ["OFF-001", "EXT-001"]
related: ["aprendizaje-no-supervisado", "aprendizaje-profundo", "redes-generativas-adversarias"]
prerequisites: ["aprendizaje-profundo", "optimizacion-matematica"]
---

# Autoencoders

## Overview

Un autoencoder aprende a codificar una entrada en una representación latente y a reconstruirla mediante un decoder. La reconstrucción permite aprender estructura sin etiquetas y puede usarse para representación, detección de outliers o generación. [OFF-001, pp. 153-160]

## Core concepts

- El encoder transforma la entrada en un código de menor dimensión y el decoder intenta recuperar la entrada original. [OFF-001, pp. 153-155]
- Un autoencoder lineal se relaciona con reducción de dimensionalidad; variantes denoising, contractive y sparse agregan objetivos o restricciones que cambian la representación aprendida. [OFF-001, pp. 154, 156-157]
- Un autoencoder generativo permite explorar el espacio latente para producir muestras nuevas; un VAE modela una distribución latente y usa inferencia variacional. [OFF-001, pp. 158-162]
- El reparameterization trick permite propagar gradientes a través de una capa estocástica del VAE. [OFF-001, pp. 160-162]

## How it works

La entrada pasa por el encoder, se obtiene un código y el decoder produce una reconstrucción. El entrenamiento minimiza una función asociada al error de reconstrucción; en el VAE se incorpora además el objetivo variacional sobre la distribución latente. [OFF-001, pp. 153-162]

## Relationships

Los autoencoders son un caso de [aprendizaje no supervisado](aprendizaje-no-supervisado.md) y una familia de [aprendizaje profundo](aprendizaje-profundo.md). Las [GAN](redes-generativas-adversarias.md) también son modelos generativos, pero usan un juego adversarial en lugar de reconstrucción.

## Exam relevance

Se debe distinguir encoder, decoder, espacio latente, autoencoder denoising/sparse/contractive y VAE, además de explicar por qué el trick de reparametrización es útil. [OFF-001, pp. 153-162]

## Sources

- [OFF-001, pp. 153-162]
- [EXT-001, pp. 41-45]
