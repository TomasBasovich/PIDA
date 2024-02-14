<p align='center'>
<img src ="https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png">
<p>

<h1 align='center'>
 <b>PROYECTO INDIVIDUAL Nº2</b>
</h1>

# <h1 align="center">**`Siniestros viales`**</h1>
![ANSV](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/logoAnsv.png?raw=true)![ALPLV](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/1630597122772.jpg?raw=true)![Driveguard](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/Driveguard.logo.jpg?raw=true)

# *DriveGuard Safety Enterprise, Drive safe to a better future*
### ***Introducción:***

Como es de público conocimiento, en la ciudad de Buenos Aires ocurren decenas y hasta cientos de accidentes por día en las diferentes condiciones de conduccion, ya sea caminando, en bicicleta, en auto o en moto, ¡hasta los transportes públicos pueden tener un accidente! 

Los siniestros viales, también conocidos como accidentes de tráfico o accidentes de tránsito, son eventos que involucran vehículos en las vías públicas y que pueden tener diversas causas, como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques con objetos fijos o caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales hasta lesiones graves o fatales para los involucrados.

En el contexto de una ciudad como Buenos Aires, los siniestros viales pueden ser una preocupación importante debido al alto volumen de tráfico y la densidad poblacional. Estos incidentes pueden tener un impacto significativo en la seguridad de los residentes y visitantes de la ciudad, así como en la infraestructura vial y los servicios de emergencia.

Las tasas de mortalidad relacionadas con siniestros viales suelen ser un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes o por cada cierta cantidad de vehículos registrados. Reducir estas tasas es un objetivo clave para mejorar la seguridad vial y proteger la vida de las personas en la ciudad.

Es importante destacar que la prevención de siniestros viales involucra medidas como la educación vial, el cumplimiento de las normas de tráfico, la infraestructura segura de carreteras y calles, así como la promoción de vehículos más seguros. El seguimiento de las estadísticas y la implementación de políticas efectivas son esenciales para abordar este problema de manera adecuada.

En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, esta sigue siendo la principal causa de muertes violentas en el país.
Los informes del Sistema Nacional de Información Criminal (SNIC), del Ministerio de Seguridad de la Nación, revelan que entre 2018 y 2022 se registraron 19.630 muertes en siniestros viales en todo el país. Estas cifras equivalen a 11 personas por día que resultaron víctimas fatales por accidentes de tránsito.

Solo en 2022, se contabilizaron 3.828 muertes fatales en este tipo de hechos. Los expertos en la materia indican que en Argentina es dos o tres veces más alta la probabilidad de que una persona muera en un siniestro vial que en un hecho de inseguridad delictiva.

Es por eso que desde DriveGuard Safety Enterprise, una empresa preocupada por el bienestar de los conductores de distintos vehículos y los peatones circulantes, realizamos el siguiente análisis estadístico enfocado en mostrar las diferentes problemáticas que se presentan en el día a día en la conducción en la ciudad,junto con la Asociación Luchemos por la Vida, abarcaremos todos los aspectos posibles para reflejar el problema y brindar una solución óptima a lo solicitado, esperamos que el consiguiente análisis logre satisfacer sus espectativas.

![Accidente](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/accidente.png?raw=true)

# Índice de vídeos explicativos / informes sobre seguridad vial: 

***Video Contextual sobre la prevención de accidentes***:
https://www.youtube.com/watch?v=iquhK1N8_zE&ab_channel=MinisteriodeTransportePBA


***CESVI argentina nos cuenta sobre su análisis de siniestros en 2020*** : 
https://www.youtube.com/watch?v=bOxMaxNMPoI&ab_channel=CESVIARGENTINA

***Responsabilidades viales según la edad del conductor por CESVI argentina*** :
https://www.youtube.com/watch?v=vCRHjIgFtZ0&ab_channel=CESVIARGENTINA

***Conductas de ciclistas en la ciudad*** :
https://www.youtube.com/watch?v=pn6ARJ50bq4&ab_channel=CESVIARGENTINA

### *A tener en cuenta* :

Desde DriveGuard y gracias a la asociación civil Luchemos por la Vida, proporcionamos un índice con links para una mejor conduccion y factores a tener en cuenta antes de encender el vehículo: 
https://www.luchemos.org.ar/es/sabermas


# ETL: 

