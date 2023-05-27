
NCAA Tournament Winner Prediction
Este proyecto tiene como objetivo predecir el ganador del Torneo Final de la NCAA en 2023. El código proporcionado consiste en varios pasos para la preparación de datos, ingeniería de características, modelado y predicción.

Preparación de los Datos
Los datos se cargan desde archivos CSV obtenidos de la pagina: https://www.kaggle.com/competitions/march-machine-learning-mania-2023/data y se fusionan los datos del torneo tanto de los torneos masculinos como femeninos. Se eliminan algunas columnas y se agrega una nueva columna que representa la diferencia de puntuación entre los equipos ganadores y perdedores.

Descripción del conjunto de datos

Cada temporada se juegan miles de partidos de baloncesto de la NCAA entre equipos de baloncesto universitario de la División I, culminando en el March Madness®, el campeonato nacional de 68 equipos que comienza a mediados de marzo. Hemos proporcionado una gran cantidad de datos históricos sobre partidos y equipos de baloncesto universitario, que se remontan a muchos años atrás. Con estos datos históricos, puedes explorarlos y desarrollar tus propias formas distintivas de predecir los resultados de los partidos del March Madness®. Incluso puedes evaluar y comparar diferentes enfoques viendo cuál de ellos habría sido el mejor para predecir los partidos del torneo en el pasado.

Si no estás familiarizado con el formato y los detalles del torneo de la NCAA®, te recomendamos leer las páginas de Wikipedia de los torneos masculinos y femeninos antes de sumergirte en los datos. La descripción de los datos y el esquema pueden parecer abrumadores al principio, pero no son tan complicados como parecen.

Ten en cuenta que en años anteriores había competiciones separadas para predecir los partidos del torneo masculino o los partidos del torneo femenino. En la competición de este año, enviarás archivos de predicción combinados que incluyen predicciones tanto para el torneo masculino como para el torneo femenino. Por lo tanto, los archivos de datos incorporan tanto datos masculinos como datos femeninos. Los archivos que se refieren solo a datos masculinos comenzarán con el prefijo M, y los archivos que se refieren solo a datos femeninos comenzarán con el prefijo W. Algunos archivos abarcan tanto datos masculinos como datos femeninos, como los archivos de Ciudades y Conferencias, y estos archivos no comienzan con un prefijo M o W.

Como recordatorio, se recomienda incorporar tus propias fuentes de datos. Hemos proporcionado datos históricos extensos para iniciar el proceso de modelado, y estos datos son autoconsistentes (por ejemplo, las fechas y las ID de los equipos siempre se tratan de la misma manera). Sin embargo, también puedes hacer uso productivo de datos externos. Si decides seguir este camino, ten en cuenta que muchas fuentes tienen su propia forma distintiva de identificar los nombres de los equipos, lo que puede dificultar la vinculación con nuestros datos. Los archivos MTeamSpellings y WTeamSpellings, que se enumeran en la sección inferior, pueden ayudarte a relacionar las referencias externas de los equipos con nuestra propia estructura de ID de equipos, y es posible que también necesites comprender cómo funcionan exactamente las fechas en nuestros datos.

Extendemos nuestro agradecimiento a Kenneth Massey por proporcionar gran parte de los datos históricos.

Agradecimiento especial a Jeff Sonas de Sonas Consulting por su apoyo en la recopilación del conjunto de datos para esta competición.

Qué predecir
Competencia de calentamiento (Warmup Competition): Debes enviar las probabilidades predichas para todos los posibles enfrentamientos en los últimos 5 torneos de la NCAA® (2017-2019 y 2021-2022). Ten en cuenta que no se celebró ningún torneo en 2020.

Competencia de 2023: Debes enviar las probabilidades predichas para todos los posibles enfrentamientos antes de que comience el torneo de 2023.

Consulta la página de Cronograma (Timeline) para ver las fechas específicas. En ambas etapas, la muestra de envío te indicará qué partidos debes predecir.

