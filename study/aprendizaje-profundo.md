---
topic: "Aprendizaje profundo"
aliases: ["Deep Learning", "DL"]
study_depth: medium
---

# Plan de estudio: Aprendizaje profundo

## Alcance y uso

Mapa basado en los materiales de la materia: fundamentos de profundidad y representación, entrenamiento y principales arquitecturas. Incluye mecanismos, formalismo central, ejemplos trabajados y límites; las demostraciones especializadas quedan fuera del recorrido principal. Cada bloque se enseña primero desde la intuición y luego desde el formalismo, de acuerdo con `study.yaml`.

Los bloques están ordenados por dependencia. CNN precede a difusión por la U-Net; autoencoders y VAE preceden a generación latente; RNN precede a Transformers; atención precede al condicionamiento de difusión. El primer bloque es un puente de prerrequisitos, no un curso completo de aprendizaje supervisado.

Los estados registran cobertura del mapa. No registran respuestas ni perfiles del estudiante. Para comenzar o continuar, usar `study-block` con este tema y el bloque correspondiente.

## Fuentes y localización

Las páginas indicadas corresponden a la numeración `Page N` de los extractos y a la página del PDF, contando desde 1. Se priorizan fuentes oficiales. El catálogo está en [sources/catalog.yaml](../sources/catalog.yaml).

| ID | Material | Acceso |
| --- | --- | --- |
| OFF-001 | Reglamento y Apuntes de Sistemas de Inteligencia Artificial | [Extracto](../sources/extracted/OFF-001.md), [original](../sources/official/SIA%20-%20Apunte%20C%C3%A1tedra.pdf) |
| OFF-021 | Deep Learning, Rodrigo Ramele | [Extracto](../sources/extracted/OFF-021.md), [original](../sources/official/DL.pdf) |
| OFF-004 | Clase 11: Perceptrón multicapa | [Extracto](../sources/extracted/OFF-004.md) |
| OFF-015 | Regularización | [Extracto](../sources/extracted/OFF-015.md) |
| EXT-001 | SIA: Resumen | [Extracto](../sources/extracted/EXT-001.md), p. 40 como repaso complementario de los cuatro pilares |

La wiki permite orientarse por concepto; las referencias de cada bloque indican dónde profundizar en los materiales docentes. Se revisaron también los diagramas originales de OFF-021, pp. 39-40, 54, 56-60, 66-67, 69-74, y de OFF-001, pp. 153-154, 163-166, 175, 179, 185, 195-196, 199.

## Bloques

### 1. [covered] Puente: redes multicapa, gradientes y generalización

- **Alcance:** repasar la composición de capas, pesos y bias, activaciones no lineales, función de costo, pasada hacia adelante, regla de la cadena y actualización por gradiente. Relacionar capacidad con entrenamiento y evaluación.
- **Resultados de aprendizaje:** distinguir el cálculo de gradientes de la actualización de parámetros; seguir el recorrido entrada-salida-error-actualización; explicar por qué una pérdida de entrenamiento baja no basta para concluir que una red generaliza.
- **Esquema de investigación:** recuperar las ecuaciones de una capa y la contribución de un peso oculto al error; diferenciar parámetros e hiperparámetros y modalidades online, mini-batch y batch; conectar subajuste y sobreajuste con capacidad. Repasar early stopping, aumento de datos y penalización L2 como recursos con propósitos concretos.
- **Ejemplo previsto:** red pequeña con una capa oculta: calcular una salida y la dependencia del error respecto de un peso; interpretar después dos curvas de entrenamiento y validación.
- **Preguntas guía:** ¿qué aprende una capa oculta?, ¿qué aporta la no linealidad?, ¿qué se deriva y qué se actualiza?, ¿qué evidencia permite hablar de generalización?
- **Fuentes:** OFF-001, pp. 81-92; OFF-004, pp. 12-14, 19-33, 39-58; OFF-015, pp. 5-24. Wiki: [MLP](../wiki/topics/perceptron-multicapa.md), [retropropagación](../wiki/topics/retropropagacion.md), [optimización](../wiki/topics/optimizacion-matematica.md), [regularización](../wiki/topics/regularizacion.md). Usar las secciones docentes, sin incorporar las aplicaciones a trabajos prácticos del artículo de MLP.

