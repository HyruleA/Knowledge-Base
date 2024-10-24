**ARTÍCULO**  [Reviewing 25 years of continuous sign language recognition research: Advances, challenges, and prospects](https://doi.org/10.1016/j.ipm.2024.103774)

### ¿Por qué es importante este artículo?
Se utilizaron las siguientes bases de datos como fuentes de información: Google Scholar, ProQuest, Scopus e IEEE Explore. La investigación inicial dio como resultado 306 artículos, que posteriormente se redujeron a 126 tras excluir los artículos aislados sobre el reconocimiento del habla. Estudios que no se centran en el reconocimiento de Lenguaje de Señas y estudios no escritos en inglés. Revisión exhaustiva de todas las publicaciones relevantes hasta marzo de 2024.

---
# Lenguaje de Señas 
El lenguaje de señas es un lenguaje visual que utiliza una combinación de:
* <span style="color:green">gestos manuales</span>, gestos con las manos
	* La forma (posición de los dedos) 
	* Orientación de la palma
	* Posición
	* Movimiento
* <span style="color:green">gestos no-manuales</span>
	* movimientos corporales (posturas)
	* y expresiones faciales (nodos principales de la cabeza y patrones de labios)
para comunicarse.

<span style="color:#33ffb5"><em>usar los gestos no-manuales para reforzar el reconocimiento</em></span>

Países que comparten lenguaje hablado no necesariamente comparten lenguaje de señas, como ejemplo los lenguajes de señas americano ASL y el británico BSL son distintos. En México existen más de 8 en este trabajo nos enfocaremos en el central la que se usa para noticias y los informes de gobernación. [FALTA REFERENCIA]


# Reconocimiento del Lenguaje de Señas 
Sign language recognition (SLR)

Es la tarea de reconocer e interpretar gestos (el mapeo de gestos a palabras de lenguaje hablado)  ya sea desde videos o imágenes. El término <span style="color:yellow">gloss</span> es la etiqueta, la palabra de lo que significa la seña. Esta tarea involucra técnicas como:
* Reconocimiento de patrones.
* Visión por computadora
* Procesamiento del Lenguaje Natural (NLP)

Los sistemas de reconocimiento de lenguaje se pueden clasificar en 3 categorías principales:
* <span style="color:green">Deletreo con los dedos</span> 
	letras, números y deletreo de palabras que no tienen seña, generalmente son estáticos sin movimiento y basta una imagen para representarla.
* <span style="color:green">Aislado</span>  
	palabras aisladas, equivalentes a palabras del lenguaje hablado, pueden ser estáticas (una imagen) o dinámicas (un video corto)
* <span style="color:green">Continuo </span> 
 	estos sistemas pueden reconocer una serie de señas en un stream de video, incluye reconocer señales estáticas como dinámicas.
	 
<span style="color:#33ffb5"><em>se está usando un sistema aislado, necesitamos planear un continuo</em></span>

## Marco Teórico
¿qué se ha hecho en términos de Reconocimiento Continuo del Lenguaje de Señas?

Trabajos anteriores: 

![[Trabajos sobre reconocimiento continuo.png]]

Taxonomía del reconocimiento continuo de lenguaje de señas **CSLR**

![[Taxonomia del reconocimiento continuo.png]]


## Reconocimiento Continuo del Lenguaje de Señas (CSLR)
Se refiere al proceso de reconocer e interpretar los gestos del lenguaje de señas realizados de forma continua sin pausas entre los señas. 

La meta es mapear (relacionar) un conjunto de imagenes (frames) 𝑋 = {𝑥1, 𝑥2, 𝑥𝑛} a un conjunto de <span style="color:yellow">glosses</span>  𝑌 = {𝑦1, 𝑦2, 𝑦𝑚}, donde 𝑛 ≠ 𝑚. El conjunto de gloesses debe estar ordenado de acuerdo al orden en las imágenes.

Este proceso implica dos tareas: <span style="color:green">establecer límites temporales</span> a partir de secuencias de vídeo débilmente anotadas y <span style="color:green">reconocer las señas  mostradas</span>.

Los modelos basados en Deep Learning se componen de tres módulos clave:
* <span style="color:green">espacial</span>, extrae caraterísticas espaciales del video de entrada.
* <span style="color:green">temporal</span>, modela los aspectos temporales de la secuencia de la señal.
* de <span style="color:green">alineación</span>, controla el aprendizaje entre las secuencias y las etiquetas gloss para producir la secuencia adecuada de glosses.


![[Modulos clave para el CSLR.png]]
### Métricas
Se usan el 
* <span style="color:green">Word Error Rate (WER)</span> 
	cuenta el número necesario de operaciones de supresión, inserción y sustitución para transformar la secuencia de etiquetas prevista en la secuencia de etiquetas real.
* <span style="color:green">Accuracy</span> 
	cuenta el número de signos identificados correctamente sobre el número total de signos de la frase.
* y <span style="color:green">The Bilingual Evaluation Understudy BLUE</span>
	Consiste en realizar comparaciones de n-gramas entre la frase predicha y la frase verdadera.

## Traducción del Lenguaje de Señas (SLT)
El Reconocimiento Continuo del Lenguaje de Señas (CSLR) y la Traducción del Lenguaje de Señas (SLT) están muy relacionadas. Los sistemas CSLR producen una secuencia de etiquetas de señas en el mismo orden en que fueron firmados en el vídeo. Este orden suele ser diferente de la estructura de las frases del lenguaje natural. SLT es una tarea de NLP que amplía CSLR traduciendo los signos reconocidos por CSLR a un lenguaje natural hablado o escrito. 

Se pueden utilizar dos enfoques para integrar el SLT con el CSLR: <span style="color:green">sign2gloss2text</span> y <span style="color:green">sign2text</span>. En el primer enfoque, se aprovecha un modelo CSLR para producir glosses intermedios y el sistema SLT procesa estas glosas para generar un texto coherente y gramaticalmente correcto en la lengua de llegada. Por otro lado, el enfoque sign2text omite el paso intermedio del gloss y traduce directamente los enunciados de la lengua de señas a texto en lengua natural.

### Retos
* <span style="color:green">Captura de características</span> de multiples aspectos como la posición del cuerpo, movimientos de la mano y expresiones faciales.
* <span style="color:green">Independencia</span> de la persona que realiza las señas. Diferentes apariencias: color de la piel, tipo de cuerpo, altura, la dominancia de alguna de las manos (si es diestro o surdo), velocidad con la que realiza las señas, que tan bien ejecuta las señas.
* <span style="color:green">Segmentación temporal</span>, detección de límites de las señas . 
* <span style="color:green">La epéntesis de movimiento</span>  es una secuencia no gestual que aparece en las frases de la lengua de señas cuando se pasa de una seña a otra.
* <span style="color:green">Efecto co-articulación</span>  se refiere a los cambios en el comienzo y el final de una seña basados en la seña anterior y la siguiente. 
* <span style="color:green">Dependencia entre señas</span> modelado de la secuencia de señas, es importante en el CSLR un modelo que capture las relaciones de larga distancia temporal con información semántica de alto nivel.
* <span style="color:green">Deletreo con dedos</span>, en el mundo real muchas veces se incluyen deletreos en las conversaciones, ser capaz de distinguirlas es también un reto grande.

### Conjunto de Datos

