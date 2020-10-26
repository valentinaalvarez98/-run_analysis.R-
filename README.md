# -run_analysis.R-
  
# # Descarga y descompresión de datos

# variables de cadena para la descarga de archivos
fileName  <-  " UCIdata.zip "
url  <-  " http://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip "
dir  <-  " Conjunto de datos UCI HAR "

# Verificación de descarga de archivos. Si el archivo no existe, descárguelo al directorio de trabajo.
if ( ! file.exists ( fileName )) {
        download.file ( url , fileName , mode  =  " wb " )
}

# Verificación de descompresión de archivos. Si el directorio no existe, descomprima el archivo descargado.
if ( ! file.exists ( dir )) {
	descomprimir ( " UCIdata.zip " , archivos  =  NULL , exdir = " . " )
}


# # Leer datos
subject_test  <- read.table ( " UCI HAR Dataset / test / subject_test.txt " )
subject_train  <- read.table ( " UCI HAR Dataset / train / subject_train.txt " )
X_test  <- read.table ( " UCI HAR Dataset / test / X_test.txt " )
X_train  <- read.table ( " UCI HAR Dataset / train / X_train.txt " )
y_test  <- read.table ( " UCI HAR Dataset / test / y_test.txt " )
y_train  <- read.table ( " UCI HAR Dataset / train / y_train.txt " )

activity_labels  <- read.table ( " UCI HAR Dataset / activity_labels.txt " )
características  <- read.table ( " UCI HAR Dataset / features.txt " )  

# # Análisis
# 1. Fusiona los conjuntos de entrenamiento y prueba para crear un conjunto de datos.
dataSet  <- rbind ( X_train , X_test )

# 2. Extrae solo las medidas de la media y la desviación estándar de cada medida.
# Cree un vector de solo mean y std, use el vector para crear subconjuntos.
MeanStdOnly  <- grep ( " mean () | std () " , features [, 2 ])
dataSet  <-  dataSet [, MeanStdOnly ]


# 4. Etiquete apropiadamente el conjunto de datos con nombres descriptivos de actividades.
# Cree un vector de nombres de características "Limpias" eliminando la aplicación "()" al conjunto de datos para cambiar el nombre de las etiquetas.
CleanFeatureNames  <- sapply ( características [, 2 ], función ( x ) {gsub ( " [()] " , " " , x )})
nombres (conjunto de datos ) <-  CleanFeatureNames [ MeanStdOnly ]

# combinar prueba y tren de datos de sujetos y datos de actividad, dar etiquetas descriptivas
sujeto  <- rbind ( sujeto_train , sujeto_prueba )
nombres ( asunto ) <-  ' asunto '
actividad  <- rbind ( y_train , y_test )
nombres ( actividad ) <-  ' actividad '

# Combine el conjunto de datos del sujeto, la actividad y la media y el estándar para crear el conjunto de datos final.
dataSet  <- cbind ( asunto , actividad , dataSet )


# 3. Utiliza nombres de actividades descriptivos para nombrar las actividades en el conjunto de datos
# agrupe la columna de actividad de dataSet, cambie el nombre de la etiqueta de niveles con activity_levels y aplíquela a dataSet.
act_group  <-  factor ( dataSet $ actividad )
niveles ( act_group ) <-  activity_labels [, 2 ]
dataSet $ actividad  <-  act_group


# 5. Crea un segundo conjunto de datos ordenado e independiente con el promedio de cada variable para cada actividad y cada tema.

# comprobar si el paquete reshape2 está instalado
if ( ! " reshape2 "  % in% installed.packages ()) {
	install.packages ( " reshape2 " )
}
biblioteca ( " reshape2 " )

# Derretir datos a datos altos y delgados y medios de transmisión. Finalmente, escriba los datos ordenados en el directorio de trabajo como "tidy_data.txt"
baseData  <- melt ( dataSet , ( id.vars = c ( " sujeto " , " actividad " )))
secondDataSet  <- dcast ( baseData , sujeto  +  actividad  ~  variable , media )
nombres ( secondDataSet ) [ - c ( 1 : 2 )] <- paste ( " [media de] " , nombres ( secondDataSet ) [ - c ( 1 : 2 )])
write.table ( secondDataSet , " tidy_data.txt " , sep  =  " , " )
