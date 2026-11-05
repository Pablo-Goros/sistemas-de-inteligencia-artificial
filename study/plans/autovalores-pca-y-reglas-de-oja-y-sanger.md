# Plan de estudio: Autovalores y autovectores, PCA y reglas de Oja y Sanger

Study depth: medium

Fuentes principales: OFF-018 — Autovalores y autovectores; OFF-019 — Análisis de componentes principales; OFF-020 — Regla de Oja y Sanger.

El tema integra las tres clases en una secuencia: comprender las direcciones propias de una transformación, usarlas para construir una representación de máxima variabilidad y estudiar cómo una red lineal aprende esas direcciones iterativamente.

## Alcance y referencias

La profundidad incluye intuición, formalismo central, supuestos, cálculos manuales, interpretación de resultados, relaciones entre métodos y limitaciones. Se desarrollan el procedimiento de PCA, la actualización de Oja y la extensión de Sanger. La deducción completa por Taylor y las demostraciones de convergencia quedan fuera de este alcance; se estudia el papel de la normalización y de la tasa de aprendizaje sin presentar las recomendaciones de las diapositivas como garantías universales.

Los prerrequisitos se recuperan dentro del mapa: combinación lineal, producto matriz-vector, media y dispersión, estandarización y salida de una neurona lineal. La introducción al aprendizaje no supervisado sirve como contexto breve; no se repite el desarrollo de Kohonen. Los ejemplos son de las clases y del apunte, sin resolver un trabajo práctico.

Las referencias usan páginas del PDF, coincidentes con las secciones `Page` de los extractos. Se revisaron los originales para recuperar fórmulas, matrices y gráficos que no aparecen completos en los extractos.

- [OFF-018: extracto](../../sources/extracted/OFF-018.md), [PDF original](<../../sources/official/4 - Autovalores y Autovectores (1).pdf>), pp. 4-14.
- [OFF-019: extracto](../../sources/extracted/OFF-019.md), [PDF original](<../../sources/official/5 - PCA (2).pdf>), pp. 5-46.
- [OFF-020: extracto](../../sources/extracted/OFF-020.md), [PDF original](<../../sources/official/6 - Regla de Oja y Sanger (1).pdf>), pp. 4-17.
- [OFF-001: apunte de cátedra](../../sources/extracted/OFF-001.md), [PDF original](<../../sources/official/SIA - Apunte Cátedra.pdf>), pp. 113-117 y 129-132. Complementa la varianza acumulada, contrasta los procedimientos de PCA y aporta la fórmula de Sanger que no desarrolla OFF-020.
- [OFF-016: contexto no supervisado](../../sources/extracted/OFF-016.md), pp. 4-5 y 15; [OFF-014: estandarización](../../sources/extracted/OFF-014.md), p. 33, como apoyo de prerrequisitos.
- [EXT-001: resumen externo](../../sources/extracted/EXT-001.md), pp. 36-38, consultado como apoyo secundario. Las fuentes oficiales tienen prioridad; las afirmaciones de convergencia del resumen no agregan una demostración.

Wiki de apoyo: [autovalores y autovectores](../../wiki/topics/autovalores-y-autovectores.md), [análisis de componentes principales](../../wiki/topics/analisis-componentes-principales.md), [reglas de Oja y Sanger](../../wiki/topics/reglas-de-oja-y-sanger.md), [aprendizaje no supervisado](../../wiki/topics/aprendizaje-no-supervisado.md), [normalización de datos](../../wiki/topics/normalizacion-de-datos.md) y [perceptrón simple](../../wiki/topics/perceptron-simple.md).

## Bloques