### 2. [covered] Por qué profundidad: representación, datos y dificultades de entrenamiento

- **Alcance:** estudiar los cuatro pilares de Deep Learning y la motivación de componer representaciones; vincular alta dimensionalidad, aproximación universal y asignación de crédito.
- **Resultados de aprendizaje:** explicar qué significa aprender características; distinguir capacidad de aproximación, facilidad de optimización y generalización; describir desvanecimiento y explosión de gradientes y el papel de datos y cómputo.
- **Esquema de investigación:** contrastar características diseñadas manualmente con representaciones aprendidas; interpretar localidad a distintas escalas y estructura composicional; estudiar el alcance del teorema de aproximación universal sin demostrarlo. Relacionar una cadena de derivadas con gradientes pequeños o grandes. Ubicar preentrenamiento por capas, Xavier, dropout y LSTM entre los enfoques mencionados por la presentación, distinguiendo sus funciones y el detalle disponible.
- **Ejemplo previsto:** secuencia visual de rasgos simples a compuestos y producto escalar de varias derivadas menores o mayores que uno como ilustración del problema de propagación.
- **Preguntas guía:** si una capa oculta puede aproximar funciones, ¿qué motiva usar más capas?, ¿qué sigue definiendo quien diseña el sistema?, ¿por qué el hardware importa?
- **Fuentes:** OFF-001, pp. 145-152; OFF-021, pp. 19-20, 33-52, 107; EXT-001, p. 40, solo como repaso. Wiki: [aprendizaje profundo](../wiki/topics/aprendizaje-profundo.md).

### 3. [in progress] CNN: estructura espacial y representaciones jerárquicas

- **Alcance:** convolución y filtros aprendidos, campos locales, pesos compartidos, canales, padding, stride, ReLU, pooling y salida de clasificación; introducir ResNet y U-Net.
- **Resultados de aprendizaje:** calcular una operación local y dimensiones de salida en un caso sencillo; distinguir filtros, canales y activaciones; explicar cómo se entrenan pesos reutilizados y por qué una CNN aprovecha la estructura espacial.
- **Esquema de investigación:** partir de un filtro de suavizado o bordes y pasar a un kernel entrenable. Seguir el flujo convolución-activación-pooling-clasificación; estudiar acumulación de contribuciones al gradiente de pesos compartidos. Distinguir equivariancia de convolución y tolerancia a desplazamientos asociada a agregación/pooling, evitando prometer invariancia total. Introducir conexiones residuales, reutilización de características y recorrido de reducción y recuperación de resolución de U-Net, con sus conexiones entre escalas.
- **Ejemplo previsto:** entrada pequeña y kernel `3 × 3`: calcular una salida, comparar padding y stride, aplicar max pooling e identificar parámetros entrenables. Leer luego un bloque residual y una U-Net.
- **Preguntas guía:** ¿qué cambia frente a una capa totalmente conectada?, ¿pooling tiene pesos?, ¿un canal equivale siempre a un color?, ¿qué información recuperan las conexiones de U-Net?
- **Fuentes:** OFF-001, pp. 173-185, especialmente 174-175 y 178-185; OFF-021, pp. 54, 72. Wiki: [redes convolucionales](../wiki/topics/redes-neuronales-convolucionales.md).

### 4. [pending] Autoencoders: reconstrucción y estructura latente

