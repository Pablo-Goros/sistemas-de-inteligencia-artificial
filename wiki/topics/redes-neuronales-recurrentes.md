---
title: "Redes neuronales recurrentes"
aliases: ["RNN", "recurrent neural network", "LSTM", "long short term memory"]
sources: ["OFF-021"]
related: ["aprendizaje-profundo", "retropropagacion", "transformers"]
prerequisites: ["perceptron-multicapa", "retropropagacion"]
---

# Redes neuronales recurrentes

## Overview

Una red recurrente procesa entradas sucesivas manteniendo un estado oculto. La presentación muestra cómo el siguiente estado depende tanto de la entrada como del estado previo; al desplegar la red en el tiempo se hace visible esta cadena de dependencias. [OFF-021, pp. 55-56]

## Core concepts

- **Estado oculto:** resume información que vuelve a intervenir en la transición siguiente. El esquema usa una transformación con `tanh` y matrices para entrada y recurrencia. [OFF-021, pp. 55-56]
- **Despliegue temporal:** representa la misma operación recurrente en distintos instantes, con conexiones entre estados consecutivos. [OFF-021, p. 56]
- **LSTM:** incorpora un estado de celda y compuertas de entrada, olvido y salida para controlar la combinación y exposición de información. La presentación la incluye entre los recursos para afrontar dificultades del aprendizaje profundo. [OFF-021, pp. 42, 57]

## How it works

En el esquema LSTM, una transformación `tanh` produce el candidato `g`; compuertas sigmoidales producen `i`, `f` y `o`. El estado de celda se actualiza como `s_t = s_(t-1) ∘ f + g ∘ i`, y el oculto como `h_t = tanh(s_t) ∘ o`. El símbolo `∘` representa productos componente a componente. Así, el olvido regula cuánto estado anterior conservar y la entrada cuánto candidato incorporar. [OFF-021, p. 57]

## Relationships

Las RNN y LSTM son arquitecturas de [aprendizaje profundo](aprendizaje-profundo.md). El problema de gradientes a lo largo de dependencias extensas conecta con la [retropropagación](retropropagacion.md). La presentación introduce luego los [Transformers](transformers.md) como otra familia, basada en atención. [OFF-021, pp. 40-42, 55-57, 66-67]

## Sources

- [OFF-021, pp. 40-42, 55-57, 66-67]
