---
title: "Teoría de la información"
aliases: ["information theory", "entropía", "información mutua", "cross entropy", "entropía cruzada", "divergencia KL", "Kullback-Leibler", "binary cross entropy"]
sources: ["OFF-016", "OFF-017"]
related: ["aprendizaje-supervisado", "autoencoders-variacionales", "regularizacion"]
prerequisites: []
---

# Teoría de la información

## Panorama general

El repaso introduce medidas para cuantificar información de eventos, incertidumbre de distribuciones y diferencias entre distribuciones. Las conecta con pérdidas de clasificación y con el objetivo variacional de los VAE. [OFF-017, pp. 16-20; OFF-016, pp. 49-53, 62-73]

## Conceptos centrales

### Información, entropía e información mutua

Para un evento de probabilidad `p(x)`, su información es `I(x) = -log p(x)`: un evento menos probable aporta más información. La entropía es el promedio `H(X) = -Σ_x p(x) log p(x)`. Es cero en certeza y máxima para eventos equiprobables dentro del conjunto de resultados considerado. [OFF-017, pp. 16-17; OFF-016, pp. 49-50]

La entropía conjunta mide la incertidumbre del par de variables; la condicional satisface `H(X|Y) = H(X,Y) - H(Y)`. La información mutua puede escribirse como `I(X;Y) = H(Y) - H(Y|X)` o como la suma ponderada de `log[p(x,y)/(p(x)p(y))]`. [OFF-017, pp. 16-17]

### Entropía cruzada

Usando `q` para la distribución objetivo y `p` para la predicción, la entropía cruzada es `H_p(q) = -Σ_k q(y_k) log p(y_k)`. Para etiquetas binarias `y_i` y probabilidades predichas `p_i`, la versión promedio es:

\[
\operatorname{BCE}=-\frac1N\sum_{i=1}^N
\left[y_i\log p_i+(1-y_i)\log(1-p_i)\right].
\]

La clase la presenta como pérdida para un clasificador binario; asignar probabilidad uno a la etiqueta correcta da pérdida cero. [OFF-017, p. 18; OFF-016, p. 51]

### Divergencia de Kullback-Leibler

La identidad con entropía cruzada y entropía da:

\[
D_{KL}(q\|p)=H_p(q)-H(q)
=\sum_xq(x)\log\frac{q(x)}{p(x)}.
\]

Las propiedades listadas son no negatividad, `D_KL(q||q) = 0` y falta de simetría en general. El material aclara que no es una norma en sentido riguroso. En el VAE sirve para comparar distribuciones y construir un término regularizador. [OFF-017, pp. 19-20; OFF-016, pp. 62-73]

## Inconsistencias de las diapositivas

Las pp. 19-20 de OFF-017 y las pp. 52-53 de OFF-016 imprimen `-Σ q log(q/p)`, pero enuncian simultáneamente `KL = H_p(q) - H(q) ≥ 0`. El signo de la fórmula impresa contradice esa identidad. Aquí se adopta la expresión que resulta de restar las entropías y que coincide con la derivación posterior `-Σ q log(p/q)` de OFF-016. Los originales y sus extractos conservan la expresión impresa. [OFF-017, pp. 18-20; OFF-016, pp. 51-53, 62-65]

La cota superior `log(2k+1)` aparece sin definir `k` en las diapositivas de entropía; por eso no se adopta como una cota general con significado determinado. [OFF-017, p. 17; OFF-016, p. 50]

## Relaciones

La entropía cruzada se aplica al [aprendizaje supervisado](aprendizaje-supervisado.md). La KL conecta reconstrucción y [regularización](regularizacion.md) en los [autoencoders variacionales](autoencoders-variacionales.md). [OFF-017, p. 18; OFF-016, pp. 69-78]

## Fuentes

- [OFF-017, pp. 16-20]
- [OFF-016, pp. 49-53, 62-78]
