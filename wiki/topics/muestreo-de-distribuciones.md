---
title: "Muestreo de distribuciones"
aliases: ["inverse transform sampling", "inverse sampling theorem", "transformada inversa", "muestreo aleatorio"]
sources: ["OFF-016", "OFF-017"]
related: ["autoencoders-variacionales", "teoria-de-la-informacion"]
prerequisites: []
---

# Muestreo de distribuciones

## Panorama general

El problema consiste en transformar números pseudoaleatorios uniformes para obtener muestras con una distribución deseada. El material lo introduce como preparación para construir funciones estocásticas con redes neuronales y distribuciones latentes. [OFF-017, pp. 5-15; OFF-016, pp. 39-48]

## Conceptos centrales

La densidad (PDF) y la función de distribución acumulada (CDF) cumplen papeles distintos: el método de inversión transforma una muestra uniforme usando la inversa de la CDF, no la inversa de la densidad. Si `U ~ Uniforme(0,1)` y la CDF `F` es invertible, `X = F⁻¹(U)` tiene CDF `F`. La formulación general presentada usa `X = inf{x : F(x) ≥ U}`. [OFF-017, pp. 5-8; OFF-016, pp. 39-41]

## Funcionamiento

1. Obtener una muestra uniforme `u`.
2. Localizarla en el eje de probabilidades acumuladas de `F`.
3. Recuperar el valor `x` asociado mediante la inversa o inversa generalizada.
4. Repetir el procedimiento. Los diagramas muestran el vínculo entre densidad, acumulada e inversión. [OFF-017, pp. 5-8]

## Otras construcciones y alcance

El repaso invoca el teorema central del límite para aproximar una normal mediante muchas muestras uniformes. Escribe media `n/2` y varianza `n/12`, pero no explicita en esa diapositiva la suma ni la independencia de las muestras; no debe leerse como que una muestra uniforme aislada se vuelve normal. [OFF-017, p. 9; OFF-016, p. 42]

Las redes estocásticas del material parametrizan una distribución condicional y utilizan una entrada aleatoria adicional. La reparametrización gaussiana del [VAE](autoencoders-variacionales.md) transforma ruido base con una media y una escala aprendidas; no exige calcular una CDF inversa en cada paso de entrenamiento. [OFF-017, pp. 11-15; OFF-016, pp. 72-83]

## Fuentes

- [OFF-017, pp. 5-15]
- [OFF-016, pp. 39-48, 72-83]
