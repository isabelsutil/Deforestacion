# Deforestacion

## El problema

La deforestacion es un proceso en el cual se destruye la vegetacion de un bosque. Puede haber numerosas causas para que esto ocurra:

- Naturales: erupciones volcanicas, inundaciones, indencios provocados por causas naturales.

- Causas humanas: incendios provocados, uso de terrenos para la edificacion, uso de los materiales (madera, plantas...), ect..


Actualmente nos encontramos en una situacion mundialmente donde, debido a la deforestacion, tenemos: suelos aridos, perdida e bsques, aumenta del cambio climatico, extincon de una gran cantidad de especies, etc..


En la region amazonica que pertenece a Brasil se llevan realizando controles desde 2015 mediante un satelite. Actualmente (Abril 2022) acabamos de conocer la noticia de que en el primer trimestre de 2022 ya se ha alcanzado un nuevo record trimestral de deforestacion. **Desde enero se han perdido 941 kilometros cuadrados de selva tropical**. 


## Que podemos hacer

Tras conocer estos datos creemos que **hemos de convatir contra la deforestacion cuanto antes**. Para ello hemos querido clasificar imagenes via satelite obtenidas de la siguiente fuente: https://www.kaggle.com/competitions/planet-understanding-the-amazon-from-space/overview . Este dataset se que nos proporciona lo se ha extraido a partir de  https://www.planet.com/ donde se recoge el mayor dataset de imagenes satelite de la tierra.

Se ha decidido crear dos modelos a partir de dos librerías muy utilizadas en el mundo de Deep Learning para la casificación de imágenes: Keras y Fastai. Al final del proyecto se comentará sobre qué librería es más óptima para este trabajo. FAST.AI es una librería enfocada a principiantes y, por lo tanto, es una librería muy facil y intuitiva de utilizar. En cambio, Keras permite saber más en profundidad sobre la arquitectura del modelo que se esta creando.

Con ambas librerías se utilizarán las redes neuronales convolcionales. Aun así, con FAST.AI se utilizará un modelo preentrenado y con Keras se creará un modelo de cero. 

## Nuestro proyecto

En nuestro proyecto podemos encontrar dos carpetas: data (contiene el dataset) y code (contiene los scripts de python).

**Si analizamos el contenido de la carpeta data podemos encontar el dataset:**

- train-jpg : carpeta que contiene todas las imagenes del dataset

- csv_tags : carpeta que contiene el csv con la clasificacion multiclass de las imagenes del dataset

- models : modelos guardados para poder predecir que tags se le pueden asocial a una imagen



**Si analizamos el contenido de la carpeta code encontramos los ficheros:**

- eda.ipynb : script de python realizado en un notebook que contiene el analisis exploratorio de nuestro dataset. Gracias a este script hemos podido llegar a entender la complejidad de nuestro reto: un reto de clasificacion de imagenes multiclass. Se han analizado las imagenes qcontenidas y un fichero "train_v2.csv" que contenia la clasificacion de las imagenes. Una imagen puede estar clasificada con varios tags. Se ha podido comprobar que hay una pequeña cantidad de tags que engloban la mayoria de imagenes: primary, clear, agriculture, road, water, partly_cloudy. Asi mismo se ha realizado un analisis de los tipos de tags que podiamos encontrar mediante heatmaps.

- fastai.ipynb : script de python realizado en un notebook donde se han realizado 3 modelos predictivos con la libreria fast.ai. Se ha realizado un primer modelo con la red preentrenada ResNet utilizando 18 capas. Desde la segunda iteracion (segundo epoch) podemos alcanzar una precision de 0.906 en nuestro conjunto de test, obteniendo un 0.943 de precision durante el entrenamiento. Esta CNN tarda en ejecutar aproximadamente 13 minutos cada epoch. Posteriormente se ha probado a crear un modelo con la misma red preentrenada utilizando 34 capas. El objetivo de este modelo es poder ver si, al utilizar mas capas podemos obtener una mayor precision realizando menos epoch. El resultado obtenido es que obtenemos valores similares de precision en los conjuntos de train y de test pero cada epoch tarda aproximadamente el doble de tiempo en ejecutarse. Por ultimo hemos probado a realizar un modelo con la red preentrenada densenet-121. Este modelo lo hemos tenido que parar antes de que terminara de ejecutarse de forma manual tras el primer epoch. Tras la primera iteracion si que conseguiamos un 0.02 aproximadamente de mayor precision frente a las primeras iteraciones realzadas con la CNN ResNet. Sin embargo estamos comparando tiempos de ejecucion de cada epoch de 13 minutos (resnet18) frente a 43 minutos (densenet). El modelo elgido como mejor para este problema utilizando la libreria fast.ai es el generado mediante la red preentrenada resnet18.

- keras.ipynb : En este script de Python se han realizado dos modelos que se diferencian en el tamaño de las imágenes que se pasan a los modelos. En el primero el tamaño es de 82x82 y el segundo es de 32x32. Como la librería de Keras lo permite, se ha decidido crear los modelos de cero utilizando las redes convolucionales. Al modelo, primero se ha decidido que la capa de entrada fuera una capa convolucional de 32 filtros con una size del kernel de 3x3, la función de activación es relu, aquí es donde se define el input_size. Después, se añade otra capa convolucional pero esta de 64 filtros. Luego se realiza el MaxPooling para quedarnos con la información que más importe. Para evitar sobre entrenamiento hemos añadido una capa de Dropout. Después añadimos una capa Dense de 128 con una función de activación de relu. Añadimos otra capa Dropout por la misma razón que la de antes. Por último, añadimos la ultima capa Dense de 17 (como el número de labels) y de función de activación de Softmax. Si los modelos se entrenan con la GPU de colab se entrenan muy rápido. En el caso del modelo de 82x82, el primer epoch ha tardado 43 seg y los demás alrededor de 28 seg. El otro modelo ha tardado mucho menos, 7 segundos el primer epoch y el resto 4 seg cada uno. Aunque se ha explicado en más profundidad en el notebook, uno de los problemas que se ha encontrado ha sido en procesar el dataset. Al final, se ha tenido que pasar las imágenes a arrays y debido al tamaño del dataset este procesado ha tardado 1h y 30mins. Sobre los accuracies, no han sido tan buenos como cuando se ha entrenado el modelo con la librería Fastai. En el modelo de tamaño 82x82 se ha conseguido un accuracy de 0,70. No hemos conseguido que funcionara el modelo de 32x32 porque solo se ha conseguido un accuracy de 0,05. No se ha tenido tiempo de analizar en más profundidad la razón de este accuracy tan bajo. En futuros trabajos se buscara un mejor modelo para este size.

Hemos realizado una comparacion entre estas dos librerias ya que son de las mas utiizadas a la hora de tratar imagenes. 
Si se tubiera que elegir una librería para entrenar un modelo con este dataset se elegiría la librería de FAST.AI. Es muy fácil de utilizar y se ha obtenido un mejor accuracy que con la librería de Keras. Además, se considera que el dataset estaba adaptado a las especificaciones de las funciones de FAST.AI, por lo que ha costado bastante cuando se ha querido utilizar las de Keras.

Este trabajo ha sido realizado por:
    - Isabel Sutil Martin
    - Ana Blasi Sanchiz
