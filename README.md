# Deforestacion

## El problema

La deforestacion es un proceso en el cual se destruye la vegetacion de un bosque. Puede haber numerosas causas para que esto ocurra:

- Naturales: erupciones volcanicas, inundaciones, indencios provocados por causas naturales.

- Causas humanas: incendios provocados, uso de terrenos para la edificacion, uso de los materiales (madera, plantas...), ect..


Actualmente nos encontramos en una situacion mundialmente donde, debido a la deforestacion, tenemos: suelos aridos, perdida e bsques, aumenta del cambio climatico, extincon de una gran cantidad de especies, etc..


En la region amazonica que pertenece a Brasil se llevan realizando controles desde 2015 mediante un satelite. Actualmente (Abril 2022) acabamos de conocer la noticia de que en el primer trimestre de 2022 ya se ha alcanzado un nuevo record trimestral de deforestacion. **Desde enero se han perdido 941 kilometros cuadrados de selva tropical**. 

## Que podemos hacer

Tras conocer estos datos creemos que **hemos de convatir contra la deforestacion cuanto antes**. Para ello hemos querido clasificar imagenes via satelite obtenidas de la siguiente fuente: https://www.kaggle.com/competitions/planet-understanding-the-amazon-from-space/overview . Este dataset se que nos proporciona lo se ha extraido a partir de  https://www.planet.com/ donde se recoge el mayor dataset de imagenes satelite de la tierra.

## Nuestro proyecto

En nuestro proyecto podemos encontrar dos carpetas: data (contiene el dataset) y code (contiene los scripts de python).

**Si analizamos el contenido de la carpeta data podemos encontar el dataset:**

- train-jpg : carpeta que contiene todas las imagenes del dataset

- csv_tags : carpeta que contiene el csv con la clasificacion multiclass de las imagenes del dataset

- models : modelos guardados para poder predecir que tags se le pueden asocial a una imagen



**Si analizamos el contenido de la carpeta code encontramos los ficheros:**

- eda.ipynb : script de python realizado en un notebook que contiene el analisis exploratorio de nuestro dataset. Gracias a este script hemos podido llegar a entender la complejidad de nuestro reto: un reto de clasificacion de imagenes multiclass. Se han analizado las imagenes qcontenidas y un fichero "train_v2.csv" que contenia la clasificacion de las imagenes. Una imagen puede estar clasificada con varios tags. Se ha podido comprobar que hay una pequeña cantidad de tags que engloban la mayoria de imagenes: primary, clear, agriculture, road, water, partly_cloudy. Asi mismo se ha realizado un analisis de los tipos de tags que podiamos encontrar mediante heatmaps.

- fastai.ipynb : script de python realizado en un notebook donde se han realizado 3 modelos predictivos con la libreria fast.ai. Se ha realizado un primer modelo con la red preentrenada ResNet utilizando 18 capas. Desde la segunda iteracion (segundo epoch) podemos alcanzar una precision de 0.906 en nuestro conjunto de test, obteniendo un 0.943 de precision durante el entrenamiento. Esta CNN tarda en ejecutar aproximadamente 13 minutos cada epoch. Posteriormente se ha probado a crear un modelo con la misma red preentrenada utilizando 34 capas. El objetivo de este modelo es poder ver si, al utilizar mas capas podemos obtener una mayor precision realizando menos epoch. El resultado obtenido es que obtenemos valores similares de precision en los conjuntos de train y de test pero cada epoch tarda aproximadamente el doble de tiempo en ejecutarse. Por ultimo hemos probado a realizar un modelo con la red preentrenada densenet-121. Este modelo lo hemos tenido que parar antes de que terminara de ejecutarse de forma manual tras el primer epoch. Tras la primera iteracion si que conseguiamos un 0.02 aproximadamente de mayor precision frente a las primeras iteraciones realzadas con la CNN ResNet. Sin embargo estamos comparando tiempos de ejecucion de cada epoch de 13 minutos (resnet18) frente a 43 minutos (densenet). El modelo elgido como mejor para este problema utilizando la libreria fast.ai es el generado mediante la red preentrenada resnet18.


Hemos realizado una comparacion entre estas dos librerias ya que son de las mas utiizadas a la hora de tratar imagenes. FAST.AI y KERAS tienen arquitecturas similares ........ conclusiones



Este trabajo ha sido realizado por:
    - Isabel Sutil Martin
    - Ana Blasi Sanchiz