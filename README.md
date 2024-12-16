# Trabajo_TD
Repositorio utilizado para la resolución de una tarea de aprendizaje sobre documentos que contienen recetas de cocina de todo el mundo.

# **Introducción**
El conjunto de datos con el que se va a trabajar consta de 20.130 recetas. Estas presenta diferentes atributos que las definen: instrucciones para hacer la receta (*directions*), categoría (*categories*), descripción (*desc*), título (*title*), puntuación dada por los usuarios (*rating*), cantidad de grasa en gramos (*fat*), proteína (*protein*), calorías (*calories*) y sodio que contienen (*sodium*), la cantidad de cada uno de los ingredientes con los que cuenta (*ingredients*) y la fecha en la que se publicó dicha receta (*date*). Para resolver el problema de regresión planteado, sólo se hace uso de la variable de puntuación dada por los usuarios. A modo de resumen, en este trabajo se va a realizar la resolución de un problema de regresión utilizando distintas vectorizaciones y estrategias de aprendizaje automático.

# **Tareas a realizar**
## **1. Análisis de las variables de entrada**
Se visualiza la relación entre la variable de salida rating y categories. Para ello, se han realizado distintas cuestiones:
- *<ins> Identificación de las categorías más comunes. <ins>*
  
  <img src="https://github.com/user-attachments/assets/09935637-8ee6-4533-95ba-7535921cb15c" alt="imagen" width="900">

  Se puede observar que la categoría más común es Bon Appétit, seguida de Gourmet, Bread, etc.

- *<ins> Representación de gráfica de la variable rating. <ins>*

  <img src="https://github.com/user-attachments/assets/46e2c2e4-53e9-4eb9-9cd5-32f743127d79" alt="imagen" width="400">

  Si se analiza esta gráfica, se observa que el rating más usual es 4.5. Sin embargo, hay valores de esta variable que no aparecen nunca, como es el caso del 1.

- *<ins> Cálculo del promedio del rating para cada categoría. <ins>*

  <img src="https://github.com/user-attachments/assets/7f929654-c89e-447d-bb8c-e47ac40e67c9" alt="imagen" width="300">
  <img src="https://github.com/user-attachments/assets/70f53a8c-327f-4590-afff-8e8f951c0b08" alt="imagen" width="300">
  
  Se muestran las categorías que presentan una mejor puntuación por parte de los usuarios (Mortar and Pestle, WasteLess, etc.). Así mismo, las que cuentan con una puntuación menor serían Quiche o Sorbet.

- *<ins> Comparación de rating. <ins>*

  <img src="https://github.com/user-attachments/assets/31aac973-74fd-482a-9dd0-69b78cb3991c" alt="imagen" width="400">

  Se comenta el funcionamiento de boxplot (representación gráfica que contiene la distribución del conjunto de datos). De forma específica en este caso, la caja azul muestra la dispersión de los datos     entre el 25% y el 75% de los valores, significando que cuanto menor tamaño tenga dicha caja menos variabilidad van a tener los datos (ratings). La línea horizontal indica la mediana (valor central de    los datos). Así mismo, los bigotes hacen referencia al valor más alto y más bajo que puede tomar la variable y que se consideran dentro de lo normal. En último lugar, los puntos que se observan son      outliers; más concretamente, representan valoraciones puntuales que se han realizado y que están alejados de la media.

- *<ins> Cálculo media de las categorías. <ins>*

   <img src="https://github.com/user-attachments/assets/5e2440c6-5c5c-4fbf-a745-2df3db3abc84" alt="imagen" width="180">

   Ordenadas de mayor a menor frecuencia con la que aparecen las distintas categorías.

- *<ins> Combinación de frecuencia con la media del rating. <ins>*

  <img src="https://github.com/user-attachments/assets/424ca077-90c2-47b9-9fa7-146ae2c5d053" alt="imagen" width="300">
  <img src="https://github.com/user-attachments/assets/5b94e98e-07e5-4261-a107-8833bcd6033d" alt="imagen" width="300">

  Analizando los resultados anteriores, se puede ver que las categorías que aparecen con menor frecuencia suelen tener una media de rating mayor. Esto es coherente ya que tienen pocas valoraciones y,      por tanto, si todas son buenas, el rating final va a ser alto. En cambio, si se ordenan las categorías por frecuencia, poniendo primero aquellas categorías que aparecen más veces, se observa que el      rating disminuye a 3.8 aproximadamente. Al igual que antes, es factible debido a que, al tener tantas valoraciones, algunas van a ser buenas y otras malas; estas últimas van a disminuir el valor del     rating medio de la categoría.

  <img src="https://github.com/user-attachments/assets/3df4fea9-3d64-4e08-839d-5d86d69e85c4" alt="imagen" width="450">

  En esta imagen se puede ver de forma gráfica lo explicado con anterioridad. Las categorías que aparecen con menos frecuencia, cuentan con una valoración por parte de los usuarios mayor. A medida que estas categorías van apareciendo más, su rating va disminuyendo, pues ahora habrá más valoraciones tanto buenas como malas.

