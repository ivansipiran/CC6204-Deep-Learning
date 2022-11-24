# Hackaton Deep Learning 2022

En esta actividad intentaremos resolver un problema de clasificación multimodal. En un problema de clasificación multimodal, cada pieza de información viene en diferentes representaciones (imágenes, texto, audios, etc) y la idea es determinar cómo usar esos datos para un problema de clasificación. 

En este caso trabajaremos con un dataset que contiene datos sobre especies de pájaros.

## Dataset CUB
Este dataset contiene datos para clasificar a una determinada ave dentro de su especie. El dataset consiste de 200 clases de especies y contiene tanto imágenes como descripciones textuales de cada instancia.

El dataset lo pueden descargar [aquí](https://drive.google.com/file/d/1_0i3sZG5y4w9mbTBokCt-Gs5Ny_axLyr/view?usp=share_link). Pueden usar [gdown](https://github.com/wkentaro/gdown) para descargar el archivo en sus notebooks usando el ID=1_0i3sZG5y4w9mbTBokCt-Gs5Ny_axLyr. Se puede usar el commando:

~~~
!gdown --id '1_0i3sZG5y4w9mbTBokCt-Gs5Ny_axLyr&confirm=t'
~~~


El dataset contiene dos folders y cuatro archivos de texto. 

*  El folder *images* contiene un subfolder por cada clase de especie y dentro de cada subfolder  están las imágenes de las aves de esa especie.
* El folder *text* contiene un subfolder por cada clase de especie y dentro de cada subfolder están los archivos de texto con las descripciones textuales de las aves. Un punto importante es que existen 10 descripciones textuales por cada ave. Los nombres de archivos de las imágenes y de las descripciones textuales concuerdan para facilitar extraer la información.
* El archivo *classes.txt* contiene los nombres de las clases del problema y un índice numérico asociado a cada clase.
* El archivo *images.txt* contiene los nombres de las imágenes y un índice numérico asociado a cada imagen.
* El archivo *image_class_labels.txt* asocia un índice de imagen con un índice de clase. Esto permite saber a qué clase pertenece una determinada imagen.
* El archivo *train_test_split.txt* nos indica qué imagen debe ser usada para *train* (valor 1) y qué imagen debe ser usada para test (valor 0).

## El problema
El problema consiste en entrenar un modelo que clasifique instancias del dataset CUB de la mejor manera posible. Algunas preguntas que podrían guiar nuestro desarrollo son:

* Se podrá obtener un buen performance de clasificación solo usando las imágenes del dataset? Este tipo de problema sería el clásico problema de clasificar imágenes.
* Se podrá obtener un buen performance de clasificación solo usando los textos del dataset? Este tipo de problema sería el clásico problema de clasificar texto.
* Se podrá obtener un mejor performance si combino la información en un modelo multimodal? Cómo construyo un modelo multimodal que reciba una imagen y un texto y clasifique la instancia con su respectiva especie? Hint: piense en cómo una red neuronal (la que sea) es simplemente una función que recibe un dato y genera una representación de alto nivel (vector característico) de ese dato. Una red CNN podría hacerse cargo de calcular la representación de una imagen y una red RNN podría hacerse cargo de calcular la representación del texto. Finalmente concateno ambas representaciones y entreno un MLP final que hace la clasificación. 


## Experimentación
Como el dataset es grande y los recursos de computación son muy limitados, una estrategia para hacer los experimentos es tomar una muestra más pequeña de datos para ir probando las ideas. Para esta estrategia, éstas son dos ideas válidas:

* Tomar menos instancias por cada clase para el desarrollo y solo dejar el dataset final para hacer el entrenamiento final y la evaluación final con testing.
* Tomar menos clases para el desarrollo inicial y solo dejar el dataset final para hacer el entrenamiento final y la evaluación final con testing.

Ambas estrategias nos permiten lidiar con los recursos limitados que tenemos, pero cuáles son sus ventajas o desventajas? Si usas alguna de estas estrategias, puedes comentar este punto en tu desarrollo final.

## Métrica de Evaluación
La métrica que se debe reportar es el accuracy en conjunto de test.