Para el desarrollo de la Extracción, Transformación y posterior Carga de los datos, se observó primero que teníamos el dataset "homicidios.xlsx" anidado en varias páginas, por lo cual procedimos a tener cada una en un dataframe diferente.
Luego, con la extensión data wrangler, recorrimos las diferentes columnas observando los datos y realizamos un merge de ambos dataframes utilizados con la columna "ID" en común, Capitalizamos todos los datos que poseen nuestras columnas a la primer letra en mayúscula,reordenamos la columna "LUGAR_DEL_HECHO" y eliminamos las columnas duplicadas y columnas irrelevantes, nos quedó así luego de realizar todo el proceso ETL:

***ID,	ROL,	VICTIMA,	SEXO,	EDAD,	FECHA_FALLECIMIENTO,	N_VICTIMAS,	FECHA_SINIESTRO,	HORA_SINIESTRO,	LUGAR_DEL_HECHO,	TIPO_DE_CALLE,	COMUNA,	pos x,	pos y,	PARTICIPANTES,	ACUSADO,	semestre***

***Nulos***

Los datos nulos estaban representados por "Sd" los cuales refieren a "Sin Dato", por criterio personal, se elimino aquellas filas que poseían "Sin Dato" en las columnas "Víctimas" "Acusado" y "Participantes", sí, había un accidente, pero ese accidente no poseía personas según los "Sin Dato" en ellas.

Procedimos a seguir revisando los datos faltantes, y encontramos "Sin Dato" en la columna "FECHA_FALLECIMIENTO" por lo cual decidimos rellenar los "Sin Dato" de "FECHA_FALLECIMIENTO" con los datos de "FECHA_SINIESTRO" deduciendo así que el accidentado falleció en el momento del accidente.

Continuando con los "Sd" encontrados en "EDAD", se realizo un ""fillna"" con la media de edad de las demás personas, para evitar tener datos faltantes, realizamos lo mismo con "HORA_SINIESTRO"



***Duplicados***

En nuestro análisis no encontramos datos duplicados para nuestro dataset.

***Outliers***

En el análisis realizado no se encontraron outliers, pero sí podríamos tomar como valor atípico los casos en que la víctima era el conductor de un vehículo y tenía más de 65 años de edad.

Según el Gobierno de la Ciudad:
¿Hasta cuándo puedo tener la licencia de conducir?
No hay límite de edad, pero a partir de los 65 años la licencia se otorga por menos tiempo. Las personas de más de 70 años pueden renovar su licencia cada año y deben rendir nuevos exámenes.

Ésto resalta quizá la velocidad de reflejos en comparativa con una persona más joven, las personas mayores de 70 años deben hacerse chequeos médicos, de vista etc, para poder seguir conduciendo, es un porcentaje menor, pero accidentes a nivel global suelen denotar que hay personas mayores de 70 años que poseían problemas cardíacos al momento del siniestro, Driveguard te dice: ¡cuida a tus mayores!, maneja por ellos.

***¿Sabías que...?***
Las personas de edad avanzada son más propensas a sufrir un accidente de automóvil al hacer giros a la izquierda que las personas de otros grupos de edad.

La capacidad de reacción de una persona de la tercera edad a la hora de conducir se puede ver afectada por varias razones, como los fármacos, la reducción de la visión, la capacidad de poder realizar varias tareas, y sobretodo el espacio a tener en cuenta con otros vehículos el cual es crucial para una buena conducción.

***Extras***

+ Se creó una nueva columna llamada "semestre" para el desarrollo de nuestro KPI
+ Se extrajo sólo el año de la fecha del siniestro para sumar a nuestro KPI y población
+ Se realizó WebScrapping para obtener datos de la poblacion para cada año, por cada Comuna
+ Se realizó Geolocalización con la librería GeoPy.GeoCoders con el objetivo de lograr obtener las coordenadas de nuestros datos faltantes en la ubicación de los accidentes
+ Se reorganizó la columna "LUGAR_DEL_HECHO" pasando por ejemplo: Rivadavia Av., a su correcta forma: Av. Rivadavia
+ Dentro de "LIMPIEZA_DATOS.IPYNB" realizamos el cálculo de la Tasa de mortalidad solicitada para los Indicadores de desempeño solicitados por el Observatorio

***Advertencia: el promedio de censos realizados para obtener la población, fue realizado en base al porcentaje de crecimiento, son datos estimativos para realizar el KPI correctamente***