- **Alcance:** encoder, código latente, decoder y pérdida de reconstrucción; relación con PCA y variantes denoising, contractive y sparse; aplicaciones y límites de la reconstrucción.
- **Resultados de aprendizaje:** identificar qué entrada y objetivo se usan para entrenar; explicar qué restricciones favorecen una representación útil; distinguir compresión, eliminación de ruido y detección de anomalías.
- **Esquema de investigación:** seguir `x → z → x'` y la minimización del error de reconstrucción. Revisar la relación del caso lineal con PCA bajo las condiciones del apunte, sin exigir la demostración espectral completa. Comparar cuello de botella con restricciones de esparsidad y de sensibilidad; aclarar que el código no siempre tiene menor dimensión que la entrada. Explorar qué significa un error alto de reconstrucción y qué limitaciones tiene usarlo como indicador de anomalía. Preparar la transición desde reconstruir a generar.
- **Ejemplo previsto:** comparar el entrenamiento con pares entrada-objetivo `x → x` y entrada ruidosa-objetivo limpio; interpretar códigos de pocas dimensiones y reconstrucciones de muestras nuevas.
- **Preguntas guía:** ¿por qué copiar la entrada puede enseñar algo?, ¿qué evita una copia trivial?, ¿en qué condiciones se conecta con PCA?, ¿reconstruir bien garantiza generar bien?
- **Fuentes:** OFF-001, pp. 153-159; OFF-021, p. 59. Wiki: [autoencoders](../wiki/topics/autoencoders.md); apoyo conceptual: [PCA](../wiki/topics/analisis-componentes-principales.md).

### 5. [pending] VAE: generación, inferencia variacional y reparametrización

- **Alcance:** estructurar probabilísticamente el espacio latente; distinguir posterior aproximada, prior y decoder; comprender el objetivo variacional y el paso estocástico diferenciable.
- **Resultados de aprendizaje:** explicar qué produce el encoder de un VAE; interpretar los términos de reconstrucción y KL; seguir una muestra y el recorrido del gradiente; distinguir entrenamiento de generación.
- **Esquema de investigación:** recuperar probabilidad condicional, esperanza y divergencia KL solo hasta lo necesario para interpretar el modelo. Leer la cota variacional de OFF-001, pp. 163-165, y su descomposición en reconstrucción y ajuste al prior. Usar notación consistente para media, desvío, varianza y log-varianza; estudiar `z = mu(x) + sigma(x) ⊙ epsilon`. Seguir el grafo encoder-parámetros-muestra-decoder-costo y el papel de la reparametrización. La derivación algebraica exhaustiva de KL gaussiana queda como ampliación.
- **Ejemplo previsto:** código gaussiano de dos dimensiones: fijar media, desvío y una muestra de ruido, obtener `z` y señalar cómo llegan los dos términos del objetivo al encoder; contrastar muestreo desde el prior e interpolación entre códigos.
- **Preguntas guía:** ¿por qué introducir una distribución?, ¿qué regulariza KL?, ¿qué cambia al fijar el ruido durante el cálculo de una derivada?, ¿de dónde sale un código al generar sin una entrada?
- **Fuentes:** OFF-001, pp. 158-167; apoyo de probabilidad e información en pp. 167-169. OFF-021, pp. 59-60, como ubicación de la familia. Wiki: [autoencoders](../wiki/topics/autoencoders.md), cuyo resumen se amplía aquí con el desarrollo del apunte.

### 6. [pending] RNN y LSTM: estado y profundidad temporal

- **Alcance:** recurrencia, estado oculto, despliegue temporal y parámetros compartidos; dificultades de dependencias largas; estado de celda y compuertas LSTM.
- **Resultados de aprendizaje:** desplegar una RNN durante pocos pasos; distinguir profundidad espacial y temporal; interpretar el control de información de una LSTM sin atribuirle memoria ilimitada.
- **Esquema de investigación:** leer las matrices de entrada y recurrencia y la transición no lineal; conectar el despliegue con el problema de gradientes del bloque 2. Identificar candidato y compuertas de entrada, olvido y salida; seguir las actualizaciones de estado de celda y oculto de OFF-021, p. 57. Comparar qué se conserva y qué se expone; ubicar las limitaciones que motivan estudiar atención. No desarrollar una derivación completa de retropropagación temporal.
- **Ejemplo previsto:** secuencia de tres entradas con el mismo conjunto de pesos; caso de compuerta de olvido cercana a uno y entrada cercana a cero para interpretar conservación del estado.
- **Preguntas guía:** ¿qué viaja entre instantes?, ¿cada paso introduce pesos nuevos?, ¿estado de celda y estado oculto son lo mismo?, ¿por qué el tiempo crea una cadena profunda?
- **Fuentes:** OFF-021, pp. 40-42, 55-57; OFF-001, pp. 193-195. Wiki: [redes recurrentes](../wiki/topics/redes-neuronales-recurrentes.md).

### 7. [pending] GAN: generación mediante entrenamiento adversarial

