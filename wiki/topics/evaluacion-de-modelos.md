---
title: "Evaluación de modelos"
aliases: ["métricas", "matriz de confusión", "sobreajuste", "cross-validation"]
sources: ["OFF-001", "OFF-010", "EXT-001"]
related: ["aprendizaje-supervisado", "aprendizaje-automatico", "ciencia-de-datos"]
prerequisites: ["aprendizaje-automatico"]
---

# Evaluación de modelos

## Overview

Evaluar un modelo implica medir sus aciertos y errores sobre datos apropiados y verificar si aprendió un patrón generalizable. Una única métrica puede ser engañosa si el conjunto está desbalanceado o si se evalúa sobre los mismos datos usados para entrenar. [OFF-001, pp. 95-99, 210-211]

## Core concepts

- La matriz de confusión organiza verdaderos positivos, verdaderos negativos, falsos positivos y falsos negativos para una clasificación. [OFF-001, p. 96]
- A partir de esos conteos se construyen métricas estándar; su interpretación depende del costo relativo de cada tipo de error. [OFF-001, pp. 95-97]
- El sobreajuste ocurre cuando el modelo se ajusta demasiado a los datos de entrenamiento y pierde generalización; el subajuste indica que no captura adecuadamente el patrón. [OFF-001, p. 97]
- La validación cruzada divide los datos en particiones para repetir entrenamiento y evaluación, buscando una estimación más confiable del desempeño. [OFF-001, pp. 98-99]

## Example

En una clasificación binaria muy desbalanceada, predecir siempre la clase mayoritaria puede producir alta exactitud y, sin embargo, ser inútil. [OFF-001, p. 211]

## Aplicación práctica

En el TP 3 se debe justificar métricas y estrategia de partición para estimar fraude, además de recomendar un umbral de detección. Para clasificación de dígitos, el archivo de test se reserva como aproximación al comportamiento en producción; el TP exige analizar el efecto de arquitectura, tasa de aprendizaje y optimización antes de evaluar generalización. [OFF-010, pp. 3-5]

## Relationships

La evaluación completa el ciclo de [aprendizaje supervisado](aprendizaje-supervisado.md) y permite comprobar la [generalización](aprendizaje-automatico.md) en un pipeline de aprendizaje automático.

## Exam relevance

Se debe poder leer una matriz de confusión, distinguir subajuste de sobreajuste y explicar por qué una partición de evaluación o validación cruzada es necesaria. [OFF-001, pp. 95-99]

## Sources

- [OFF-001, pp. 95-99, 210-211]
- [OFF-010, pp. 3-5]
- [EXT-001, pp. 31-34]
