---
title: "Autoencoders"
aliases: ["autoencoder", "autoasociador", "DAE", "CAE", "SAE"]
sources: ["OFF-001", "EXT-001", "OFF-022", "OFF-023"]
related: ["aprendizaje-no-supervisado", "aprendizaje-profundo", "redes-generativas-adversarias", "autoencoders-variacionales", "regularizacion"]
prerequisites: ["aprendizaje-profundo", "optimizacion-matematica"]
---

# Autoencoders

## Panorama general

Un autoencoder aprende a codificar una entrada en una representación latente y a reconstruirla mediante un decoder. La reconstrucción permite aprender estructura sin etiquetas y puede usarse para representación, detección de outliers o generación. [OFF-001, pp. 153-160]

## Conceptos centrales

- El encoder transforma la entrada en un código y el decoder intenta recuperar la entrada original. Un cuello de botella de menor dimensión impone compresión, pero otras variantes pueden usar más dimensiones y restricciones diferentes. [OFF-001, pp. 153-155; OFF-022, pp. 6, 26]
- Un autoencoder lineal se relaciona con reducción de dimensionalidad; variantes denoising, contractive y sparse agregan objetivos o restricciones que cambian la representación aprendida. [OFF-001, pp. 154, 156-157]
- Un autoencoder generativo permite explorar el espacio latente para producir muestras nuevas; un VAE modela una distribución latente y usa inferencia variacional. [OFF-001, pp. 158-162]
- El reparameterization trick permite propagar gradientes a través de una capa estocástica del VAE. [OFF-001, pp. 160-162]

### Relación con PCA y SVD

La clase relaciona la reconstrucción lineal de rango reducido con SVD y PCA. Para datos centrados, la matriz de covarianza es `XᵀX/(n-1)`; sus autovectores coinciden con los vectores singulares derechos y sus autovalores son `s_i²/(n-1)`. En la construcción con base ortonormal que presenta la derivación, el código coincide con las proyecciones de PCA. Las activaciones no lineales permiten pensar al autoencoder como una extensión no lineal de la reducción de dimensionalidad. [OFF-022, pp. 8-16; OFF-023, pp. 2-3]

**Alcance y notación:** el lema sobre PCA de las pp. 10 y 15 debe leerse dentro de esa construcción con datos centrados y base ortonormal. La p. 9 escribe `X ≈ ZVᵀ` pero asigna a `V` dimensiones `k × d`: con `Z` de `n × k`, esas dimensiones corresponden al factor decoder completo, no al factor antes de transponer. Esta observación surge de comprobar las dimensiones indicadas en la misma diapositiva. [OFF-022, pp. 9-15]

### Variantes y usos

| Variante | Restricción o procedimiento | Referencia |
| --- | --- | --- |
| Denoising (DAE) | Recibe una versión contaminada y busca reconstruir el dato limpio. | [OFF-022, pp. 20-22] |
| Contractive (CAE) | Agrega una penalización para reducir la sensibilidad de la representación a cambios de la entrada. | [OFF-022, pp. 24-25] |
| Sparse (SAE) | Favorece activaciones nulas; la clase presenta un código de mayor dimensión restringido por esparsidad. | [OFF-022, p. 26] |

La clase desarrolla compresión y detección de outliers midiendo diferencias entre entrada y reconstrucción; no fija un umbral universal de anomalía. Para generar muestras propone explorar coordenadas del espacio latente y usar el decoder, pero advierte que se necesita estructura estadística para obtener muestras válidas al recorrerlo. Esto motiva los [VAE](autoencoders-variacionales.md). [OFF-022, pp. 18-19, 28-38]

## Funcionamiento

La entrada pasa por el encoder, se obtiene un código y el decoder produce una reconstrucción. El entrenamiento minimiza una función asociada al error de reconstrucción; en el VAE se incorpora además el objetivo variacional sobre la distribución latente. [OFF-001, pp. 153-162]

En la formulación inicial de la clase, `Z = f(X)`, `X' = g(Z)` y `L(X, X') = ||X - X'||²`. Para cada entrada `X`, se usa ese mismo patrón como salida esperada y se ajustan los pesos con un método de aprendizaje de MLP. El cuello de botella u otras restricciones fuerzan una representación útil en lugar de limitarse a copiar sin restricciones. [OFF-022, pp. 3-6]

En un DAE se modela el ruido, por ejemplo gaussiano o salt-and-pepper, y se construye una entrada contaminada `X̃`. El par de entrenamiento es `(X̃, X)`: el objetivo conserva el patrón original sin ruido. [OFF-022, p. 22]

## Relaciones

Los autoencoders son un caso de [aprendizaje no supervisado](aprendizaje-no-supervisado.md) y una familia de [aprendizaje profundo](aprendizaje-profundo.md). Las [GAN](redes-generativas-adversarias.md) también son modelos generativos, pero usan un juego adversarial en lugar de reconstrucción.

Las restricciones de las variantes se vinculan con [regularización](regularizacion.md). La inferencia variacional, la pérdida probabilística y los gradientes de la reparametrización se desarrollan en [autoencoders variacionales](autoencoders-variacionales.md). [OFF-022, pp. 23-26, 55-89]

## Fuentes

- [OFF-001, pp. 153-162]
- [EXT-001, pp. 41-45]
- [OFF-022, pp. 2-38, 55-89]
- [OFF-023, pp. 2-4]