- *<ins> Comparación media del rating con promedio general. <ins>*

  <img src="https://github.com/user-attachments/assets/ff778abb-27e5-4446-a32f-26903221f21c" alt="imagen" width="350">

  Se han escogido algunas categorías (Winter, Omelet, Peanut Free) calculando su rating. Este, ha sido comparado con la media del rating que se obtuvó en apartados anteriores. Se puede ver que Omelet es la que presenta un valor más elevado en comparación con la media. Esto es debido a que, analizando la gráfica del apartado de arriba, aparece sólo 2 veces por lo que, si estas dos valoraciones son buenas, el rating que consigue también lo es.

- *<ins> Elección categoría más frecuente en un grupo de recetas y comparación con rating. <ins>*

  Se han elegido las 100 primeras recetas entre las 20.130 disponibles para facilitar la ejecución de la tarea. Se ha procedido a buscar la categoría más frecuente en estas y a anotar aquellas recetas en las que aparecía. Así mismo, se ha representado el *rating* de cada una de ellas y la distribución del *rating* para esta categoría.

  <img src="https://github.com/user-attachments/assets/a0fe7c35-deac-46fc-9fc0-c96f4a84c52b" alt="imagen" width="350">
  <img src="https://github.com/user-attachments/assets/d627a9e6-ade7-4498-9715-66acf4081c88" alt="imagen" width="350">

  A modo de conclusión, se ha podido ver que la categoría que aparece con mayor frecuencia suele estar asociada a recetas que tienen una buena valoración por parte de los usuarios.

## **2. Implementación de un pipeline para el preprocesado de los textos**

Para esta parte se ha hecho uso de la librería SpaCy. 
En primer lugar, se ha convertido todo el texto a minúsculas. Seguidamente, se han eliminado las tíldes y las palabras irrelevantes. Además, en el caso de que haya un número, se cambiará a tipo String. El texto tras el preprocesado en el caso de la variable *directions* sería:

<img src="https://github.com/user-attachments/assets/9c09f4c4-7ede-4c20-a480-268abefc0346" alt="imagen" width="350">

Si se repite el proceso, pero para la variable *desc*, se consigue:

<img src="https://github.com/user-attachments/assets/84ae016e-7442-4f80-9c2e-5dd7b4527c4a" alt="imagen" width="350">

Fijándose en las dos imágenes anteriores, la conversión de números a String no se hace de forma adecuada. Sin embargo, no se le ha dado una gran importancia, ya que se considera que es útil la presencia de números, como tiempo de ejecución, cantidad de ingredientes, etc. cuando se trata de una receta de cocina.

## **3. Representación vectorial de los documentos mediante tres procedimientos diferentes**