1. [cubierto] Combinaciones lineales y direcciones propias
   - Alcance: recuperar vectores, coeficientes y producto matriz-vector; construir la intuición geométrica de autovector y autovalor antes del cálculo algebraico.
   - Resultados de aprendizaje: escribir una combinación lineal; aplicar una matriz a un vector; distinguir conservación de la dirección de conservación del vector; interpretar `Av = λv` con `v ≠ 0`.
   - Esquema de investigación: coeficientes de una combinación; transformación lineal en dos dimensiones; comparación de vectores que cambian de dirección con uno que se escala; relación entre un autovalor y su autovector. Aclarar que la palabra «invariante» de la diapositiva se refiere a la dirección propia, no a que siempre se cumpla `Av = v`.
   - Ejemplo previsto: matriz `A = [[3, 2], [1, 4]]` y vectores `(1, 0)`, `(0, 1)` y `(1, 1)`; leer el gráfico oficial y verificar cuál conserva su dirección. No adelantar todavía la búsqueda de todos los autovalores.
   - Fuentes: OFF-018, pp. 4-9. Fórmulas y gráfico originales: pp. 4-7 y 9; wiki de autovalores y autovectores.

2. [cubierto] Cálculo de autovalores y autovectores
   - Alcance: resolver el problema en una matriz pequeña y preparar el uso de autovectores como cargas de PCA.
   - Resultados de aprendizaje: construir `A - λI`; calcular `det(A - λI)`; hallar sus raíces; resolver el sistema homogéneo para cada raíz; verificar un par propio; reconocer que los múltiplos no nulos representan la misma dirección y normalizar un vector para usarlo como carga.
   - Esquema de investigación: equivalencia entre `Av = λv` y `(A - λI)v = 0`; solución no trivial y determinante nulo; separación entre hallar valores y hallar vectores; normalización de la longitud sin cambiar el autovalor. No extender a formas de Jordan ni a un estudio general de diagonalización.
   - Ejemplo previsto: reconstruir el cálculo de OFF-018 para la matriz del bloque 1, resolver ambos sistemas y comprobar los resultados por multiplicación. Como puente a PCA, comparar un autovector con su versión de norma uno.
   - Fuentes: OFF-018, pp. 10-14; OFF-019, pp. 21-22, para el uso posterior de las cargas. Matrices y desarrollo algebraico originales: OFF-018, pp. 12-14.

3. [en curso] Dispersión, covarianza, correlación y preparación de datos
   - Alcance: organizar observaciones y variables; estudiar los estadísticos que construyen la matriz sobre la que se aplicará PCA; decidir entre centrar y estandarizar.
   - Resultados de aprendizaje: calcular media, varianza y covarianza en un conjunto pequeño; interpretar el signo de la covarianza; construir una matriz cuadrada de relaciones entre variables; distinguir covarianza nula de independencia; justificar una elección entre covarianzas y correlaciones según las escalas.
   - Esquema de investigación: convención única `X` con `m` observaciones y `p` variables; media y varianza por columna; covarianza entre pares; varianzas en la diagonal y simetría; correlación `r_ik = s_ik / (sqrt(s_ii) sqrt(s_kk))`; centrado `X_c = X - media(X)` y estandarización por desvío. Para los cálculos muestrales, fijar el denominador según la cantidad de observaciones y mantenerlo coherente entre varianza y covarianza; revisar la inconsistencia de índices de las fuentes.
   - Ejemplo previsto: tomar dos columnas de los tiempos de natación de OFF-019, p. 5, calcular sus estadísticos y comparar el efecto de cambiar la unidad de una columna. Usar después las variables del ejemplo de pacientes para discutir escalas diferentes, sin desarrollar una predicción clínica.
   - Fuentes: OFF-019, pp. 5-11 y 25-27; OFF-001, pp. 113-114 y 116; OFF-014, p. 33. Fórmulas originales: OFF-019, pp. 7-11. Atender a las discrepancias registradas al final del plan.

4. [pendiente] PCA como búsqueda de direcciones de máxima varianza
   - Alcance: relacionar reducción de dimensionalidad, proyección y autovectores; precisar qué se maximiza y qué significa una componente principal.
   - Resultados de aprendizaje: distinguir variable original, vector de cargas y valor de una componente para una observación; explicar la necesidad de cargas de norma uno; relacionar cada autovalor con la varianza de su componente; distinguir obtener las componentes de seleccionar solo algunas.
   - Esquema de investigación: redundancia y correlación; combinaciones lineales de datos centrados; problema de maximizar la varianza bajo `||a|| = 1`; reconstrucción algebraica breve de `Var(aᵀx) = aᵀSa`; autovectores normalizados como cargas; direcciones ortogonales y componentes no correlacionadas; orden decreciente de autovalores. Ubicar PCA en aprendizaje no supervisado y aclarar que «información» se usa aquí en términos de variabilidad, no como sinónimo de utilidad para cualquier objetivo.
   - Ejemplo previsto: comparar dos proyecciones de una nube alargada, apoyándose en el gráfico de OFF-019, p. 17; explicar por qué aumentar arbitrariamente la longitud de una carga haría necesario imponer la restricción de norma.
   - Fuentes: OFF-019, pp. 13-23; OFF-001, pp. 114-115; OFF-016, pp. 4 y 15. Fórmulas originales: OFF-019, pp. 20-23. La identidad de varianza se reconstruirá a partir de la definición de covarianza y de la combinación lineal presentadas en las fuentes.