- **Alcance:** generador, discriminador, ruido latente, objetivo minimax, entrenamiento alternado, equilibrio ideal y colapso modal.
- **Resultados de aprendizaje:** explicar qué recibe y optimiza cada red; interpretar el objetivo adversarial y el flujo del gradiente al generador; distinguir equilibrio ideal de comportamiento real durante el entrenamiento.
- **Esquema de investigación:** leer los dos términos del objetivo con datos reales y muestras `G(z)`; relacionarlos con clasificación binaria. Seguir una actualización del discriminador y otra del generador, identificando qué parámetros se ajustan en cada una. Interpretar el caso ideal de indistinguibilidad y la dificultad de equilibrar ambas redes. Contrastar generación con VAE y falta de diversidad con simple mala calidad visual.
- **Ejemplo previsto:** distribución con varios grupos: dibujar muestras reales y generadas e identificar cuándo el generador solo cubre un grupo; recorrer el esquema ruido-generador-discriminador.
- **Preguntas guía:** ¿el generador recibe una imagen objetivo para cada ruido?, ¿cómo aprende del discriminador?, ¿una salida cercana a azar prueba por sí sola que se aprendió la distribución?, ¿qué significa colapso modal?
- **Fuentes:** OFF-001, pp. 187-190; OFF-021, pp. 61-64. Wiki: [GAN](../wiki/topics/redes-generativas-adversarias.md).

### 8. [pending] Transformers: tokens, atención y procesamiento de secuencias

- **Alcance:** tokenización, embeddings e información posicional; Query, Key, Value y atención escalada; arquitectura encoder-decoder, atención causal y atención entre entrada y salida.
- **Resultados de aprendizaje:** calcular un ejemplo pequeño de atención como combinación ponderada; explicar qué aprende cada proyección; distinguir funciones de encoder y decoder y justificar la restricción a información previa durante generación.
- **Esquema de investigación:** partir de las limitaciones de secuencias recurrentes; ubicar vocabulario, vectores y posición antes de calcular atención. Interpretar `softmax(QK^T / sqrt(d_k)) V`, sus dimensiones y proyecciones aprendidas; relacionar acceso continuo por similitud y promedio ponderado. Seguir self-attention y atención encoder-decoder, bloques MLP y salida lineal-Softmax. Separar entrenamiento con secuencias conocidas de producción sucesiva de tokens. Estudiar el papel del orden sin memorizar fórmulas sinusoidales.
- **Ejemplo previsto:** frase breve con una referencia entre palabras y una matriz pequeña de puntajes; obtener pesos y suma de Values; mostrar qué entradas se ocultan en atención causal.
- **Preguntas guía:** ¿token e embedding son lo mismo?, ¿de dónde vienen Q, K y V?, ¿qué información aporta la posición?, ¿qué diferencia hay entre self-attention y cross-attention?, ¿encoder/decoder significa lo mismo que en un autoencoder?
- **Fuentes:** OFF-001, pp. 193-200, especialmente 195-199; OFF-021, pp. 66-67, 73. Wiki: [Transformers](../wiki/topics/transformers.md).

### 9. [pending] Difusión: generación por eliminación de ruido y condicionamiento

- **Alcance:** proceso directo de ruido y proceso inverso aprendido; difusión en espacio latente e integración de VAE, U-Net, atención y codificador de condición.
- **Resultados de aprendizaje:** reconstruir el flujo de generación del diagrama de difusión latente; asignar una función a cada componente; distinguir eliminación de ruido en varios pasos de una reconstrucción directa por autoencoder.
- **Esquema de investigación:** leer la cadena de OFF-021, p. 69, y comparar estados progresivamente ruidosos con transiciones inversas. Seguir ruido latente-U-Net condicionada-actualizaciones sucesivas-decoder VAE-imagen. Identificar el paso temporal y el embedding de condición; leer cross-attention entre características de imagen y contexto. Ubicar CLIP como codificador de condición en el esquema presentado y reconocer sus ramas de texto e imagen, sin desarrollar su entrenamiento completo.
- **Ejemplo previsto:** diagrama anotado para una imagen guiada por texto: indicar dónde están el ruido, el código, la condición y la imagen, y qué se repite en cada paso.
- **Preguntas guía:** ¿en qué espacio se elimina ruido?, ¿qué función cumple el VAE?, ¿la condición es la imagen de salida?, ¿qué produce cada iteración y qué hace el decoder final?
- **Fuentes:** OFF-021, pp. 68-74, con revisión visual indispensable de pp. 69-74. Wiki: [modelos de difusión](../wiki/topics/modelos-de-difusion.md). Prerrequisitos internos: bloques 3, 5 y 8.
- **Límite de cobertura:** estas fuentes permiten una explicación arquitectónica sólida, pero no desarrollan la pérdida completa, la derivación probabilística ni algoritmos numéricos de muestreo. No se promete ese desarrollo en este mapa.