# ***EDA***


Luego de nuestro proceso de ETL, procedimos a darle una visión gráfica a nuestros datos, para así poder observar con detenimiento los puntos a investigar y el por qué suceden los accidentes en Capital Federal.

### Rol de las víctimas al momento del siniestro: 


![Rol de las víctimas](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/V%C3%ADctimas.png?raw=true)

Tabla proporcionada por la asociación Luchemos por la Vida, explicando el rol que ocupaban las víctimas en accidentes fatales en 2021


![Uso del celular](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/Celular.jpg?raw=true)
![Uso celular peatones](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/CelularPeatones.jpg?raw=true)

Un aspecto importante a tener en cuenta es el uso de celulares en la conducción y al caminar, ya que posee un alto porcentaje de distracción a nuestros alrededores, junto con el alcohol, es una de las principales razones de accidentes

### Porcentaje de accidentes por tipo de rol:


![Cantidad de accidentes x Rol](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/victimasxrol.png?raw=true)

En éste gráfico podemos observar el rol que tenía la víctima al momento del accidente, siendo principalmente conductores de vehículos, seguido por peatones y luego pasajeros/acompañantes damnificados, más adelante observaremos con más detalle acerca de qué punto de interés se puede utilizar para realizar una investigación sobre éstos datos

### Cantidad de accidentes a lo largo del tiempo por Comuna:

![Accidentes x Año ](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/siniestrosxa%C3%B1os.png?raw=true)

Éste gráfico de líneas (un poco confuso, pero permítame explicarlo) representa la cantidad de accidentes por comuna, el cual nos deja denotar que la Comuna 1 posee más accidentes que las demás, observamos a nivel global un descenso de accidentes entre el final de 2019 y comienzos/mitad de 2020, ésto lo asociamos a la pandemia, ya que en marzo de 2020 se instauró el aislamiento social, limitando en gran cantidad el transito vehicular en toda la ciudad que estamos analizando.
Es por ésta razón que tenemos una disminución drástica de los accidentes, pero como observamos, al llegar a finales de 2020, volvemos lamentablemente a un incremento bastante drástico de accidentes, creemos que ésto se debe a que la gente, a costa de su propia seguridad por la pandemia, decidió salir igual, ya sea de vacaciones o para visitar algún familiar lejano, lo cual pudo provocar en varias oportunidades accidentes viales.

### Cantidad de víctimas por comuna:


![Víctimas x comuna ](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/cantvictimasxcomuna.png?raw=true)

Como podemos observar, en la Ciudad Autónoma de Buenos Aires, poseemos 15 comunas, de la 1 a la 15, las cuales son agrupaciones de 2 o más barrios adyacentes
El gráfico representa la suma total de víctimas por cada comuna, un detalle bastante importante a tener en cuenta si se observa que la mayoria de los accidentes ocurrieron en la Comuna número 1
*¿A qué se debe esto?* 
La comuna número 1 es, por decir, la más importante en la capital, en ella se reúnen el puerto de Buenos Aires, el Microcentro, la terminal de omnibus de Retiro, y varias zonas que son de índole turística, a continuación vamos a contextualizar el por qué, según nosotros, ocurren éstos accidentes en la Comuna número 1:

# Atracciones turísticas y recorridos:

![Atracciones para turistas](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/atracciones.png?raw=true)

Como podemos observar en el mapa, la gran mayoría de atracciones turísticas se encuentra en la Comuna 1, gran punto para investigar más a fondo como podriamos resolver la problematica de los accidentes.
Desde un café con figuras de cera de famosos Argentinos, hasta plazas, teatros, calles enteras y pizzerías de renombre internacional, todo se puede encontrar en ésta Comuna.

![Ruta Turistica](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/RecorridoTuristico.jpg?raw=true)


El recorrido turístico, a su vez, abarca toda la Cómuna 1 y en parte menor, otras comunas, pero principalmente la comuna 1 es la que más atracciones turísticas tiene.



# Trámites ciudadanos:
Otro gran punto a investigar, es la convergencia de todos los puntos principales de trámites para el ciudadano, desde un reclamo por un servicio hasta los trámites pertinentes para la transferencia de un vehiculo o inmueble tienen que pasar por oficinas ubicadas específicamente en la Comuna 1 como vemos a continuación: 

![Tramites](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/mapagestiones.png?raw=true)

# Conclusión