5. [pendiente] Procedimiento de PCA y varianza explicada
   - Alcance: integrar preparación, descomposición, selección y transformación en un procedimiento completo; cuantificar lo que retiene una reducción.
   - Resultados de aprendizaje: ordenar los pares propios; formar una matriz de cargas con dimensiones correctas; proyectar observaciones; calcular varianza explicada individual y acumulada; seleccionar una cantidad de componentes con un criterio explícito e identificar la variabilidad descartada.
   - Esquema de investigación: comparar el recorrido por covarianzas de OFF-001 con el recorrido por correlaciones de OFF-019; mantener el centrado o la estandarización elegidos; usar autovectores como columnas de `V_q`, de tamaño `p × q`, y `Y = X_c V_q`, de tamaño `m × q`, o su equivalente sobre datos estandarizados. Proporciones `λ_i / sum(λ_j)` y `sum(λ_1,...,λ_q) / sum(λ_j)`; criterio de retención, con el 95 % del apunte como ejemplo. Comprobar dimensiones antes de trasladar la notación matricial de las fuentes.
   - Ejemplo previsto: reconstruir el ejercicio `S = [[3, 1, 1], [1, 3, 1], [1, 1, 5]]`, obtener las componentes y las proporciones de varianza, comparar retener una o dos y discutir un umbral propuesto. Tratar `S` como matriz de covarianzas según OFF-001 y verificar los vectores antes de usar sus aproximaciones impresas.
   - Fuentes: OFF-019, pp. 22-32; OFF-001, pp. 115-117. Matriz, cargas y resultados originales: OFF-019, pp. 28-31; fórmula acumulada y procedimiento: OFF-001, p. 116. La orientación `Y = X_c V_q` es la adaptación a la convención de filas y columnas fijada en este mapa.

6. [pendiente] Interpretación de cargas, índices y gráficos de PCA
   - Alcance: pasar del cálculo a la lectura de resultados; estudiar los ejemplos de presupuestos familiares y chatbots dentro de la evidencia disponible.
   - Resultados de aprendizaje: interpretar signos y magnitudes de cargas; distinguir cargas de coordenadas de observaciones; explicar un índice construido con PC1; reconocer el efecto de invertir el signo de un autovector; leer cualitativamente los gráficos sin atribuir causalidad a las asociaciones.
   - Esquema de investigación: componente como suma ponderada e índice de ordenación; interpretación de las cargas del ejemplo de gastos; inversión conjunta de carga y coordenadas; comparación de boxplots antes y después de estandarizar; identificación de observaciones y variables en el biplot PC1-PC2; consecuencias de visualizar solo dos componentes. Separar máxima varianza de máxima capacidad de explicar una variable de respuesta, como satisfacción.
   - Ejemplo previsto: interpretar la PC1 del presupuesto familiar de OFF-019, pp. 34-38; luego contrastar los boxplots del chatbot y leer su biplot e índice, señalando qué preguntas pueden explorarse y qué conclusiones requieren datos o análisis adicionales.
   - Fuentes: OFF-019, pp. 34-46; OFF-001, p. 117. Fórmula original de gastos: OFF-019, p. 35; gráficos originales del chatbot: pp. 43-46. La igualdad de dirección propia al cambiar el signo se verifica con la ecuación de OFF-018, p. 9.

