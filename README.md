# Proyecto 2 - Complaints
## Tabla de contenido


## Introducción



## Personas involucrudas en el proyecto
* Alicia Zamorano zamoranoalicia@gmail.com
* Cesar Quiroga cesar.a.quiroga.c@gmail.com
* Juan Carlos Peralta juancarlosperaltaolivera@gmail.com
* Nilton Apaza nilton.apcon@gmail.com

## Métodos y modelos usados
* Averaged Perceptron Tagger
* Punkt
* Wordnet
* GloVe
* TF-IDF
* BERTopic
* NMF
* Regresión logística
* Árbol de decisión
* Bosque aleatorio
* Naive Bayes

## Tecnologías
* Python
* Pandas
* Numpy
* Sklearn
* Google colab
* NLTK
* spaCy
* BERTopic

## Descargar y configurar
### Prerrequisitos
* Este proyecto se puede ejecutar utilizando colab.research desde Google https://drive.google.com/file/d/1QF1EFNGXJHrMG8wlAqTt7mAIftrrQppZ/view?usp=sharing o anaconda navigator

### Cómo ejecutar

El código fuente puede ser clonado desde este repositorio usando Git:

1. Abrir la terminal favorita (Unix, Linux o Macos), como ser Terminal, Command, Console, iTerm2, etc.

2. Clonar el repositorio

```
git clone <GITHUB_REPO_URL>
```

3. Abrir el archivo ** *.ipynb** el mismo es un notebook que puede ser utilizando en Anaconda o Python con la dependencia de Jupyter instalada.

```
jupyter notebook <NLP - Clasificacion Automatica de Tickets.ipynb>
```

### Data Reading / Data Understanding



### Data Cleaning



### Data Preprocessing



### Data Visualization

Para la visualizacion de datos se realizó Análisis exploratorio de datos para familiarizarse con los mismos.
Se hizo la visualizacion de datos de acuerdo a los caracteres de longitud segun las quejas que se tenian dentro del archivo o dataset .Uilizando el conglomerado de palabras  se realizo el objeto TF-IDF para vectorizar y ajustar el dataset para encontrar las palaabras frecunetes y otras que son escazas o raras dentro del dataset con ello determinamos los n-gramas con el proposito  de obtener el conjunto de caracteristicas (palabras) en el vector.
Estos pasos nos permitirán utilizar para la extraccion de  información de los datos en el dataset de tickets y visualizarla. Tambien podremos ajustar los parámetros del vectorizer según las necesidades y preferencias que se requieren para los complaints. Por ultimo  realizaremos el uso de métodos de procesamiento de lenguaje natural, como la lematización o el filtrado de stop words para la clasificacion de texto, antes de aplicar Tf-Idf para obtener resultados más precisos dentro del proyecto.

### Feature Extraction

La extracción de características (feature extraction) nos permite realizar un proceso común en el análisis de datos y en el procesamiento del lenguaje natural. El fin de la extracción de características es transformar estos datos de entrada (en este caso el texto para el proposito del proyecto) en un conjunto de características que sean más relevantes y significativas para nuestro análisis del presente dataset.
El uso de max_df y min_df se realizo para el siguiente fin:
max_df se usó para eliminar términos que aparecen con demasiada frecuencia, también conocidos como "palabras vacías específicas dentro del cuerpo del texto" el promedio de max_df = 0.95 significa "ignorar términos que aparecen en más del 95% de las quejas"

min_df se usó  para eliminar términos que aparecen con poca frecuencia el promedio del min_df = 2 significa "ignorar términos que aparecen en menos de 2 quejas"


### Topic Modelling
Para el modelado de tópicos se ha hecho uso de limpieza mediante spaCy y PoS de spaCy, esto debido a que se consideró que tendrá un mayor rendimiento considerando spaCy SM utiliza GloVe, se guarda el dataset en complaints_cleaned.xlsx.

Para NMF se hace uso de scikit-learn, se prueba con n = 4 y se establece que no es un valor óptimo, a la vez se prueba con n = 5 y se aprecia un mejor resultado, con ello y mediante evaluación de las sentencias RAW se llega a la conclusión de los siguientes tags:
* Topic 0: Otros (Others)
* Topic 1: Reporte de robos (Theft/Dispute Reporting)
* Topic 2: Servicio de cuenta de banco (Bank Account services)
* Topic 3: Tarjeta de crédito (Credit card or prepaid card)
* Topic 4: Prestamos Hipotecarios y Otros Prestamos (Mortgage/Loan)

