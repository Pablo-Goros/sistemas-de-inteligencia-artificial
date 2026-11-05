---
title: "Regularización"
aliases: ["regularization", "control del sobreajuste", "weight decay"]
sources: ["OFF-014", "OFF-015", "OFF-016", "OFF-017"]
related: ["evaluacion-de-modelos", "aprendizaje-supervisado", "optimizacion-matematica", "aprendizaje-profundo", "autoencoders", "autoencoders-variacionales"]
prerequisites: ["aprendizaje-supervisado", "evaluacion-de-modelos"]
---

# Regularización

## Panorama general

La regularización reúne técnicas para reducir el error de validación o prueba y mejorar la generalización. La clase la introduce como respuesta a la brecha entre el error de entrenamiento y el de evaluación. [OFF-015, pp. 5-7]

## Conceptos centrales

La capacidad de un modelo es su potencial para aproximar distintas funciones. Puede modificarse mediante la elección del modelo, su arquitectura o las características de entrada. Una capacidad insuficiente puede causar subajuste; una capacidad excesiva respecto de los datos puede favorecer sobreajuste. [OFF-015, pp. 8-13]

La clase desarrolla tres técnicas:

- *Early stopping*: detener el entrenamiento cuando el error de validación deja de mejorar. La curva ilustrada muestra que puede seguir bajando el error de entrenamiento mientras el de validación vuelve a subir. [OFF-015, p. 14]
- *Data augmentation*: generar variantes de ejemplos de entrenamiento, por ejemplo con ruido gaussiano, rotaciones, traslaciones o cambios de escala para imágenes. Las transformaciones deben preservar el significado de los datos. [OFF-015, pp. 15-18]
- Penalización L2 o *weight decay*: sumar al costo una penalización proporcional a la norma L2 cuadrada de los pesos, `Ereg(w) = E(w) + (lambda/2) ||w||^2`. El gradiente agrega el término `lambda w`, que empuja los pesos hacia valores menores. [OFF-015, pp. 19-24]

La clase menciona además dropout, ensambles, aprendizaje semi-supervisado y entrenamiento adversarial como otras técnicas, sin desarrollarlas en detalle. [OFF-015, p. 26]

### Restricciones de representación y regularización probabilística

Las clases de autoencoders y repaso presentan el esquema `J = L + λR`: una penalización adicional restringe las soluciones y `λ` controla su importancia relativa. En los [autoencoders](autoencoders.md), la penalización contractiva reduce sensibilidad a la entrada y la sparse favorece activaciones nulas. En los [VAE](autoencoders-variacionales.md), el objetivo derivado incorpora una KL entre la distribución del encoder y el prior, además de reconstrucción. Son restricciones sobre representaciones o distribuciones, diferentes de penalizar directamente la magnitud de los pesos. [OFF-016, pp. 23-26, 69-78; OFF-017, p. 4]

## Relaciones

La [evaluación de modelos](evaluacion-de-modelos.md) permite observar la brecha entre entrenamiento y validación que motiva estas técnicas. La penalización L2 modifica la función objetivo que minimiza la [optimización matemática](optimizacion-matematica.md).

## Relevancia para evaluaciones

La clase incluye regularización entre los contenidos de repaso y pregunta cómo reconocer la capacidad del modelo, el subajuste y el sobreajuste. Esto respalda estudiar la relación entre capacidad y generalización y explicar las técnicas presentadas; no se especifica una evaluación particular. [OFF-015, pp. 2, 8-13]

## Fuentes

- [OFF-015, pp. 2-26]
- [OFF-016, pp. 23-26, 69-78]
- [OFF-017, p. 4]