7. [pendiente] De la neurona lineal y Hebb a la regla de Oja
   - Alcance: comprender el paso de una actualización supervisada a una no supervisada y el problema del crecimiento de los pesos.
   - Resultados de aprendizaje: calcular `y = wᵀx`; distinguir la actualización con salida deseada de `Δw = ηyx`; explicar el papel de la normalización; interpretar los dos términos de `Δw = η(yx - y²w)`.
   - Esquema de investigación: recuperar únicamente la salida lineal del perceptrón; ausencia de etiqueta de verdad; refuerzo hebbiano entre entrada y salida; crecimiento de la norma; normalización de una actualización hebbiana; aproximación por Taylor como origen del término correctivo, sin desarrollar toda la expansión; relación del peso aprendido con una carga de PCA.
   - Ejemplo previsto: usar una entrada y un vector de pesos bidimensionales para comparar una actualización de Hebb con una de Oja; separar el refuerzo `ηyx` de la corrección `-ηy²w` y observar cómo afectan a los pesos.
   - Fuentes: OFF-020, pp. 7-12; OFF-001, pp. 129-131; wiki del perceptrón simple, para la activación lineal. Fórmulas de normalización y Taylor originales: OFF-020, pp. 10-11; actualización operativa: p. 12.

8. [pendiente] Algoritmo de Oja, preprocesamiento y convergencia
   - Alcance: recorrer una época de entrenamiento, conectar el peso final con PC1 y delimitar los supuestos de las afirmaciones de convergencia de la clase.
   - Resultados de aprendizaje: ejecutar manualmente una actualización completa; distinguir muestras, dimensiones y épocas; explicar por qué se requieren entradas centradas; relacionar el preprocesamiento con la matriz de la que se aprende una dirección; reconocer el papel de inicialización, tasa y cantidad de iteraciones.
   - Esquema de investigación: pesos iniciales aleatorios; para cada muestra, calcular `y` y actualizar simultáneamente el vector con `w ← w + ηy(x - yw)`; repetir sobre las observaciones; comparar norma y dirección; leer la trayectoria de pesos del gráfico oficial. Revisar la tasa vinculada al autovalor, la recomendación de tasa inicial y la alternativa pequeña constante; distinguir estas propuestas de una prueba general. Conectar datos centrados con covarianzas y estandarizados con correlaciones mediante las definiciones del bloque 3.
   - Ejemplo previsto: recorrer pocas muestras centradas de dimensión dos, con una tasa explícita, y comprobar las dimensiones de cada operación; interpretar después el gráfico de convergencia de OFF-020, p. 13, frente a la solución de PCA calculada directamente.
   - Fuentes: OFF-020, pp. 12-16; OFF-001, pp. 131-132; OFF-019, pp. 11 y 25-27. Gráfico y tasa originales: OFF-020, pp. 13-14; algoritmo: p. 16. La relación entre matriz aprendida y preprocesamiento se reconstruye con las definiciones de covarianza y correlación; se mantiene visible el uso de ambos nombres en las fuentes.

9. [pendiente] Sanger y extracción de varias componentes
   - Alcance: extender Oja a varias salidas, comprender la corrección por componentes anteriores e integrar los tres enfoques del tema.
   - Resultados de aprendizaje: distinguir una salida de Oja de las `k` salidas de Sanger; interpretar los índices de la actualización; explicar por qué la primera fila reproduce Oja; recorrer una actualización de dos salidas; comparar qué devuelve PCA directo, Oja y Sanger y qué variabilidad conserva cada elección.
   - Esquema de investigación: pesos `W` de tamaño `k × p`, salida `y = Wx`, con `1 ≤ k ≤ p`; regla por fila `Δw_i = η y_i (x - sum_{j=1}^i y_j w_j)`; inclusión de la propia componente y de las anteriores; relación con direcciones principales distintas y con las cargas. Usar una copia de los pesos previos para el cálculo conjunto del ejemplo. Diferenciar aprender `k` direcciones de obtener la descomposición completa cuando `k = p`; contrastar costo y pérdida de variabilidad sin convertir las ventajas mencionadas por la clase en garantías.
   - Ejemplo previsto: con dos salidas y dos características, escribir las correcciones de la primera y segunda fila y realizar un paso; cerrar con una comparación del resultado esperado de PCA, Oja y Sanger sobre el mismo conjunto preparado.
   - Fuentes: OFF-020, pp. 4-5 y 17; OFF-001, p. 132, ecuaciones 15.10-15.11 y explicación de la corrección; conexión con OFF-019, pp. 22-23 y 32. EXT-001, pp. 37-38, solo como síntesis secundaria.

