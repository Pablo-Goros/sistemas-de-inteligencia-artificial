---
title: "Agentes y ambientes"
aliases: ["agente racional", "ambiente", "agent and environment"]
sources: ["OFF-001", "EXT-001"]
related: ["introduccion-inteligencia-artificial", "busqueda-en-espacios-de-estados", "aprendizaje-por-refuerzo"]
prerequisites: ["introduccion-inteligencia-artificial"]
---

# Agentes y ambientes

## Overview

Un agente es un sistema que percibe un ambiente y actúa sobre él con cierto grado de independencia. El ambiente origina las percepciones y recibe las acciones; esta relación ofrece un modelo operativo para estudiar comportamiento inteligente. [OFF-001, pp. 33-34]

## Core concepts

- Un agente racional elige acciones que maximizan su medida de desempeño; no es necesariamente omnisciente, porque racionalidad y conocimiento perfecto son propiedades distintas. [OFF-001, p. 33]
- Un agente reactivo puede modelarse como `a = f(P)`, mientras que uno basado en modelo usa también un estado interno: `a = f(P, M)`. [OFF-001, pp. 33-34]
- Los ambientes se clasifican como discretos o continuos, determinísticos o estocásticos, totalmente o parcialmente observables, conocidos o desconocidos, individuales o multiagente, y colaborativos o adversariales. [OFF-001, p. 34]
- La experiencia del agente puede describirse como la secuencia de acciones ejecutadas y estados transitados. [OFF-001, p. 34]

## Example

En un ambiente multiagente adversarial, el resultado de una acción puede depender de las acciones de otros agentes aunque las reglas del ambiente sean conocidas. [OFF-001, p. 34]

## Relationships

La [búsqueda en espacios de estados](busqueda-en-espacios-de-estados.md) modela las transiciones posibles de un agente. En [aprendizaje por refuerzo](aprendizaje-por-refuerzo.md), el agente aprende su política mediante interacción con el ambiente.

## Exam relevance

Es importante distinguir agente racional de agente omnisciente, agente reactivo de agente basado en modelo, y cada dimensión de clasificación de los ambientes. [OFF-001, pp. 33-34]

## Sources

- [OFF-001, pp. 33-35]
- [EXT-001, p. 4]
