241104 

La implementación actual del sistema nos limita a distinguir de entre 6 preguntas, usando  28 señas. Se asume un porcentaje de efectividad del 60% para detectar el gloss correspondiente a la seña en tiempo real. 

La meta a muy corto plazo y para fines de demostración de la app, es utilizar los resultados alcanzados hasta el momento, y definir una eurística  para llevar el conjunto de gloss detectados a una de las 6 preguntas. 

Se analizaron los siguientes escenarios: 


## BERT
usando el transformer preentrenado de Hugging Face bert-base-uncased, como tokenizer y como modelo para clasificar se puede hacer fine tunning para adecuarlo a las necesitades pero se cuenta con muy pocos ejemplos de enetrenamiento y el accouracy de la clasificación decae rápidamente a medida que se aumentan las clases, el fine tunning mejora pero se corre el riesgo de hacer overfit.  Los resultados del accouracy van del 60 al 80% pero no nos dicen mucho por el bajo número de ejemplos de entrenamiento.


## Zero-shot
Esta eurística no requiere datos de entrenamiento y de ser necesario se puede hacer fine tunning. Se usó el modelo **dccuchile/bert-base-spanish-wwm-uncased**, prentenado con textos en español por una institución chilena.

los resultados fueron como el ejemplo siguiente con bajos valores en los scores y el mayor score no corresponde a la pregunta que le corresponde.

````
'sequence': 'legal donde puedo saber derecho', 
'labels': [ '¿cómo reclamo una herencia?', 
			'¿cómo puedo hacer una denuncia?', 
			'¿cómo puedo hacer para pagar mis impuestos?', 
			'¿cómo encontrar asistencia legal gratuita?', 
			'¿dónde puedo encontrar un abogado?', 
			'¿dónde puedo saber mas de mis derechos?'], 'scores': [0.1859944462776184, 0.1752515584230423, 0.17047464847564697, 0.16164320707321167, 0.15469540655612946, 0.15194071829319]

````



## Búsqueda Semántica 
Usando los transformers disponibles en HuggingFace 
Usando sentence_transformers como encoder para cada conjunto de gloss y a través de la decomposición PCA se pueden graficar en 2D y se observa que no es un problema linealmente separable. Cada punto es un conjunto de gloss que corresponden a 1 de las 6 Preguntas (colores) posibles. La estrella es la representación de una de las preguntas, y no se ve un grupo claro de puntos de un mismo color que la rodee.  


![[Similitud semántica usando PCA.png]]


# Chat Llama y Gemini 
Asumiendo que se paga/habilita el uso de la API para interactuar con estos modelos, el resultado supera al de las anteriores pruebas ya que sin entrenar en la mayoría de los escenarios se ecnuentra la pregunta correspondiente, es débil por supuesto cuando el conjunto de gloss es pequeño y sin contexto. 
````
como mis como
````


# Conclusiones
Sin hacer demasiados ajustes parece que la inteligencia artificial generativa nos da mejores resultados, Memo reporta que con OpenIA se tienen aun mejores resultados porque sorprende con conjuntos de gloss pequeos como el citado anteriorrmente, por el momento se opta por esa solución de paga.