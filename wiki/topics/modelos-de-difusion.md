---
title: "Modelos de difusión"
aliases: ["diffusion models", "difusión latente", "Stable Diffusion", "latent diffusion"]
sources: ["OFF-021"]
related: ["aprendizaje-profundo", "autoencoders", "redes-neuronales-convolucionales", "transformers", "redes-generativas-adversarias"]
prerequisites: ["aprendizaje-profundo", "autoencoders"]
---

# Modelos de difusión

## Overview

Los modelos de difusión son modelos generativos cuyo esquema distingue un proceso que transforma datos hacia ruido y un proceso inverso que permite producir muestras. La presentación introduce la generación de imágenes y luego la difusión en un espacio latente. [OFF-021, pp. 68-71]

## Core concepts

- **Proceso directo e inverso:** el diagrama muestra la secuencia entre una imagen y estados progresivamente ruidosos, junto con transiciones inversas de reconstrucción. [OFF-021, p. 69]
- **Espacio latente:** un VAE convierte entre imágenes y representaciones latentes, donde se realiza la difusión. [OFF-021, pp. 70-71]
- **Condicionamiento:** un codificador produce un embedding que guía a una U-Net encargada de revertir la difusión. En la arquitectura presentada, el codificador de condición utiliza CLIP. [OFF-021, p. 71]

## How it works

En la generación latente ilustrada se parte de ruido gaussiano en el espacio latente, se aplica repetidamente una U-Net condicionada para eliminar ruido y se decodifica el resultado a imagen con el VAE. El esquema separa la representación de la imagen, el proceso de eliminación de ruido y la representación de la condición. [OFF-021, pp. 70-71]

La presentación muestra cross-attention para vincular características de imagen con el embedding de contexto y un codificador CLIP con ramas de texto e imagen. No desarrolla aquí una función de pérdida completa de difusión ni un algoritmo numérico de muestreo. [OFF-021, pp. 73-74]

## Relationships

Los [autoencoders](autoencoders.md) proporcionan la conversión al espacio latente. La U-Net pertenece a las [redes convolucionales](redes-neuronales-convolucionales.md), mientras que la atención conecta con [Transformers](transformers.md). La presentación trata también las [GAN](redes-generativas-adversarias.md), cuyo mecanismo de entrenamiento es adversarial. [OFF-021, pp. 61, 66-74]

## Sources

- [OFF-021, pp. 68-74]
