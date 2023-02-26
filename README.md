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



### Feature Extraction



### Topic Modelling
Para el modelado de tópicos se ha hecho uso de limpieza mediante spaCy y PoS de spaCy, esto debido a que se consideró que tendrá un mayor rendimiento considerando spaCy SM utiliza GloVe.

Para NMF se hace uso de scikit-learn, se prueba con n = 4 y se establece que no es un valor óptimo, a la vez se prueba con n = 5 y se aprecia un mejor resultado, con ello y mediante evaluación de las sentencias RAW se llega a la conclusión de los siguientes tags:
* Topic 0: Otros (Others)
* Topic 1: Reporte de robos (Theft/Dispute Reporting)
* Topic 2: Servicio de cuenta de banco (Bank Account services)
* Topic 3: Tarjeta de crédito (Credit card or prepaid card)
* Topic 4: Prestamos Hipotecarios y Otros Prestamos (Mortgage/Loan)

También se ha hecho la prueba con BERTopic, una red que utiliza transformers y tiene mayor rendimiento, pudiendo otorgar un poco más de información, se evalua el resultado del procesamiento de datos RAW como también con la limpieza, siendo coherente que con la limpieza aún con redes tan potentes se obtiene un resultado mucho mejor y apropiado, BERTopic utiliza HDBSCAN para estimar la cantidad de tópicos, sin embargo se ha visto prudente utilizarlo con n = 5.

### Model Building



### Model Inference



### Code readability and conciseness


## Conclusiones


