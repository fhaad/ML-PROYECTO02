![HenryLogo](https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png)

### PROYECTO INDIVIDUAL 02 - ML - APLICACION DE MODELO DE MACHINE LEARNING

### JOSE FEDERICO HAAD ATUESTA - DTS-05

### TABLA GENERAL

1. Introducción
2. Procedimientos
3. Limpieza ETL (Extract, Transform, Load)
4. Consigna del Problema
5. Aplicación de Solución
6. Modelos utilizados y resultados
7. Diagrama de proceso


### 1. INTRODUCCION

En la aplicación de modelos de Machine Learning (ML) existen diferentes soluciones para llegar a un resultado adecuado y consistente. No importa si tu modelo es supervisado o no supervisado, en el análisis de los feature y su correlación cercana o alta pueden generar un buen resultado, lo demás podrían ocasionar ruido o distorsión de los datos. Es aquí donde el papel de Data Engineer como analista de los datos, busca encontrar la relación acorde a la aplicación de métricas para conocer si el resultado esta sesgado, desbalanceado o es óptimo 

### 2. PROCEDIMIENTOS

Despues de conocer la fuente de los datos y extraerlos se realiza un EDA (Exploratory Data Analysis) o Analisis exploratorio de los datos e identificar las variables y su contenido.
Podemos realizar los siguientes pasos

- Analisis exploratorio
- Documentacion de lo encontrado
- Documentacion de las soluciones
- Organizacion de la Data 

Dentro del desarrollo de DATA ENGINNER los pasos del analisis son fundamentales y el pre ambulo del trabajo que se debe realizar con la informacion para obtener un buen resultado.


<img src="/src/ETL.jpg"  height="400">

### 3. LIMPIEZA ETL

El proceso de ETL comienza con la extraccion de los datos de forma cruda. Estos archivos originales de los datos se guardaron en un directorio.

DIRECTORIO  ..\DATASET_RAW (Archivos originales)

Se procedió a cargar la data en un DataFrame de pandas para su mejor manipulacion.
Los archivos cargados son de tipo .CSV, para un total de 2 archivos con diferente cantidad de registros.

A continuacion se procede a realizar un EDA con los datos:

Para este procedimiento se utilizo una libreria practica y agil conocida como **pandas-profiling**, que genera un reporte detallado y completo de los datos crudos.

- from pandas_profiling import ProfileReport (Libreria de Reporte): genera un reporte con una interface en HTML.
- Se procedio a guardar estos reportes en un directorio como documentacion encontrada 
DIRECTORIO  ..\EDA_REPORT (Reportes)

- dataset_train_EDA.html
- dataset_test_EDA.html


<img src="/src/profiling.jpg"  height="400">

Despues del anterior analisis se procede a aplicar una serie de codigos de limpieza de datos. 
Para el archivo de DATA se creo un **Jupyter Notebook** con el siguientes nombres

- hospitalizaciones_ETL


este archivo quedo en el directorio ETL.

Pasos que se aplicaron de limpieza

- Eliminacion de columnas (no necesarias)
- Agregacion de nuevas columnas
- Renombre de columnas
- Generacion de una copia del dataset
  

### 4. CONSIGNA DEL PROBLEMA

En algún hospital x o y de acuerdo a los datos suministrados se desea predecir si un paciente tendrá una estadía prolongada o no. Para este análisis y predicción el hospital entrega un conjunto de datos en el que existen variables de muy baja o alta correlación. La problemática de este tipo de conjunto de datos es buscar y encontrar las mejores correlaciones que permita predecir cuando un paciente va a tener una estadía mayor o menor de acuerdo a su condición de salud.

### 5. APLICACION DE SOLUCION

De acuerdo a la problemática plateada anteriormente en base a las correlaciones entre cada una de las variables se procede a crear un nuevo dataset de entrenamiento al cual se le aplicara el modelo de Machine Learning. Este es el procedimiento.


-	Se elimina las columnas con muy poca correlación o que poca influencia tiene en los datos
-	Se crea la columna target (objetivo) a predecir
-	La columna target se crea en base a la columna Stay (estadía)
-	La columna target solo cuenta con (0 y 1), para estadías igual o menor a 8 días se asigna el valor (0) y para estadías mayor a 8 días se asigna el valor de (1)
-	el nuevo dataset de entrenamiento solo queda con las variables de mayor correlación.
-	Se aplica el método get_dummies a los features o variables, es decir, que de acuerdo a los valores string el método genera nuevas columnas con valores numéricos esencial para la aplicación de cualquier modelo.
-	Se genera una nueva correlación entre el nuevo dataset
-	Se escogen las feature o variables con las mejores correlaciones

Ya con este procedimiento aplicado se procede a aplicar los modelos de Machine Learning convenientes para el conjunto de datos clasificado. 


<img src="/src/mapa.jpg"  height="400">

### 6. MODELOS UTILIZADOS Y RESULTADOS

En la aplicación de modelos de Machine Learning se utilizan dos modelos de clasificación.

-	Árbol de decisión
-	Support vector machine (SVM)
-   Kvecinos
-   Bagging classifier
-   Random Forest

Cada uno de ellos cumple con la función de clasificar y ordenar las clases e instancias con el fin de predecir un resultado.

El mejor resultado obtenido al aplicar DecisionTreeClassifier es el siguiente:
El accuracy del modelo es: 0.6627967479674797
Y al utilizar el método de classification_report nos muestra esta tabla de resultados

<img src="/src/reporte1.jpg"  height="200">  

<img src="/src/reporte2.jpg"  height="200">

<img src="/src/grafico1.jpg"  height="200">

- Resultados de validacion cruzada

[0.62296341 0.62296341 0.62296341 0.62296341 0.62297561]
[0.62095122 0.56932927 0.58335366 0.57820732 0.58113415]

- Hold-out

Accuracy Modelo  0  es  0.6610325203252032
Accuracy Modelo  1  es  0.6608861788617886
Accuracy Modelo  2  es  0.6607886178861788
Accuracy Modelo  3  es  0.6609756097560976
Accuracy Modelo  4  es  0.6609512195121952
Accuracy Modelo  5  es  0.6610487804878049
Accuracy Modelo  6  es  0.6610569105691056
Accuracy Modelo  7  es  0.6610325203252032
Accuracy Modelo  8  es  0.6610081300813008
Accuracy Modelo  9  es  0.6609674796747967

Accuracy del ensamble:  0.6610569105691056

- Bagging Classifier

0.6616620209059233
0.6610569105691056

- Random forest

0.6616620209059233

- Pipeline

Regresión Logística pipeline accuracy en test: 0.622
SVM pipeline accuracy en test: 0.627
Árbol de decisión pipeline accuracy en test: 0.661
RandomForest pipeline accuracy en test: 0.661


### 7. DIAGRAMA DE PROCESO

<img src="/src/Proyecto_02.jpg"  height="600">