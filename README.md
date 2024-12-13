# Trabajo_TD
Repositorio utilizado para la resolución de una tarea de aprendizaje sobre documentos que contienen recetas de cocina de todo el mundo

# **Introducción**
El conjunto de datos con el que se va a trabajar consta de 20.130 recetas. Estas presenta diferentes atributos que las definen: instrucciones para hacer la receta, categoría, descripción, título, puntuación dada por los usuarios, cantidad de grasa en gramos, proteína, calorías y sodio que contienen, la cantidad de cada uno de los ingredientes con los que cuenta y la fecha en la que se publicó dicha receta. Para resolver el problema de regresión planteado, sólo se hace uso de la variable de puntuación dada por los usuarios (rating). A modo de resumen, en este trabajo se va a realizar la resolución de un problema de regresión utilizando distintas vectorizaciones y estrategias de aprendizaje automático.

# **Tareas a realizar**
## **1. Análisis de las variables de entrada**
Se visualizan la relación entre la variable de salida rating y categories. Para ello, se han realizado distintas cuestiones:
- *<ins> Identificación de las categorías más comunes. <ins>*
  
  <img src="https://github.com/user-attachments/assets/09935637-8ee6-4533-95ba-7535921cb15c" alt="imagen" width="900">

  Se puede observar que la categoría más común es Bon Appétit, seguida de Gourmet, Bread, etc.

- *<ins> Representación de gráfica de la variable rating. <ins>*

  <img src="https://github.com/user-attachments/assets/46e2c2e4-53e9-4eb9-9cd5-32f743127d79" alt="imagen" width="500">

  Si se analiza esta gráfica, se observa que el rating más usual es 4.5. Sin embargo, hay valores de esta variable que no aparecen nunca, como es el caso del 1.

- *<ins> Cálculo del promedio del rating para cada categoría. <ins>*

  <img src="https://github.com/user-attachments/assets/2fb51953-5e12-41b5-aeea-6674f02ebf7f" alt="imagen" width="250">
  <img src="https://github.com/user-attachments/assets/7f929654-c89e-447d-bb8c-e47ac40e67c9" alt="imagen" width="400">
  <img src="https://github.com/user-attachments/assets/70f53a8c-327f-4590-afff-8e8f951c0b08" alt="imagen" width="400">
  
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








  