Estimamos que éstos puntos de interes que convergen en una misma zona, son los principales focos de problemáticas viales en la comuna investigada, aunque existe un plan de reducción de velocidad (Como lo son los topes, o llamados en argentina:Lomos de burro), sumando las cámaras con fotomulta, ésto no impide que cada tanto un conductor, taxista o chófer de colectivo que tenga los tiempos "apretados" exceda la velocidad límite especificada, provocando de esta manera un aumento en las probabilidades de participar en un siniestro vehicular 

### Cantidad de víctimas por tipo de vehículo:

![victimas x vehiculo](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/victimasxvehiculo.png?raw=true)

En éste grafico podemos observar los tipos de vehículo que conducían las víctimas por accidente, representando en primer lugar los motovehículos, seguido en segundo lugar por los peatones y en tercer lugar los automóviles, 

### Indicador de desempeño número 1: 

El Observatorio de Movilidad y Seguridad Vial (OMSV) nos solicitó 2 indicadores de desempeño, el primero nos pide como objetivo reducir en un 10% la tasa de mortalidad en la ciudad de Buenos aires, objetivo el cuál se cumple en ciertos rangos de tiempo 

![KPI](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/KPI1.png?raw=true)

Como se puede observar en la imagen, en el primer semestre de 2019 el objetivo se cumple en un -24.52% respecto al semestre numero 2 del año 2018, logrando ampliamente el objetivo solicitado

Si observamos con detenimiento, iterando entre años para ver los resultados, podemos ver que en el primer semestre del año 2020 se cumple en un -34.47%, asociamos esto debido a la pandemia del COVID-19, la cual instauró el aislamiento social y preventivo, permitiendo observar una disminución bastante grande de accidentes.

A comparación del primer semestre, el segundo semestre del 2020 fue más trágico, creemos que por contexto de el aislamiento, muchas personas querían visitar a sus familiares, no olvidemos que las personas mayores quedaron aisladas de su familia, lo cual, según observamos, terminó en tragedia, aumentando un 80% la tasa de accidentes para este semestre, sumandole las fiestas y vacaciones que tuvo la población.

### Indicador de desempeño número 2: 

Nuestro indicador de desempeño número  2 nos solicita cumplir con la baja de mortalidad para motovehículos en un -7% respecto al año anterior

![KPI2](https://github.com/TomasBasovich/PIDA/blob/main/Logos-ImagenesPIDA2/KP%C3%8C2.png?raw=true)

Se observa en los gráficos, que el año seleccionado es 2019, el cual cumple con el objetivo propuesto por el OMSV triplicando el descenso de la tasa de mortalidad en un -21.31% respecto al año 2018

Si observamos el año 2018, respecto al año 2017, la tasa de mortalidad por accidentes de motovehículo aumentó un 3.39%, incumpliendo con el objetivo propuesto, asociamos este aumento de los accidentes en motovehículos al famoso "Boom de los deliverys" que se instauró en argentina a partir de inicios del 2018, personalmente logré observar como los motovehículos incumplen varias normas de tránsito, aumentando asi las probabilidades de un accidente.

Éstas apps de delivery, le piden al motociclista, cumplir con los pedidos en cierto margen de tiempo, lo cual a veces los obliga a ponerse en situaciones de riesgo en el tráfico, lo cual puede ser una posible causa de siniestros donde la víctima o el acusado sea un motovehículo.

En ambos indicadores de desempeño tenemos puntos de observación que podrían ser analizados en profundidad para esclarecer éstos inconvenientes

Desde DriveGuard Safety Enterprise, la observación final que realizamos es que debe analizarse el curso que lleva el tráfico en las zonas de conflicto marcadas en los gráficos, como conclusión, observamos que los accidentes se suelen dar más en avenidas que en calles, y que las víctimas suelen ser motovehículos y peatones, ésto requiere de una inversión en infraestructura para poder lograr un tráfico más fluido, como lo es invertir en los llamados "lomos de burro" en calles o bien la instalación de semáforos en lugares donde los accidentes se den más amenudo, a su vez, instaurar consciencia en los peatones y conductores de diferentes vehículos podría ser un punto a favor en el futuro para lograr una reducción general de los siniestros de tránsito.



### Análisis y observaciones realizadas por el departamento de análisis de DriveGuard Safety Enterprise.


+ Link de Github: https://github.com/TomasBasovich/PIDA 