- *<ins> TF-IDF <ins>*
  
  Este procedimiento, no tiene en cuenta el contexto de las palabras. Calcula el peso de cada una de ellas por separado.
  
  Se ha comenzado calculando el TF (frecuencia con la que una palabra aparece en un documento con respecto al total de palabras) para las columnas *desc* y *directions*. Seguidamente, también para estas dos, el IDF (rareza de una palabra en el corpus completo). A modo de ejemplo se muestran algunos resultados obtenidos:

  <img src="https://github.com/user-attachments/assets/a6d1be13-bbbb-499b-8304-74d26368fc68" alt="imagen" width="250">
  <img src="https://github.com/user-attachments/assets/52c3beaf-75d3-4ca7-857d-244cc794d761" alt="imagen" width="250">
  
  Relativo a las imágenes, la primera columna (lo que hay dentro del paréntesis) corresponde al número de documento y de palabra. La segunda columna indica el peso que se le ha asignado a cada una de       estas palabras.
  A la hora de elegir el peso que tendrá cada palabra, el código hace uso de las siguientes fórmulas:
  
  <img src="https://github.com/user-attachments/assets/ef2724e1-54da-4a9f-89fb-26afdda8036e" alt="imagen" width="250">
  <img src="https://github.com/user-attachments/assets/162045df-04a7-4257-b3e5-a2584f5967d4" alt="imagen" width="250">
  <img src="https://github.com/user-attachments/assets/e88ae608-73c6-4120-bce2-ee3399b417b5" alt="imagen" width="250">
  
  Como ejemplo, se ha seleccionado el documento 22 y se ha llevado a cabo una representación gráfica de los pesos que presentan las palabras:

  <img src="https://github.com/user-attachments/assets/d29fcde9-ff6e-4de5-a1d5-1b8e1388171c" alt="imagen" width="350">
  <img src="https://github.com/user-attachments/assets/ef74b88d-adc1-42a4-a168-83efc8d37613" alt="imagen" width="350">

  Se observa en la primera imagen que para la variable *desc* la palabra más importante es *packet* ya que es la que presenta un peso mayor. En el caso de la siguiente, es *fish*. Así mismo, hay palabras a las que se le asigna un peso de 0 que puede ser debido a que son muy comunes en el documento o que sólo aparezcan una vez.

  A continuación, se realiza una comparativa entre la similitud del primer documento con el resto de estos:
  
  <img src="https://github.com/user-attachments/assets/de1c1ce2-0fa7-4b1e-b96e-4040e7e9316b" alt="imagen" width="350">

  Como era de esperar, para sí mismo presenta una similitud del 100%.
  
  <img src="https://github.com/user-attachments/assets/d3d8b8ea-5ee9-4815-b491-5d14366c8ffb" alt="imagen" width="350">

  En este caso se han escogido 14 documentos y se ha representado la similitud. Comentar que, aunque la mayoría de ellos arrojan los resultados esperados, hay algunos (0, 2 y 4) que no lo hacen.
  
- *<ins> Word2Vec <ins>*

  A diferencia del procedimiento anterior, este sí va a tener en cuenta el contexto en el que se encuentran las palabras utilizando para ello una ventana.
  A modo de ejemplo para verificar su correcto funcionamiento, se ha elegido la palabra *white* y se ha observado su similitud con 10 palabras, tanto para la variable *desc* como *directions*:
  
  <img src="https://github.com/user-attachments/assets/abaea410-944e-4f03-aa03-3781ffc2b19d" alt="imagen" width="900">

  Como resulta coherente, presenta una gran similitud con la palabra color (*color*) o yema (*yolk*).
  Al igual que antes, se realiza la comparativa en similitud del documento 1 con el resto:
  
  <img src="https://github.com/user-attachments/assets/55213007-7af2-424a-a4db-fa8308959d2b" alt="imagen" width="350">

  Ahora se comprueba como la similitud entre documentos es mayor que en el caso de TF-IDF. Esto es coherente ya que se está teniendo en cuenta el contexto en el que se encuentra cada palabra. Además, como se está trabajando con recetas, serán bastantes similares entre sí dentro lo que cabe.

- *<ins> Embeddings contextuales calculados a partir de modelos basados en transformers <ins>*

  En este último procedimiento se tiene en cuenta el contexto completo del documento analizando de forma simultánea todas las palabras que aparecen en el texto. Funciona mediante transformers, los cuales emplean mecanismos para analizar las relaciones entre todas las palabras del texto.
  
  Se comienza añadiendo los token [CLS] y [SEP] a los datos con los que se va a trabajar. Cabe destacar que para la implementación del BERT ha sido necesario disminuir el número de datos a utilizar debido a las limitaciones del mismo y de la RAM.
  
  Com BERT se pueden obtener Word Vectors de varias formas, en nuestro caso se ha implementado la suma de las 4 últimas capas del modelo. Y también es posible obtener solo un vector para cada frase completa.
  A continuación se muestra un ejemplo:
  
  <img src="https://github.com/user-attachments/assets/59953cf4-d7ac-4840-9bd1-3050d988ea5e" alt="imagen" width="85">

Para el documento anterior ha sido posible observar que la palabra *art* aparece en dos posiciones distintas del texto, por lo tanto, se ha mostrado su vector de pesos en ambos casos:

<img src="https://github.com/user-attachments/assets/0a5f7a24-5cbc-4393-ac32-22b36e976bf5" alt="imagen">