## Discrepancias y límites de las fuentes

- OFF-018, p. 9, llama al autovector «vector que queda invariante», pero la propia ecuación `Av = λv` permite un cambio de escala. En el bloque 1 se precisará qué se conserva, apoyándose también en el ejemplo de pp. 6-8.
- OFF-019, p. 8, distingue `m` observaciones y `n` variables, pero imprime `1/n` como factor de la covarianza y suma sobre `m` observaciones. OFF-001, p. 114, repite esa notación; la varianza muestral de OFF-019, p. 7, usa cantidad de observaciones menos uno. El bloque 3 fijará una convención muestral coherente y explicitará la adaptación, sin copiar el denominador de variables como si fuera el de observaciones.
- OFF-019, p. 9, y OFF-001, p. 114, describen la matriz de covarianzas como definida positiva. El bloque 3 verificará el alcance de esa afirmación y contemplará variables redundantes. A partir de la definición se puede reconstruir `aᵀSa` como una suma de cuadrados: no negativa, pero posiblemente cero. Esta es una comprobación algebraica del plan; las fuentes no desarrollan las condiciones de positividad estricta.
- OFF-019, p. 10, afirma que covarianza nula implica independencia; OFF-001, p. 114, dice que no hay asociación lineal. Se conservará explícitamente la discrepancia y se usará la formulación del apunte, sin convertir ausencia de asociación lineal en independencia.
- OFF-019, p. 28, llama «matriz de correlaciones» a `S`, cuya diagonal es `3, 3, 5`. OFF-001, p. 116, presenta la misma matriz como covarianzas. El bloque 5 seguirá esa atribución y contrastará la diagonal con la definición de correlación de OFF-019, p. 11.
- OFF-019, p. 21, y OFF-001, p. 115, imprimen de forma imprecisa la condición de normalización de las cargas. El bloque 4 formulará `||a|| = 1` y mostrará por qué es necesaria. OFF-001, p. 116, escribe además `Y = E(X - media(X))`, aunque presenta datos con variables en columnas y autovectores en columnas; el bloque 5 comprobará dimensiones y explicitará la orientación elegida.
- OFF-019, p. 16, y OFF-001, p. 115, afirman que PCA no tiene sentido si las variables no están correlacionadas. El bloque 4 comprobará qué resulta de una matriz diagonal y distinguirá ausencia de rotación útil de la selección de dimensiones según sus varianzas; no repetirá esa frase como imposibilidad algebraica de realizar PCA.
- OFF-020, p. 12, y OFF-001, p. 131, hablan de correlaciones para Oja; OFF-020, p. 17, y OFF-001, p. 132, hablan de covarianzas para Sanger. El bloque 8 distinguirá el preprocesamiento de entradas antes de identificar la matriz. El pseudocódigo de OFF-020, p. 16, y el de OFF-001, p. 132, también mezclan cantidad de datos y dimensión: la enseñanza recorrerá muestras completas con notación inequívoca.
- OFF-020, pp. 12-15, y OFF-001, p. 131, dan afirmaciones y recomendaciones de convergencia, pero no una demostración completa con todos sus supuestos. No se prometerá convergencia para cualquier conjunto, inicialización o tasa. OFF-020, p. 17, solo resume Sanger; la fórmula del bloque 9 proviene explícitamente de OFF-001, p. 132.
- OFF-019, pp. 40-46, ofrece contexto y gráficos del chatbot, pero no el conjunto completo de observaciones, las cargas numéricas de todas sus componentes ni todos los detalles de construcción del biplot. El bloque 6 permite una lectura cualitativa; no promete reproducir el análisis ni demostrar qué variables causan satisfacción.

## Continuación

Usar `$study-block autovalores-pca-y-reglas-de-oja-y-sanger, bloque 1` para comenzar. Los estados registran únicamente cobertura por bloques; este mapa no almacena respuestas ni perfiles del estudiante.