También se ha hecho la prueba con BERTopic, una red que utiliza transformers y tiene mayor rendimiento, pudiendo otorgar un poco más de información, se evalua el resultado del procesamiento de datos RAW como también con la limpieza, siendo coherente que con la limpieza aún con redes tan potentes se obtiene un resultado mucho mejor y apropiado, BERTopic utiliza HDBSCAN para estimar la cantidad de tópicos, sin embargo se ha visto prudente utilizarlo con n = 5.

### Model Building
***Regresión logística:*** es un modelo lineal que utiliza una función sigmoide para mapear la entrada a una probabilidad de pertenencia a una clase. El modelo de regresión logística se entrena utilizando la función de pérdida logarítmica y el método de descenso de gradiente. Se utiliza el parámetro max_iter para especificar el número máximo de iteraciones permitidas para la convergencia.

***Árbol de decisión:*** es un modelo no lineal que divide el espacio de entrada en regiones utilizando un conjunto de reglas de decisión basadas en las características de la entrada. El modelo de árbol de decisión se entrena utilizando un algoritmo que busca la mejor forma de dividir el espacio de entrada en regiones más homogéneas.

***Bosque aleatorio:*** es un modelo que combina varios árboles de decisión para mejorar la precisión y reducir el sobreajuste. El modelo de bosque aleatorio se entrena utilizando un conjunto de árboles de decisión y un método de muestreo aleatorio para seleccionar las características y las instancias utilizadas en cada árbol.

***Naive Bayes:*** es un modelo probabilístico que utiliza el teorema de Bayes para calcular la probabilidad de pertenencia a una clase dada una entrada. El modelo de Naive Bayes se entrena utilizando la suposición de independencia condicional entre las características de la entrada.

Las métricas de evaluación utilizadas son:

1. ***Precisión:*** es la proporción de instancias positivas que fueron clasificadas correctamente como positivas en comparación con el número total de instancias clasificadas como positivas (verdaderos positivos más falsos positivos). Se utiliza la función precision_score para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve la precisión como un número entre 0 y 1. La precisión ponderada es la precisión promedio ponderada por el número de muestras en cada clase. Se utiliza el parámetro average="weighted" para calcular la precisión ponderada.

2. ***Recall:*** es la proporción de instancias positivas que fueron clasificadas correctamente como positivas en comparación con el número total de instancias positivas (verdaderos positivos más falsos negativos). Se utiliza la función recall_score para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve el recall como un número entre 0 y 1. El recall ponderado es el recall promedio ponderado por el número de muestras en cada clase. Se utiliza el parámetro average="weighted" para calcular el recall ponderado.

3. ***F1 Score:*** es la media armónica de la precisión y el recall, y se utiliza para equilibrar ambos valores. Se utiliza la función f1_score para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve el F1 Score como un número entre 0 y 1. El F1 Score ponderado es el F1 Score promedio ponderado por el número de muestras en cada clase. Se utiliza el parámetro average="weighted" para calcular el F1 Score ponderado.

4. ***Exactitud (Accuracy):*** es la proporción de instancias que fueron clasificadas correctamente. Se utiliza la función accuracy_score para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve la exactitud como un número entre 0 y 1.

5. ***Matriz de Confusión:*** es una tabla que muestra el número de instancias que fueron clasificadas correctamente e incorrectamente por el modelo. Se utiliza la función confusion_matrix para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve una matriz de confusión.

6. ***Reporte de Clasificación:*** es una tabla que muestra las puntuaciones de precisión, recall y F1 Score para cada clase. Se utiliza la función classification_report para calcular esta métrica. Esta función toma como entrada las etiquetas verdaderas y predichas y devuelve un reporte de clasificación.

| Model               | Training Score | Validation Score | Accuracy | Precision | Recall   | F1 Score |
|---------------------|----------------|------------------|----------|-----------|----------|----------|
| Logistic Regression | 0.914038       | 0.923155         | 0.923155 | 0.927456  | 0.923155 | 0.923051 |
| Decision Tree       | 0.768472       | 0.785107         | 0.785107 | 0.785255  | 0.785107 | 0.785108 |
| Random Forest       | 0.755378       | 0.766066         | 0.766066 | 0.812939  | 0.766066 | 0.759560 |
| Naive Bayes         | 0.458464       | 0.459028         | 0.459028 | 0.717521  | 0.459028 | 0.349921 |

