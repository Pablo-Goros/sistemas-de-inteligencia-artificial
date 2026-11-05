# Plan de estudio: Aprendizaje no supervisado y mapas de Kohonen

Study depth: medium

Fuentes principales: OFF-016 — Introducción al aprendizaje no supervisado; OFF-017 — Modelo de Kohonen.

Este es un único tema de estudio: descubrir estructura en datos sin etiquetas y comprender cómo un mapa autoorganizado la aprende y representa. La secuencia integra ambos materiales por conceptos, sin repetir la introducción al comenzar Kohonen.

## Alcance y referencias

La profundidad incluye mecanismos, formalismo central, supuestos, ejemplos numéricos, interpretación de resultados y limitaciones. Hopfield, PCA, autoencoders, Oja y Sanger se ubican como ejemplos del panorama, sin desarrollar sus algoritmos. Los ejemplos de aplicaciones de OFF-016 se usan para discutir entradas y tareas; las diapositivas no describen sistemas completos de recomendación ni permiten concluir su modalidad de entrenamiento solo por mencionar CNN o ResNets.

Las páginas indicadas corresponden a la numeración de los PDF y de sus extractos. Fuentes:

- [OFF-016: extracto](sources/extracted/OFF-016.md), [PDF original](<sources/official/1 - Introducción Aprendizaje No Supervisado.pdf>).
- [OFF-017: extracto](sources/extracted/OFF-017.md), [PDF original](<sources/official/2 - Modelo de Kohonen.pdf>).
- [OFF-001: apunte de cátedra](sources/extracted/OFF-001.md), como complemento oficial para nomenclatura y contraste del algoritmo.
- [EXT-001: resumen externo](sources/extracted/EXT-001.md), pp. 35-36, consultado como apoyo secundario; prevalecen las fuentes oficiales.

Wiki de apoyo: [aprendizaje automático](wiki/topics/aprendizaje-automatico.md), [aprendizaje no supervisado](wiki/topics/aprendizaje-no-supervisado.md), [mapas autoorganizados de Kohonen](wiki/topics/mapas-autoorganizados-de-kohonen.md) y [normalización de datos](wiki/topics/normalizacion-de-datos.md).

## Bloques

1. [cubierto] Datos sin etiquetas y estructura interna
   - Alcance: recuperar los prerrequisitos de muestras, variables y vectores; distinguir aprendizaje supervisado y no supervisado por la información disponible; plantear el problema de interpretar resultados sin una respuesta conocida.
   - Resultados de aprendizaje: identificar filas y columnas de una matriz de datos; reconocer qué información falta en un problema no supervisado; explicar qué estructura se busca y por qué una visualización parcial puede omitir relaciones.
   - Esquema de investigación: matriz con `P` muestras y `n` variables; etiquetas frente a características; ejemplo de pacientes con siete variables y gráficos de dos y tres variables; diferencia entre descubrir similitudes y disponer de evidencia para predecir riesgo.
   - Ejemplo previsto: organizar el ejemplo de pacientes como matriz y comparar qué muestran y qué omiten las visualizaciones de presión, edad y peso.
   - Fuentes: OFF-016, pp. 4-9; OFF-001, pp. 27-28, 109-110. Gráficos originales: OFF-016, pp. 7-8.

2. [cubierto] Agrupamiento, asociación y reducción de dimensionalidad
   - Alcance: comparar las tres tareas por su pregunta, entrada y resultado esperado; ubicar Kohonen dentro del panorama y reconocer aplicaciones y límites de las afirmaciones introductorias.
   - Resultados de aprendizaje: distinguir un agrupamiento de una memoria asociativa y de una representación de menor dimensión; justificar por qué agrupar requiere definir similitud; relacionar cada tarea con los ejemplos de la clase.
   - Esquema de investigación: similitud dentro de grupos; anomalías y segmentación; relaciones entre atributos y recuperación por asociación; proyección a un espacio menor; costo de etiquetas y dimensionalidad; ubicación de Hopfield, PCA, autoencoders, Oja y Sanger como conexiones futuras.
   - Ejemplo previsto: formular las tres preguntas sobre un mismo conjunto de pacientes; contrastar luego con los ejemplos de marketing, compresión y recomendaciones. Revisar la afirmación sobre separar outliers como una posibilidad de ciertos métodos, sin convertirla en garantía de todo aprendizaje no supervisado.
   - Fuentes: OFF-016, pp. 10-21; OFF-001, pp. 109-110; EXT-001, p. 35. Aplicaciones visuales originales: OFF-016, pp. 18-20.