Esto significa que la misma palabra puede tener diferentes representaciones dependiendo de como se usa e interpreta en el texto. Por lo tanto, en el ejemplo anterior es posible decir que la palabra *art* aparece en dos ocasiones pero en diferentes contextos.

Al igual que para TF-IDF y Word2Vec se muestra la similitud del documento 1 con el resto de documentos, mostrando gráficamente los 20 documentos con mayor similitud.

<img src="https://github.com/user-attachments/assets/fbf4d039-25f1-4208-bbd4-84e58bce6a12" alt="imagen">

Analizando la gráfica destaca que los resultados obtenidos son peores que los de Word2Vec, ya que en el caso anterior aparecían numerosos documentos con una similitud prácticamente igual al documento original. La diferencia de resultados se puede deber a que estamos trabajando con un número reducido de datos y por lo tanto la precisión no es tan buena. O también puede ocurrir que como BERT si tiene en cuenta el contexto completo de los datos interprete que las recetas difieren más entre sí aunque todas sean de cocina.

## **4. Entrenamiento y evaluación de modelos de regresión**
Se va a realizar el entrenamiento y evaluación de los modelos de regresión implementando Random Forest y redes neuronales.

- *<ins> Random Forest <ins>*
Antes de mostrar el desarrollo y resultados obtenidos es importante destacar que el código empleado se ha reutilizado para los distintos datos (TF-IDF, Word2Vec y BERT). Así mismo, todos los datos han sido normalizados para trabajar dentro del rango 0 y 1, haciendo así que sea más sencilla la interpretación de resultados.

Al utilizar la técnica de Random Forest es posible modificar ciertos hiperparámetros del modelo para intentar encontrar los resultados óptimos. Es por ello que en este apartado se han analizado distintas combinaciones de los parámetros *n_estimators* y *max_depth*. 

Para TF-IDF los resultados obtenidos son los siguientes:

<img src="https://github.com/user-attachments/assets/12f0a051-3b42-4af6-b1c1-3780dfd1b361" alt="imagen">

<img src="https://github.com/user-attachments/assets/3d18deb6-af71-4a83-9213-c75560b9b77f" alt="imagen">

<img src="https://github.com/user-attachments/assets/e6b100ad-0a32-42b1-aec3-385556d957a9" alt="imagen">

Repetimos el proceso para Word2Vec:

<img src="https://github.com/user-attachments/assets/887b147e-d991-41e8-bd61-e3526844c41f" alt="imagen">

<img src="https://github.com/user-attachments/assets/11fb8de6-9740-4b5c-a8a1-a6732e729e1c" alt="imagen">

<img src="https://github.com/user-attachments/assets/03b0a2da-4c0d-40a6-86f7-3b6bec422267" alt="imagen">

Por último, para BERT se ha obtenido:

<img src="https://github.com/user-attachments/assets/1eef3d83-cd07-4417-a23e-c135ece6334a" alt="imagen">

<img src="https://github.com/user-attachments/assets/ce99f85d-dfe2-4657-bc87-e38c4e88a522" alt="imagen">

<img src="https://github.com/user-attachments/assets/fad33016-c621-4430-ada7-e4166e3f5049" alt="imagen">


- *<ins> Redes Neuronales <ins>*
Al igual que en caso anterior se ha implementado un código que se ha reutilizado para introducir los distintos datos con los que se va a trabajar. Los datos están normalizados y para que funcione el modelo correctamente se han tenido que pasar a tensores.

A la hora de crear el modelo se ha tenido en cuenta varios parámetros los cuales se pueden modificar para obtener los mejores resultados posibles. Estos parámetros son *learning rate*, *epochs* y *hidden_size*. En función de sus valores las métricas de error serán mejores o peores.

A continuación se muestran los datos obtenidos y las gráficas para cada uno de los casos:

Para TF-IDF tenemos:

<img src="https://github.com/user-attachments/assets/7eef7a66-d3d3-4082-8eae-33ceaa37d9fe" alt="imagen">

<img src="https://github.com/user-attachments/assets/d6c15407-fafb-4dbf-a381-7eb2a24fa6ae" alt="imagen">

<img src="https://github.com/user-attachments/assets/fb4002c3-c181-4e21-8c9e-bb0bb5d20aaf" alt="imagen">

Para Word2Vec se ha obtenido:

<img src="https://github.com/user-attachments/assets/18a2816e-f217-434e-a38b-6770271843c6" alt="imagen">