La tabla muestra los resultados de comparación de los cuatro modelos de aprendizaje automático entrenados en los datos de entrenamiento y validación.

La columna "Model" indica el nombre del modelo correspondiente. La columna "Training Score" indica el puntaje promedio de validación cruzada de 5 pliegues para el modelo en los datos de entrenamiento. La columna "Validation Score" indica el puntaje del modelo en los datos de validación. Las columnas "Accuracy", "Precision", "Recall" y "F1 Score" son métricas de evaluación relevantes utilizadas para evaluar la capacidad de clasificación del modelo. De acuerdo con los resultados de la tabla, se puede ver que el modelo de regresión logística es el mejor modelo, ya que obtuvo la puntuación más alta en las métricas de "Validation Score", "Accuracy", "Precision", "Recall" y "F1 Score". Los otros modelos obtuvieron puntuaciones más bajas en estas métricas, lo que sugiere que tienen un rendimiento inferior al modelo de regresión logística en el conjunto de datos de prueba.

La regresión logística tiene un alto puntaje de validación cruzada y de validación en los datos de entrenamiento y validación respectivamente, lo que sugiere que es un modelo estable y generaliza bien para datos nuevos. Por lo tanto, se puede elegir el modelo de regresión logística como el mejor modelo para clasificar las quejas en temas.

Utilizando dicho modelo para el entrenamiento se tiene los siguientes resultados:
* El modelo obtuvo un Accuracy de 0.92, lo que significa que el 92% de las quejas fueron clasificadas correctamente.
* El valor de Precision de 0.93 indica que cuando el modelo clasifica una queja como perteneciente a un tema en particular, el 93% de las veces esta clasificación es correcta.
* El valor de Recall de 0.92 indica que el 92% de las quejas pertenecientes a un tema en particular fueron identificadas correctamente por el modelo.
* El valor de F1 Score de 0.92 indica que el modelo tiene un buen equilibrio entre Precision y Recall.
* La matriz de confusión (Confusion Matrix) muestra que la mayoría de las quejas son clasificadas correctamente por el modelo, y que los errores de clasificación se concentran principalmente en los temas 1 y 2.
* El reporte de clasificación (Classification Report) proporciona una visión detallada de las métricas de evaluación para cada tema, incluyendo la precisión, recall y F1-score. Los valores más altos de estas métricas se observan en los temas 0, 1 y 2, mientras que los valores más bajos se observan en los temas 3 y 4.
* Por los resultados se puede concluir que el modelo tiene un buen desempeño en la clasificación de las quejas, con un alto porcentaje de casos clasificados correctamente, un buen equilibrio entre Precision y Recall, y un bajo número de errores de clasificación.

### Model Inference

Se utiliza el archivo random_complaints.csv para inferir los resultados usado el modelo elegido (regresión logística), por ejemplo para el siguiente texto: 

"jp morgan chase bank  an individual or group of individuals have accessed sensitive information and are now calling in to document fake reports on my name and have blocked me out of my checking account  its a collective group of individuals doing a mass fraud scheme and have simply targeted me for whatever hateful and spiteful reasons.".

Se indica que es del tópico 2: Bank Account services, lo cual es correcto.

### Code readability and conciseness

El código contempla comentarios en las secciones correspondientes, a la vez se tiene markdowns si es necesario ampliar el texto, se considera la misma indentación en todo el código y en lo mayor posible se mantiene el idioma español.

## Conclusiones y recomendaciones
Se puede concluir con lo siguiente:
* Tanto NLTK y spaCy son ideales para lemmatización
* Los procesos de entrenamiento sin GPU pueden demorar en exceso en estas tareas
* Es necesario el preprocesamiento de los datos como un componente crítico antes de aplicar modelos
* Los tópicos son fácilmente identificables utilizando BERTopic y NMF
* TF-IDF es esencial para las tareas, la mayoría de los modelos lo utilizan en algún punto
* La regresión logística fue el mejor modelo obtenible después de la evaluación dada
* Utilizar clustering y posteriormente entrenamiento supervisado es ideal para el procesamiento de quejas
* Se recomienda profundizar en nuevas redes que utilicen transformers, el dataset da para obtener mayor información y precisión con nuevos modelos