3. [cubierto] Arquitectura de Kohonen, competencia y organización del mapa
   - Alcance: comprender SOM como una grilla de representantes y relacionar la selección de una ganadora con el agrupamiento y la organización de neuronas vecinas.
   - Resultados de aprendizaje: distinguir dimensión de entrada, cantidad de neuronas y coordenadas del mapa; explicar qué representa un vector de pesos; diferenciar activación de la ganadora y actualización de su vecindario.
   - Esquema de investigación: una capa de neuronas de salida más las entradas; grillas rectangular y hexagonal; `k × k` neuronas con pesos `W_j` de dimensión `n`; aprendizaje competitivo y neurona ganadora; proximidad entre vectores en el espacio de datos frente a proximidad entre posiciones en la grilla.
   - Ejemplo previsto: dibujar una grilla `3 × 3` con entradas de cuatro variables; identificar sus nueve representantes, su dimensión y los vecindarios de una neurona central y una de borde.
   - Fuentes: OFF-017, pp. 4-16; OFF-001, pp. 119-120. Diagramas originales: OFF-017, pp. 6-7, 13-15.

4. [cubierto] Escalas, estandarización y medidas de similitud
   - Alcance: preparar el criterio que determina la ganadora y comprender cómo la escala altera las distancias; comparar las tres transformaciones presentadas.
   - Resultados de aprendizaje: calcular una distancia euclídea y una estandarización sencilla; distinguir min-max, Z-score y longitud unitaria; explicar por qué dos variables con unidades diferentes pueden contribuir de forma desigual a la selección.
   - Esquema de investigación: min-max a `[a,b]`; Z-score por variable; división de un vector por su norma; lectura de los gráficos antes y después de estandarizar; minimización de distancia y maximización de similitud exponencial, atendiendo a la discrepancia entre fuentes.
   - Ejemplo previsto: comparar dos candidatos a ganadora con variables de escalas muy distintas antes y después de estandarizar; realizar un cálculo breve de cada transformación para mostrar qué cambia.
   - Fuentes: OFF-017, pp. 18-22, 29; OFF-001, p. 122. Fórmulas y gráficos originales: OFF-017, pp. 18-22, 29; apoyo conceptual en la wiki de normalización, respaldada por OFF-014, pp. 32-36.

5. [cubierto] Algoritmo de entrenamiento y regla de Kohonen
   - Alcance: recorrer inicialización, selección de entrada, búsqueda de la ganadora, definición del vecindario y actualización de pesos; integrar los bloques anteriores en una iteración completa.
   - Resultados de aprendizaje: ejecutar manualmente una iteración; determinar qué pesos cambian; interpretar el papel de la tasa de aprendizaje y del radio; distinguir asignar una entrada al mapa de entrenar sus representantes.
   - Esquema de investigación: entradas `x_p`, pesos `W_j`, índice ganador `j* = argmin_j ||x_p - W_j||`; vecindario definido sobre posiciones de la grilla; regla `W_j(i+1) = W_j(i) + η(i)(x_p - W_j(i))` dentro del vecindario y pesos constantes fuera; repetición sobre las muestras. Unificar la notación para no confundir `n` variables con `k²` neuronas.
   - Ejemplo previsto: usar una grilla pequeña, pesos bidimensionales y una entrada; calcular distancias, seleccionar la ganadora y actualizarla junto con sus vecinas usando una convención de frontera explícita.
   - Fuentes: OFF-017, pp. 24-27, 29; OFF-001, pp. 120-121.

