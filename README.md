# Trabajo_TD
Repositorio utilizado para la resolución de una tarea de aprendizaje sobre documentos que contienen recetas de cocina de todo el mundo

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
  
  Se ha comenzado calculando el TF (frecuencia con la que una palabra aparece en un documento con respecto al total de palabras) para las columnas *desc* y *directions*. Seguidamente, también para   estas dos, el IDF (rareza de una palabra en el corpus completo). A modo de ejemplo se muestran algunos resultados obtenidos:

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

  Se observa en la primera imagen que para la variable *desc* la palabra más importante es *packet* ya que es la que presenta un peso mayor. En el caso de la siguiente, es *fish*. Así mismo, hay palabras a las que se le asigna un peso de 0 que puede ser debido a que son muy comunes en el documento.

  A continuación, se realiza una comparativa entre la similitud del primer documento con el resto de estos:
  
  <img src="https://github.com/user-attachments/assets/de1c1ce2-0fa7-4b1e-b96e-4040e7e9316b" alt="imagen" width="350">

  Como era de esperar, para sí mismo presenta una similitud del 100%.
  
  <img src="https://github.com/user-attachments/assets/d3d8b8ea-5ee9-4815-b491-5d14366c8ffb" alt="imagen" width="350">

  En este caso se han escogido 14 documentos y se ha representado la similitud. Comentar que, aunque la mayoría de ellos arrojan los resultados esperados, hay algunos (0, 2 y 4) que no lo hacen.