### 10. [pending] Integración: elegir mecanismos, reconocer límites y ubicar extensiones

- **Alcance:** comparar familias por estructura de datos, objetivo de entrenamiento, representación y tipo de salida; conectar capacidad, generalización e interpretación con aplicaciones y limitaciones del material.
- **Resultados de aprendizaje:** justificar qué mecanismo resulta pertinente para una tarea; comparar reconstrucción, generación adversarial, recurrencia, atención y eliminación iterativa de ruido; explicar por qué una arquitectura puede integrar varias familias.
- **Esquema de investigación:** construir una tabla con CNN, autoencoder, VAE, RNN/LSTM, GAN, Transformer y difusión: entrada, representación, señal de entrenamiento, salida y limitación principal. Reutilizar una tarea visual y otra secuencial para discutir alternativas. Relacionar sesgo de datos, errores de evaluación, inteligibilidad y explicabilidad con los límites del modelo. Ubicar DBN y aprendizaje por refuerzo profundo como extensiones mencionadas por OFF-021, sin convertirlas en un desarrollo completo de modelos energéticos o de aprendizaje por refuerzo.
- **Ejemplo previsto:** clasificar imágenes, detectar una muestra atípica, procesar una secuencia y generar una imagen condicionada; justificar componentes, información disponible al entrenar y evidencia necesaria para evaluar el resultado.
- **Preguntas guía:** ¿qué diferencia una arquitectura de un objetivo de aprendizaje?, ¿por qué una U-Net puede aparecer dentro de difusión?, ¿calidad de una muestra implica diversidad?, ¿qué permite interpretar una decisión y qué sigue sin explicarse?
- **Fuentes:** síntesis de las fuentes de bloques 2-9; OFF-001, pp. 182-185; OFF-021, pp. 58, 75-76, 78-85, 99, 107. Los riesgos se estudian como contenidos de la presentación, sin inferir normativa vigente ni comparaciones actuales de productos.

## Límites y precauciones de lectura de las fuentes

- La profundidad `medium` alcanza el formalismo central de las familias desarrolladas. No incluye pruebas completas de aproximación universal, equivalencia lineal con PCA, derivación exhaustiva de KL gaussiana ni detalle de implementación de cada arquitectura.
- OFF-021 enumera técnicas de entrenamiento en p. 42 y presenta DBN en p. 58; esa cobertura no basta para enseñar sus algoritmos completos. Se ubican sus propósitos y se registra el límite.
- La expresión de Softmax de OFF-001, pp. 181 y 196, muestra el mismo índice en el numerador y dentro de la suma del denominador. Al enseñar, revisar la indexación con el requisito de normalización y los diagramas; no copiar esa escritura mecánicamente. En VAE, pp. 161-167, distinguir explícitamente desvío, covarianza y log-varianza al interpretar los símbolos del apunte. La expresión de KL de p. 169 también debe cotejarse con sus propiedades y con el desarrollo de pp. 163-165 por la discrepancia de signo visible en el texto.
- El argumento de profundidad se estudia como motivación de las fuentes; no se interpreta como garantía de que cualquier red más profunda sea más fácil de entrenar o generalice mejor. Comparar OFF-001, p. 149, con las dificultades señaladas en OFF-021, pp. 39-42.
- No se incluyen recomendaciones de herramientas, rankings actuales, normativa ni desarrollos posteriores a las fuentes. Los trabajos prácticos no se utilizan como autoridad académica ni se resuelven en este recorrido.
