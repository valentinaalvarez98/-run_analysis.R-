# -run_analysis.R-
Proyecto de obtención y limpieza de datos
Criterios
El conjunto de datos enviado está ordenado.
El repositorio de Github contiene los scripts necesarios.
GitHub contiene un libro de códigos que modifica y actualiza los libros de códigos disponibles con los datos para indicar todas las variables y resúmenes calculados, junto con las unidades y cualquier otra información relevante.
El archivo README que explica los archivos de análisis es claro y comprensible.
El trabajo presentado para este proyecto es el trabajo del estudiante que lo envió.
Instrucciones
El propósito de este proyecto es demostrar su capacidad para recopilar, trabajar y limpiar un conjunto de datos. El objetivo es preparar datos ordenados que se puedan utilizar para un análisis posterior. Sus compañeros lo calificarán en una serie de preguntas de sí / no relacionadas con el proyecto. Se le pedirá que envíe: 1) un conjunto de datos ordenado como se describe a continuación, 2) un enlace a un repositorio de Github con su script para realizar el análisis, y 3) un libro de códigos que describe las variables, los datos y cualquier transformación o trabajo que realizó para limpiar los datos llamado CodeBook.md. También debe incluir un README.md en el repositorio con sus scripts. Este repositorio explica cómo funcionan todos los scripts y cómo están conectados.

Una de las áreas más interesantes de toda la ciencia de datos en este momento es la informática portátil; consulte, por ejemplo, este artículo. Empresas como Fitbit, Nike y Jawbone Up están compitiendo para desarrollar los algoritmos más avanzados para atraer nuevos usuarios. Los datos vinculados desde el sitio web del curso representan datos recopilados de los acelerómetros del teléfono inteligente Samsung Galaxy S. Una descripción completa está disponible en el sitio donde se obtuvieron los datos:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

Aquí están los datos del proyecto:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Debe crear un script de R llamado run_analysis.R que haga lo siguiente.

Fusiona los conjuntos de entrenamiento y prueba para crear un conjunto de datos.
Extrae solo las medidas de la desviación estándar y media de cada medida.
Utiliza nombres de actividades descriptivos para nombrar las actividades en el conjunto de datos
Etiqueta adecuadamente el conjunto de datos con nombres de variables descriptivos.
A partir del conjunto de datos del paso 4, crea un segundo conjunto de datos ordenado e independiente con el promedio de cada variable para cada actividad y cada tema. ¡Buena suerte!
Entrada
Conjunto de datos: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

Script de análisis
run_analysis.R: este script toma los datos de entrada y crea el archivo de salida

El script primero descarga y descomprime el conjunto de datos de la URL anterior. Luego, el guión lee los conjuntos de prueba y entrenamiento, los fusiona (1). Filtra las características medias y estándar, y selecciona solo estas (2) Se fusiona en los nombres de las actividades para las actividades (3) Luego crea una serie de columnas etiquetadas para representar variables individuales de la característica. (4) Calcula el promedio de cada variable y escribe este conjunto de datos en tidy.txt(5)

Salida
Conjunto de datos ordenado: tidy.txt
Libro de códigos
CodeBook.md: describe las variables, los datos y cualquier transformación o trabajo que realizó para limpiar los datos
