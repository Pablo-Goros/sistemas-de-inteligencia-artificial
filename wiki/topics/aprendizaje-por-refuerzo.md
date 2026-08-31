---
title: "Aprendizaje por refuerzo"
aliases: ["reinforcement learning", "RL", "MDP", "proceso de decisión de Markov"]
sources: ["OFF-001", "EXT-001"]
related: ["agentes-y-ambientes", "aprendizaje-automatico", "optimizacion-matematica"]
prerequisites: ["agentes-y-ambientes", "aprendizaje-automatico"]
---

# Aprendizaje por refuerzo

## Overview

En el aprendizaje por refuerzo, un agente interactúa con un ambiente: toma acciones, recibe recompensas y aprende una política que busca maximizar la recompensa acumulada. A diferencia del aprendizaje supervisado, la señal puede ser tardía y no es una etiqueta correcta por cada ejemplo. [EXT-001, p. 13]

## Core concepts

- Un Proceso de Decisión de Markov (MDP) se representa como `(S, A, R, p, γ)`: estados, acciones, recompensas, dinámica probabilística y factor de descuento. La transición conjunta es `p(s', r | s, a)`. [EXT-001, p. 13]
- La propiedad de Markov supone que, para predecir el paso siguiente, alcanza con el estado y la acción actuales; el estado debe resumir la información relevante del pasado. [EXT-001, p. 14]
- Una política puede ser determinista o estocástica. Las funciones de valor `vπ` y `qπ` estiman la recompensa esperada a largo plazo bajo una política. [EXT-001, p. 14]
- Generalized Policy Iteration alterna evaluación de una política y mejora de esa política. Monte Carlo estima valores usando retornos de episodios completos; Q-learning actualiza en cada paso mediante bootstrap. [EXT-001, pp. 15-16]

## How it works

El agente observa el estado, elige una acción según su política, recibe una recompensa y observa el nuevo estado. El factor `γ` pondera el futuro: valores cercanos a cero favorecen recompensas inmediatas y valores cercanos a uno favorecen planificación a más largo plazo. [EXT-001, p. 13]

## Relationships

El apunte oficial ubica el aprendizaje por refuerzo entre los métodos de aprendizaje, pero no desarrolla aquí el formalismo MDP ni los algoritmos anteriores. [OFF-001, p. 28] El resumen externo aporta ese desarrollo y debe tratarse como cobertura complementaria, no como sustituto de una explicación oficial.

## Exam relevance

El material disponible permite estudiar las definiciones de MDP, propiedad de Markov, política, funciones de valor, GPI, Monte Carlo y Q-learning. La fuente detallada de estos contenidos es externa. [EXT-001, pp. 13-16]

## Sources

- [OFF-001, p. 28]
- [EXT-001, pp. 13-16]
