---
title: "Transformers"
aliases: ["Transformer", "attention", "self-attention", "embedding", "Encoder", "Decoder", "multi-head attention", "positional encoding"]
sources: ["OFF-001", "EXT-001", "OFF-024"]
related: ["aprendizaje-profundo", "autoencoders", "aprendizaje-supervisado"]
prerequisites: ["aprendizaje-profundo", "aprendizaje-supervisado"]
---

# Transformers

## Panorama general

Los Transformers son una arquitectura para procesar secuencias de tokens, especialmente texto. Su mecanismo central es la atención, que permite relacionar un token con otros tokens relevantes de la secuencia. [OFF-001, pp. 193-197]

## Conceptos centrales

- La arquitectura general distingue Encoder y Decoder: el Encoder procesa entradas y el Decoder usa la entrada y la salida producida hasta ese momento. [OFF-001, pp. 195-196]
- La atención calcula relaciones entre Query, Key y Value; mediante productos, pesos y Softmax produce una combinación ponderada de valores. [OFF-001, pp. 196-198]
- En el Encoder la atención puede considerar la entrada completa; en el Decoder se restringe a tokens previos de la secuencia de salida. [OFF-001, p. 196]
- Tokenization divide el texto en componentes y los embeddings codifican tokens como números para que la red pueda procesarlos. [OFF-001, pp. 199-200]
- El apunte los presenta como una respuesta a dificultades de redes recurrentes y LSTM relacionadas con secuencias largas y gradientes vanishing/exploding. [OFF-001, pp. 193-195]

### Atención escalada y cálculo matricial

Los embeddings de entrada se agrupan en `X`. Tres matrices de pesos aprendidas producen `Q = XW_Q`, `K = XW_K` y `V = XW_V`. Para cada token se compara su query con las keys mediante productos escalares, se divide por `√d_k`, se normalizan conjuntamente los scores con Softmax y se obtiene una suma ponderada de los values. La formulación matricial de la clase es:

\[
Z=\operatorname{softmax}\!\left(\frac{QK^T}{\sqrt{d_k}}\right)V.
\]

`d_k` es la dimensión de las keys. El resultado es una representación contextual por token: sus pesos determinan cuánto aporta cada value. [OFF-024, pp. 12-16]

La notación gráfica de las pp. 14-15 escribe Softmax al lado de cada score individual. Aquí se explicita que la normalización se aplica sobre el conjunto de scores de una query, en correspondencia con la fórmula matricial de la p. 16. [OFF-024, pp. 14-16]

### Múltiples cabezas, posición y bloques

- **Multi-head attention:** utiliza varios conjuntos de proyecciones Q, K y V, llamados cabezas, para atender a distintas posiciones simultáneamente. Los diagramas ilustran diferentes relaciones capturadas por las cabezas. [OFF-024, pp. 18-19]
- **Positional encoding:** agrega a cada embedding un vector que representa la posición. La variante ilustrada usa `PE(pos,2i) = sin(pos/10000^(2i/d))` y `PE(pos,2i+1) = cos(pos/10000^(2i/d))`, donde `d` es la dimensión del embedding y `i` identifica el par de componentes. [OFF-024, pp. 20-21]
- **Encoder:** combina self-attention y una red feed-forward. Los tokens se relacionan en la atención y pasan por la misma transformación feed-forward aplicada a cada posición; esos caminos pueden procesarse en paralelo. [OFF-024, pp. 9, 17]
- **Decoder:** además de atender a los tokens previos de su salida, incluye atención encoder-decoder para usar la representación de entrada. La última salida pasa por una capa lineal que produce logits del vocabulario y por Softmax para obtener probabilidades. [OFF-024, pp. 9-10, 22-23]

La dimensión 512 de los embeddings corresponde al ejemplo presentado por la clase; no es una condición de la definición general de atención que expresa su fórmula. [OFF-024, pp. 11, 16]

## Funcionamiento

Se tokeniza la entrada, se generan embeddings, se calculan puntuaciones de atención y se combinan los Values con esos pesos. El Decoder termina con una capa lineal y Softmax para seleccionar el próximo token; el entrenamiento ajusta los pesos mediante ejemplos supervisados. [OFF-001, pp. 196-200]

### Ejemplo de entrenamiento y aplicaciones

Para traducir «gracias» a «thanks», la clase fija un vocabulario de salida y compara la distribución predicha con una distribución objetivo que asigna toda la probabilidad al token correcto. La retropropagación ajusta los pesos a partir de esa diferencia. Las diapositivas también señalan el costo computacional del entrenamiento. [OFF-024, pp. 25-28]

Los ejemplos del material incluyen generación y completado de texto, traducción, procesamiento de imágenes, reconocimiento de audio y generación musical. Las capturas de servicios y las listas de modelos corresponden a la presentación; no constituyen un catálogo actualizado de productos. [OFF-024, pp. 30-55]

## Relaciones

Los Transformers son una arquitectura de [aprendizaje profundo](aprendizaje-profundo.md) para secuencias y comparten con otras redes el ajuste por [aprendizaje supervisado](aprendizaje-supervisado.md). Su atención puede verse como un promedio ponderado por similitud. [OFF-001, pp. 197-198]

## Fuentes

- [OFF-001, pp. 193-200]
- [EXT-001, pp. 49-51]
- [OFF-024, pp. 5-28, 30-55]
