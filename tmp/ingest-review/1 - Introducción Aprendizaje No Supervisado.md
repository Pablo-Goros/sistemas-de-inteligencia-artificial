# Extracted source: 1 - Introducción Aprendizaje No Supervisado

## Page 1

APRENDIZAJE
NO SUPERVISADO
Introducción
Sistemas de Inteligencia Artiﬁcial - 2026

## Page 2

TABLA DE CONTENIDOS
01. INTRODUCCIÓN
02. MODELO DE
KOHONEN
03. MODELO DE
HOPFIELD
04.
05.
06.
2
AUTOVALORES Y
AUTOVECTORES
COMPONENTES
PRINCIPALES
REGLA DE OJA Y
SANGER

## Page 3

01
INTRODUCCIÓN
¿Qué es el Aprendizaje
No Supervisado?
3

## Page 4

4
APRENDIZAJE
SUPERVISADO
APRENDIZAJE
NO SUPERVISADO
El agente tiene acceso a
etiquetas
Conocimiento de la
variable de respuesta
Tareas bien deﬁnidas que
no cambian mucho en el
tiempo
Clasiﬁcación y regresión
La  variable de respuesta no
es información disponible
Puede resolver problemas
menos deﬁnidos
Clustering, Asociación y
Reducción de Dimensionalidad
SUPERVISADO vs NO SUPERVISADO

## Page 5

¿QUÉ ES EL
APRENDIZAJE NO SUPERVISADO?
No se conoce el valor de verdad
¿Cómo sabemos si los resultados que obtenemos son signiﬁcativos?
Construye modelos de predicción
Estrategias para obtener características o patrones y sacar conclusiones
5

## Page 6

6
EJEMPLO
Para una investigación se seleccionan al azar 3500 pacientes hipertensos sobre los que
se midieron las siguiente variables:
● Edad
● Duración de los síntomas (cantidad de días)
● Colesterol (mg/dl)
● Sexo
● Peso (kg)
● Presión arterial media (mm Hg)
● Medida del estrés
Se desea saber cuál es el riesgo de que un paciente presente una enfermedad arterial

## Page 7

7
EJEMPLO
Si consideramos 2 variables:
● Presión
● Edad
¿Qué nos dice este gráﬁco?
La dimensión inicial
del problema es 7.

## Page 8

8
EJEMPLO
Si consideramos 3 variables:
● Presión
● Edad
● Peso
¿Qué nos dice este gráﬁco?
La dimensión inicial
del problema es 7.

## Page 9

9
EJEMPLO
¿Se puede deﬁnir un índice que cuantiﬁque la situación
de riesgo cardíaco de un paciente con hipertensión arterial,
teniendo en cuenta todas las variables?
PROBLEMAS A RESOLVER:
● Agrupamiento o Clustering
● Asociaciones
● Reducción de dimensionalidad

## Page 10

10
APRENDIZAJE NO SUPERVISADO
MODELO
INPUT
Datos no etiquetados
OUTPUT
Datos similares agrupados

## Page 11

11
CLUSTERING
● Agrupar observaciones de forma tal que el grado de
similitud entre miembros de un mismo grupo sea lo
más fuerte posible
● Identiﬁcar similitudes entre los datos y asignarlos a
un grupo (cluster)
● Implica deﬁnir similitud

## Page 12

12
CLUSTERING
Ej:
Medicina: Datos: edad, sexo, peso, colesterol ¿hay ciertos
patrones en el conjunto de entrada que me indican si
responderá bien ante cierto tratamiento médico?
Detección de anomalías: identiﬁcar outliers dentro de los
clusters
Estrategias de marketing: ¿a qué tipos de usuarios está
dirigida mi aplicación y cómo puedo mejorar su
experiencia?

## Page 13

13
ASOCIACIÓN
● Encontrar relaciones entre los atributos del conjunto
de datos

● Memorias Asociativas:
El almacenamiento y recuperación de información
por asociación con otros datos
Ej:
Modelo de Hopﬁeld

## Page 14

14
ASOCIACIÓN
Aplicaciones
Sistemas de recomendación
● identiﬁcar qué artículos los clientes compran juntos
con frecuencia. Se puede utilizar para mejorar la
organización de productos y aumentar las ventas
Identiﬁcar relaciones entre diferentes síntomas y
enfermedades

## Page 15

15
REDUCCIÓN DE DIMENSIÓN
La reducción de la dimensionalidad proyecta
el conjunto de datos en un espacio menor,
dejando de lado las características menos
relevantes
Ej: PCA, Autoencoders
N
variables
2
variables

## Page 16

16
REDUCCIÓN DE DIMENSIÓN
Aplicaciones
 ● Identiﬁcar qué variables afectan más a cada
país para luego invertir (educación, agricultura,
inﬂación, etc)
● Comprimir una imagen y reducir el costo
computacional
N
variables
2
variables

## Page 17

17
PROBLEMAS DEL APRENDIZAJE SUPERVISADO
Etiquetas
Es costo generar/obtener un gran conjunto de datos donde todos estén etiquetados
El Aprendizaje No Supervisado no necesita etiquetas

Dimensionalidad
Cuando tenemos muchas características (features) es costoso encontrar un buena aproximación
El Aprendizaje No Supervisado permite la reducción de la dimensionalidad
Outliers
La calidad del conjunto de datos es importante. Si se ignoran los outliers aprenderá de ellos y
cometerá más errores
El Aprendizaje No Supervisado agrupa los outliers por un lado y el resto los datos por el otro

## Page 18

18
APLICACIONES

[Very little text was extracted; inspect the original page for visual content.]

## Page 19

19
EJEMPLO
Variables:
● Positive Actions: Likes and Saves
● Negative Actions: “See Fewer Posts Like This” (SFPLT)
Modelo: ResNets

## Page 20

20
EJEMPLO
TU COMPORTAMIENTO
● Playlists
● Skips
● Favorites
● Shares
● Listening frequency
● Listening time
COMPORTAMIENTO DE OTROS
● Playlists
● Trending artists
● Artists similar to your
favorite artists
● New songs of your liked
artists
AUDIO
● Song spectogram
● Tempo
● Loudness
● Amplitude
● Lyrics
Modelo: CNN

## Page 21

21
REDES NEURONALES
En esta materia se estudiarán Métodos de Aprendizaje No Supervisado
usando modelos de Redes Neuronales
● Red de Kohonen
● Red de Hopﬁeld
● Modelo de Oja
● Modelo de Sanger

## Page 22

BIBLIOGRAFÍA
22
[1] McKay D.J.C. Hopﬁeld Networks. Information Theory, Inference and Learning
Algorithms, Cambridge, 2003.
[2] Anders Krogh John Hertz and Richard Palmer. Introduction to the Theory of Neural
Computation. Addison-Wesley, 1991.
[3] T. Kohonen. Self-organized formation of topologically correct feature maps. Biological
Cybernetics, 1(43):59–69, 1982.
[4] T. Kohonen. The self-organizing map. Neurocomputing, pages 1–6, 1998.
[5] Hiran, K. K., Jain, R. K., Lakhwani, K., & Doshi, R. (2021). Machine Learning: Master
Supervised and Unsupervised Learning Algorithms with Real Examples (English Edition).
BPB Publications.
