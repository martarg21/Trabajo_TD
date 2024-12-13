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

  Se comenta el funcionamiento de boxplot (representación gráfica que contiene la distribución del conjunto de datos). De forma específica en este caso, la caja azul muestra la dispersión de los datos entre el 25% y el 75% de los valores, significando que cuanto menor tamaño tenga dicha caja menos variabilidad van a tener los datos (ratings). La línea horizontal indica la mediana (valor central de los datos). Así mismo, los bigotes hacen referencia al valor más alto y más bajo que puede tomar la variable y que se consideran dentro de lo normal. En último lugar, los puntos que se observan son outliers; más concretamente, representan valoraciones puntuales que se han realizado y que están alejados de la media.




  