6. [cubierto] Inicialización, hiperparámetros y alcance de la convergencia
   - Alcance: estudiar las decisiones que condicionan el entrenamiento y reconstruir el argumento algebraico central de acercamiento a una entrada.
   - Resultados de aprendizaje: distinguir pesos aprendidos de hiperparámetros; explicar el problema de unidades muertas; interpretar las agendas de radio y tasa; demostrar el acercamiento de un peso actualizado a la entrada bajo una tasa apropiada, sin inferir de ello una garantía global del mapa.
   - Esquema de investigación: pesos aleatorios frente a muestras de entrenamiento; tamaño de grilla; radio inicial y reducción o mantenimiento constante; tasa decreciente; cantidad de iteraciones sugerida como heurística; identidad `W_j(i+1) - x_p = (1 - η(i))(W_j(i) - x_p)` y su interpretación para `0 < η(i) < 1`.
   - Ejemplo previsto: comparar dos inicializaciones y dos valores de tasa en una actualización; explicar por qué acercarse a la muestra actual no equivale a acercarse simultáneamente a todas las muestras.
   - Fuentes: OFF-017, pp. 24, 26-31, 38; OFF-001, pp. 28, 121-122.

7. [cubierto] Lectura de resultados, aplicaciones y límites del SOM
   - Alcance: interpretar asignaciones, ocupación de neuronas, matriz U y mapas de una variable; cerrar la relación entre estructura no supervisada y representación bidimensional.
   - Resultados de aprendizaje: distinguir cuántos registros llegan a una neurona de las distancias entre representantes; describir qué calcula la matriz U; usar los mapas para comparar regiones del conjunto de datos; reconocer límites de la visualización y del método.
   - Esquema de investigación: coordenadas de las entradas en el mapa; conteos por neurona; promedio de distancias euclídeas a representantes vecinos; visualización de una variable; ejemplo de ciudades y grilla `20 × 20`; variables numéricas, pérdida de detalle al representar muchas dimensiones y elección del tamaño de grilla. Tratar la comparación de rapidez con MLP como una posibilidad indicada por la clase, no como garantía universal.
   - Ejemplo previsto: leer los gráficos oficiales y comparar un mapa de ocupación con una matriz U; reconstruir el recorrido completo de las variables de ciudades hasta las preguntas que permite explorar el mapa.
   - Fuentes: OFF-017, pp. 33-38; OFF-001, p. 122; conexión con OFF-016, pp. 5, 11-16. Gráficos originales: OFF-017, pp. 33, 35-37.

## Discrepancias y límites de las fuentes

- OFF-017, p. 29, imprime `argmin` para la similitud `exp(-||x-W_j||²)`, mientras OFF-001, p. 122, imprime `argmax`. El bloque 4 contrastará ambas expresiones y su comportamiento; no se repetirá la primera como equivalente a minimizar distancia.
- OFF-017, p. 26, define el vecindario con distancia estrictamente menor que `R`, pero pp. 15 y 31 asocian `R = 1` con los vecinos inmediatos, situados a distancia uno. El bloque 5 explicitará la elección de frontera y mantendrá visible la discrepancia.
- La fórmula impresa bajo «desvío estándar» en OFF-017, p. 19, presenta `s_i²` pero omite el cuadrado de las desviaciones en la suma. No se usará esa transcripción como definición operativa; se señalará el problema al trabajar la estandarización.
- El argumento de OFF-017, p. 28, y OFF-001, pp. 121-122, muestra acercamiento del peso a la entrada de una actualización. Las fuentes consultadas no aportan una demostración completa de convergencia global ni de conservación perfecta de la topología.
- OFF-016, p. 5, plantea la significatividad sin desarrollar un protocolo de evaluación; OFF-017, p. 36, propone una lectura cualitativa de la matriz U. El plan no añadirá métricas especializadas ni presentará distancias pequeñas como prueba suficiente de calidad.

## Continuación

Usar `$study-block` con este plan y el bloque 1 para comenzar. Los estados registran únicamente el avance por bloques; no se guardan respuestas ni perfiles del estudiante.
