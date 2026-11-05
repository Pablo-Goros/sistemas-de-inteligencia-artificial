---
title: "Autoencoders variacionales"
aliases: ["VAE", "variational autoencoder", "inferencia variacional", "ELBO", "reparameterization trick", "truco de reparametrización"]
sources: ["OFF-001", "OFF-016", "OFF-017", "OFF-019"]
related: ["regularizacion", "muestreo-de-distribuciones", "retropropagacion"]
prerequisites: ["autoencoders", "teoria-de-la-informacion", "optimizacion-matematica"]
---

# Autoencoders variacionales

## Panorama general

Un VAE combina un modelo generativo estimado mediante inferencia variacional con dos redes acopladas: un encoder y un decoder. El encoder estima parámetros de una distribución de códigos; se muestrea un código y el decoder lo convierte en una reconstrucción. [OFF-016, pp. 55-61, 71-74]

## Conceptos centrales

### Inferencia y distribuciones

La inferencia variacional aproxima una distribución desconocida mediante una familia conocida cuyos parámetros se optimizan. Se distinguen la posterior `pθ(z|x)`, su aproximación `qφ(z|x)`, el prior `p(z)` y el modelo de reconstrucción `pθ(x|z)`. Los parámetros `φ` y `θ` corresponden a los pesos del encoder y del decoder. La elección presentada usa prior normal estándar y aproximación gaussiana con covarianza diagonal. [OFF-016, pp. 58-62, 70-74]

### Cota variacional y pérdida

La derivación descompone la log-verosimilitud en una cota inferior y una divergencia no negativa. Explicitando el condicionamiento en `x`, que las diapositivas a veces omiten:

\[
\log p_\theta(x)
=D_{KL}(q_\phi(z|x)\|p_\theta(z|x))+\mathcal L(\theta,\phi;x),
\]

\[
\mathcal L
=\mathbb E_{q_\phi(z|x)}[\log p_\theta(x|z)]
-D_{KL}(q_\phi(z|x)\|p(z))\leq\log p_\theta(x).
\]

Para un modelo generativo fijo, aumentar la cota reduce la divergencia respecto de la posterior. El entrenamiento del VAE ajusta conjuntamente ambos modelos maximizando esa cota, o minimizando su negativo. La pérdida contiene reconstrucción y un regularizador que compara la distribución del encoder con el prior; esa comparación es distinta de la divergencia respecto de la posterior de la primera identidad. [OFF-016, pp. 63-74]

Con covarianza diagonal, el regularizador gaussiano es:

\[
D_{KL}=\frac12\sum_i(\sigma_i^2+\mu_i^2-1-\log\sigma_i^2).
\]

Definiendo `ℓ_i = log σ_i²`, se reescribe como `½ Σ_i(exp(ℓ_i) + μ_i² - 1 - ℓ_i)`. Aquí se distinguen varianza y log-varianza; la diapositiva reutiliza `Σ` para la cantidad y su parametrización exponencial. [OFF-016, pp. 76-78]

### Reparametrización y gradientes

El truco separa el ruido aleatorio de la transformación parametrizada. Para una gaussiana diagonal, usando `σ` como desvío estándar:

\[
\epsilon\sim\mathcal N(0,I),\qquad
z=\mu(x)+\sigma(x)\odot\epsilon.
\]

Para una realización fija de `ε`, las derivadas son `∂z/∂μ = 1` y `∂z/∂σ = ε`, componente a componente. El decoder recibe el gradiente de reconstrucción; el encoder recibe tanto esa contribución a través de la reparametrización como la derivada del regularizador respecto de sus parámetros de distribución. [OFF-016, pp. 80-89; OFF-017, p. 12]

## Funcionamiento

1. Obtener del encoder los parámetros de `qφ(z|x)` para una entrada real.
2. Muestrear ruido normal estándar y transformarlo mediante la reparametrización.
3. Pasar el código al decoder y calcular la reconstrucción.
4. Evaluar reconstrucción y KL, y retropropagar las contribuciones correspondientes. [OFF-016, pp. 72-89]

## Precauciones de lectura de las fuentes

- **Escala frente a covarianza:** las pp. 45 y 80-83 escriben `ε ⊙ Σ + μ`, mientras las pp. 74 y 76 usan `Σ` como covarianza. Las pp. 86-87 emplean `σ` y las derivadas anteriores. Aquí se explicita la escala mediante `σ`; si se parte de varianzas diagonales, se usa su raíz, y si se parte de log-varianzas, `exp(ℓ/2)`. Es una normalización algebraica para compatibilizar esas expresiones, no una transcripción literal. [OFF-016, pp. 45, 74, 76-83, 86-87; OFF-017, p. 12]
- **Qué se muestrea:** la p. 80 dice que se toma `z` de `N(0,I)` y lo equipara a transformar ruido con media y escala del encoder. En el procedimiento de las pp. 72-74, el ruido base es normal estándar y el código transformado corresponde a `qφ(z|x)`; ambas variables deben distinguirse. [OFF-016, pp. 72-74, 80]
- **Signo de la gaussiana:** la p. 75 imprime una exponencial cuadrática positiva y una proporcionalidad positiva para el logaritmo. Esto es inconsistente con el término de error que se minimiza en las pp. 73 y 78; esa fórmula no se reproduce como una densidad válida. [OFF-016, pp. 73, 75, 78]

## Aplicación práctica: extensión variacional

La segunda parte del TP5 exige extender el autoencoder anterior a un VAE. Se debe elegir o construir un conjunto de datos nuevo (los emojis son un ejemplo propuesto, no una elección obligatoria), incorporar el esquema variacional para abordar la representación latente y generar una muestra nueva que pueda juzgarse como perteneciente al conjunto de datos elegido. La consigna solicita una valoración de la muestra generada, sin especificar una métrica cuantitativa de calidad generativa. [OFF-019, p. 1, §2.a-c]

La condición explícita de espacio latente bidimensional y el objetivo de un píxel incorrecto aparecen en la parte del autoencoder básico de caracteres. El apartado variacional no vuelve a establecer esas condiciones para el nuevo dataset; no corresponde trasladar automáticamente el criterio de píxeles de los caracteres a cualquier dato elegido. [OFF-019, p. 1, §§1.a y 2]

## Relaciones

Extiende los [autoencoders](autoencoders.md) con distribuciones latentes y usa [teoría de la información](teoria-de-la-informacion.md) para construir el objetivo. El [muestreo](muestreo-de-distribuciones.md) explica cómo obtener realizaciones aleatorias y la [retropropagación](retropropagacion.md) permite ajustar las dos redes. [OFF-016, pp. 39-53, 63-89]

## Fuentes

- [OFF-016, pp. 39-89]
- [OFF-017, pp. 10-20]
- [OFF-001, pp. 158-162]
- [OFF-019, p. 1, §2]