<img src="https://github.com/user-attachments/assets/2c7b9830-dbf7-47be-9279-3cfd388eacf9" alt="imagen">

<img src="https://github.com/user-attachments/assets/295e912c-68e2-4945-8c34-ee57901dd25c" alt="imagen">

Y por último, para BERT tenemos:

<img src="https://github.com/user-attachments/assets/1f031abb-22e6-487e-8fbc-b42e41d11287" alt="imagen">

<img src="https://github.com/user-attachments/assets/5077a276-2e15-4c85-a019-a1993abbae1b" alt="imagen">

<img src="https://github.com/user-attachments/assets/d26df283-34fe-4e83-89b0-2ca8cbfbf9ba" alt="imagen">


## **5. Comparación de lo obtenido en el paso 3 con el *fine-tuning* de un modelo preentrenado con *Hugging Face***

Para este apartado se ha hecho uso del modelo DistilBERT debido a su rápida ejecución en comparación con BERT. Por este mismo motivo, los datos evaluados se han reducido a un total de 10.000 y sólo se ha realizado una época. El valor del MSE obtenido para el caso de la variable *directions* es:

<img src="https://github.com/user-attachments/assets/a27c653c-89b7-4d9d-9495-9dc96cad1f7a" alt="imagen" width="350">

Cabe recalcar que los datos no se encuentran normalizados, consecuencia de que el MSE sea superior a 1. Para una mejora del mismo, se podría cambiar de DistilBERT a BERT, aumentar el número de épocas o introducir más datos.
De forma similar se ha hecho para la variable *desc*:

AÑADIR IMAGEN

A continuación, se incluye una tabla comparativa entre los resultados obtenidos en el punto 3 con los conseguidos en este caso:

AÑADIR TABLA

# **Extensión**

A modo de extender el trabajo realizado, se han implementado varias tareas adicionales.

## **1. Uso de *summarizer* preentrenado**

Se ha hecho uso del modelo Pegasus-XSUM (especializado en resumenes cortos de textos largos) para resumir la variable *directions*. Para una rápida ejecución, sólo se ha realizado sobre 5 documentos.

<img src="https://github.com/user-attachments/assets/3188b577-643d-4cef-8f6c-fb31ddbf3861" alt="imagen" width="650">

Como se puede ver en la imagen, ahora aparece una nueva columna, llamada *directions_summary*, que contiene estos resúmenes.
A modo de ejemplo, se ha seleccionado el documento 2 para ver de forma más detallada el resumen realizado:

<img src="https://github.com/user-attachments/assets/47da5ebe-fe3a-4ec2-accc-a776e1a9f56c" alt="imagen" width="350">
<img src="https://github.com/user-attachments/assets/153f6e5b-4ba0-4082-93c5-3c5be4f147d9" alt="imagen" width="350">

Comentar que al tratarse de recetas de cocina, el resumen no es el más eficiente posible debido a que hay pasos que se consideran importantes y relevantes a la hora de la receta que no se tienen en cuenta.

## **2. Representación gráfica de los datos**

En primer lugar, se ha realizado una clasificación de texto con TF-IDF y KMeans. Se ha llevado a cabo una vectorización con TF-IDF para obtener las palabras con más peso en cada documento. Posteriormente, con KMeans, se realiza una agrupación de los datos en clusters en función de la similitud entre ellos (por simplicidad, se ha reducido el número de dichos clusters a 8). Se tienen centroides que indican el centro del cluster y cada documento será asignado al más cercano. Seguidamente, se identifica la palabra que más representa a cada uno de estos clusters. La representación de los datos ha sido con un gráfico de barras:

<img src="https://github.com/user-attachments/assets/3a650a58-9953-43ac-b08e-b35d4b7e7faa" alt="imagen" width="500">
<img src="https://github.com/user-attachments/assets/b0e66466-1a71-4b36-bd48-a12b83548b53" alt="imagen" width="500">

A partir de haber obtenido las palabras más representativas de cada cluster (se han seleccionado 30), se ha procedido a su visualización en nubes de palabras. Para ello, se ha utilizado Word Cloud.

<img src="https://github.com/user-attachments/assets/961f80dc-63a0-42de-b87e-10cccac559e3" alt="imagen" width="500">
<img src="https://github.com/user-attachments/assets/14b90e75-23ab-49b0-9d72-2f92e2f7f6d9" alt="imagen" width="500">