Descripciones de archivos
A continuación, describimos el formato y los campos de los archivos de datos de la competencia. Todos los archivos están completos hasta el 7 de febrero de la temporada actual. A medida que nos acerquemos al torneo a mediados de marzo, proporcionaremos actualizaciones de estos archivos para incorporar datos de las semanas restantes de la temporada actual.

Sección de datos 1: Lo básico
Esta sección proporciona todo lo que necesitas para construir un modelo de predicción simple y enviar predicciones.

ID y nombres de equipos
Semillas del torneo desde la temporada 1984-85
Puntuaciones finales de todos los partidos de temporada regular, torneos de conferencias y torneos de la NCAA® desde la temporada 1984-85
Detalles a nivel de temporada, incluyendo fechas y nombres de regiones
Archivo de ejemplo de envío para la etapa 1

Nota especial sobre los números de "Temporada": la temporada de baloncesto universitario dura desde principios de noviembre hasta el torneo del campeonato nacional que comienza a mediados de marzo. Por ejemplo, este año los primeros partidos de temporada regular se jugaron en noviembre de 2022 y los partidos del campeonato nacional se jugarán en abril de 2023. Debido a que una temporada de baloncesto abarca dos años calendario de esta manera, puede resultar confuso referirse al año de la temporada. Por convención, cuando identificamos una temporada en particular, nos referiremos al año en que termina la temporada, no al año en que comienza. Entonces, por ejemplo, la temporada actual se identificará en nuestros datos como la temporada 2023, no la temporada 2022 o la temporada 2022-23 o la temporada 2022-2023, aunque puedas ver cualquiera de estos términos en el uso cotidiano fuera de nuestros datos.


Ingeniería de Características
Para cada equipo en cada temporada, el código calcula el número de victorias, el número de derrotas, el promedio de la diferencia de puntuación en las victorias y el promedio de la diferencia de puntuación en las derrotas. Luego, se calcula la proporción de victorias y el promedio de la diferencia de puntuación como características.

Resultados del Torneo
Se cargan los resultados del torneo y se preparan para el entrenamiento. Se asignan las semillas (clasificaciones pre-torneo asignadas a cada equipo en función de su rendimiento durante la temporada regular) a los equipos ganadores y perdedores.

Estadísticas de la Temporada
El código combina las estadísticas de la temporada con los resultados del torneo para agregar características adicionales. Esto incluye combinar las características de la temporada con los resultados del torneo para obtener estadísticas como el número de victorias, el número de derrotas, la proporción de victorias y el promedio de la diferencia de puntuación para cada equipo en cada temporada.

Agregar Partidos Perdidos
El código crea dos versiones de cada partido en el conjunto de datos, una desde la perspectiva del equipo ganador y otra desde la perspectiva del equipo perdedor.

Diferencias de Características
El código calcula las diferencias entre las características de los equipos ganadores y perdedores para cada partido.

Modelado y Evaluación
Se utiliza un clasificador de Random Forest para el modelado. El conjunto de datos se divide en conjuntos de entrenamiento y validación. El modelo se entrena en el conjunto de entrenamiento y se evalúa en el conjunto de validación utilizando la precisión y una matriz de confusión. Además, se trazan y analizan la precisión, la curva ROC y la curva de precisión-recall. También se determina la importancia de las características y se visualiza uno de los árboles de decisión del bosque aleatorio.

Guardar el Modelo
El modelo entrenado se guarda como un archivo pickle para su uso futuro.

Realizar Predicciones
Se utiliza el modelo para hacer predicciones en el archivo de muestra proporcionado. Los datos de muestra se procesan, se fusionan con los datos de validación y se utiliza el modelo para predecir las probabilidades de ganar para cada equipo. Luego, las predicciones se agregan al dataframe de muestra.

Determinar al Ganador
Se utiliza la función final_winner para determinar al ganador de la ronda final. La función mezcla la lista de ganadores y elimina equipos hasta que solo quede un ganador. Por último, se imprime el nombre y la ID del ganador.

Contribuidores
Adrian Infantes - infantesromeroadrian@gmail.com


Tenga en cuenta que este README resume los pasos y la información proporcionados en el código. Se pueden encontrar más detalles sobre el proyecto y la implementación en el código y en los comentarios del mismo.
