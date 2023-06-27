<div style="width: 50%; clear: both;">
<div style="float: left; width: 20%;">
<img src="https://www.laureate.net/wp-content/uploads/2019/03/10-UPC-Universidad-Peruana-de-Ciencias-Aplicadas.png", align="center">
</div>
</div>
<div style="width:100%;">&nbsp;</div>

# FDS-2023-1-CC52

<center><h1>Creacion de conocimiento aplicando la metodología CRISP-DM</h1></center>



**FUNDAMENTOS DE DATA SCIENCE** 

**TF – GRUPO 03** 

TEMA: Creacion de conocimiento aplicando la metodología CRISP-DM 

DOCENTE:  Patricia Daniela Reyes Silva** INTEGRANTES 

* Gonzales Astoray, Andrea Abigail               U20211C561 
* Marco Antonio Fuentes Rivera Onofre            U20211b693 
* Esteban Fabricio Cabrera Arbizu                 U202014600 

trabajofinal-grupo3

June 27, 2023

**1 Contenidos**

1. Introducción
1. Integrantes del grupo y roles
1. Metodología CRISP-DM
1. Comprensión del negocio
   1. Objetivos del proyecto
   1. Objetivos de Data Science
1. Comprensión de los datos 3.2.1.Recolectar los datos iniciales 3.2.2.Descripción de los datos 3.2.3.Exploración de los datos 3.2.4.Verificar la calidad de los datos
1. Preparacion de los datos

3\.3.1. Exploración de los datos 3.3.2.Construir los datos 3.3.3.Requerimientos

3. Modelado
4. Conclusiones
1. **1. Introducción**

Para este trabajo final de fundamentos de Data Science estaremos llevando a cabo un proyecto de analítica de datos a petición de una firma consultora con sede en Lima. El objetivo es comprender las características de los clientes que adquieren bicicletas, centrándonos principalmente en sus ingresos, edad y los vehículos adicionales que utilizan. Esto se hace con la finalidad de implementar un scoring de venta, identificando con ello los clientes más propensos a comprar una bicicleta.

2. **2. Integrantes del grupo y roles**

Integrante Rol Responsabilidades![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.003.png)![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.004.png)

2

Esteban Business Cabrera Project

Sponsor Abigail Data Gonzales Science

Marco Data Fuentes Engineer

- Liderar y supervisar el progreso del proyecto. - Promover y respaldar el proyecto en la organización.
- Analizar los datos y encontrar patrones significativos. - Aplicar técnicas de modelado y estadísticas para desarrollar el scoring. - Utilizar gráficos para visualizar los resultados y comunicar hallazgos importantes.
- Limpiar los datos, identificar y manejar los valores nulos y outliers. - Realizar transformaciones y preparación de datos para su posterior análisis.



3. **3. Metodología CRISP-DM![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.005.png)**
1. **3.1 Comprensión del negocio**
1. **Objetivos del proyecto:** Nuestro objetivo principal es analizar con detenimiento los datos acerca de los clientes interesados en comprar una bicicleta. Esto con la finalidad de hacer un scoring de venta que identifique los clientes más propensos a comprar una bicicleta.

Con ello, nos importa que estos datos sean de calidad y confiables, por ello, tenemos que: Pre- procesar y procesar los datos para así tenerlos con buena calidad. Con ello estaremos lidiando con valores nulos, repetido y atípicos (outliers). Y para hacer el scoring necesitamos:

- El promedio de ingresos de los clientes
- La distribución de: las regiones donde se encuentran los clientes, su distancia de viaje por su ocupación, su ocupación, estado civil, nivel educativo, género, edad, hijos y casa propia.
- Encontrar las relaciones vistas de acuerdo con las distribuciones antes mencionadas
- Ver la cantidad de clientes que tiene comprada una bicicleta.
2. **Objetivos de Data Science :** Nuestro objetivo en términos de Data Science predecir que tan propensos están los clientes de querer comprar una bicicleta por medio de su scoring.
2. **3.2 Comprensión de los datos**
1. **Recolección de los datos iniciales** La data llamado bike\_buyers fue proporcianado por la empresa Peru\_bike que dedicada a la venta de bicicletas esta data esta compuesta por un conjunto de datos que tiene detalles de 1000 usuarios de diferentes orígenes y si compran o no una bicicleta. Esta data contiene 13 campos como lo son: 1. ID: Numeric 2. Marital Status: Binary 3. Gender:Binary 4. Income: Numeric 5. Children: Numeric 6. Education:Sequential

7\. Occupation: Sequential 8. Home Owner:Binary 9. Cars: Numeric 10. Commute Distance: Numeric 11. Region:Nominal 12. Age:Numeric 13. Purchased Bike:Binary![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.006.png)

Variable Descripción![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.007.png)

ID Identificación del comprador

Marital Estado civil del comprador (casado o soltero) Status

|Variable|Descripción|
| - | - |
|Gender|Género del comprador (hombre o mujer)|
|Income|Ingresos del comprador en un determinado período de tiempo|
|Children|Número de hijos que tiene el comprador|
|Education|Antecedentes educativos del comprador (licenciatura, posgrado, escuela|
||secundaria, universidad parcial, etc.)|
|Occupation|Trabajo u ocupación del comprador (oficinista, administrativo, manual,|
||profesional, etc.)|
|Home Owner|Estado del comprador si posee o no una casa propia|
|Cars|Número de coches que posee el comprador|
|Commute|Distancia entre la casa del comprador y la empresa en la que trabaja (0-1|
|Distance|millas, 1-2 millas, 10+ millas, etc.)|
|Region|Región donde vive el comprador (Europa, América del Norte, el Pacífico, etc.)|
|Age|Edad del comprador|
|Purchased|Estado del comprador si ha comprado la bicicleta o no|
|Bike||


2. **Descripción de los datos**
2. **Exploración de los datos** Importamos las libreraias a usar

[ ]: **import pandas as pd![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.008.png)**

**from tabulate import** tabulate

**import plotly.graph\_objects as ply**

**import plotly.express as px**

**import missingno as msno** *#visualizar los datos faltantes* **from plotly.subplots import** make\_subplots

**import numpyas np**

#####Cargar los datos

cargamos la dataset de un csv llamado **bike\_buyes**

[ ]: datos = pd.read\_csv('/content/bike\_buyers.csv')![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.009.png)

data\_bike = pd.DataFrame(datos)

data\_bike.head()

[ ]: ID Marital Status Gender Income Children Education \

0  12496 Married Female 40000.0 1.0 Bachelors
0  24107 Married Male 30000.0 3.0 Partial College
0  14177 Married Male 80000.0 5.0 Partial College
0  24381 Single NaN 70000.0 0.0 Bachelors
0  25597 Single Male 30000.0 0.0 Bachelors

Occupation Home Owner Cars Commute Distance Region Age \

0 Skilled Manual Yes 0.0 0-1 Miles Europe 42.0 1 Clerical Yes 1.0 0-1 Miles Europe 43.0

2  Professional No 2.0 2-5 Miles Europe 60.0
2  Professional Yes 1.0 5-10 Miles Pacific 41.0 4 Clerical No 0.0 0-1 Miles Europe 36.0

Purchased Bike

0 No 1 No 2 No 3 Yes 4 Yes

#####Inspeccionar los datos

Para esta inspeccion de datos tendremos en cuenta ciertos puntos

- Saber cuantas filas y columnas tiene nuestra data
- Nombre de cada columna
- El tipo de dato que tiene cada columna
- Tablas de frecuencia

1\.Saber cuantas filas y columnas tiene nuestra data

[ ]: print("Estamos evaluando", data\_bike.shape[0] ,"filas con ",data\_bike.shape[1]␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.010.png)

↪, "columnas")

Estamos evaluando 1000 filas con 13 columnas

2\.Nombre de cada columna

[ ]: print("Nombres de columnas")![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.011.png)

tabla = []

**for** columna **in** data\_bike.columns:

tabla.append(columna) pd.DataFrame(tabla, columns='Columna'.split())

Nombres de columnas

[ ]: Columna 0 ID 1 Marital Status

2 Gender 3 Income 4 Children

5 Education

6 Occupation

7 Home Owner 8 Cars 9 Commute Distance 10 Region 11 Age

12 Purchased Bike

3\.El tipo de dato que tiene cada columna

[ ]: print("Tipos de datos")![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.012.png)

tabla = []

**for** columna **in** data\_bike.columns:

tabla.append([columna, data\_bike[columna].dtype])          pd.DataFrame(tabla, columns='Columna Tipo\_de\_dato'.split())

Tipos de datos

[ ]: Columna Tipo\_de\_dato

0 ID int64 1 Marital Status object 2 Gender object 3 Income float64 4 Children float64 5 Education object 6 Occupation object 7 Home Owner object 8 Cars float64 9 Commute Distance object 10 Region object 11 Age float64 12 Purchased Bike object

4. Contenido de la data

[ ]: data\_bike.head()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.013.png)

[ ]: ID Marital Status Gender Income Children Education \

0  12496 Married Female 40000.0 1.0 Bachelors
0  24107 Married Male 30000.0 3.0 Partial College
0  14177 Married Male 80000.0 5.0 Partial College
0  24381 Single NaN 70000.0 0.0 Bachelors
0  25597 Single Male 30000.0 0.0 Bachelors

Occupation Home Owner Cars Commute Distance Region Age \

0 Skilled Manual Yes 0.0 0-1 Miles Europe 42.0 1 Clerical Yes 1.0 0-1 Miles Europe 43.0

2  Professional No 2.0 2-5 Miles Europe 60.0
2  Professional Yes 1.0 5-10 Miles Pacific 41.0

4 Clerical No 0.0 0-1 Miles Europe 36.0

Purchased Bike

0 No 1 No 2 No 3 Yes 4 Yes

5. Tablas de frecuencia

Enesta tabla de frecuencia puedo acceder a un resumen de cinco números para valores int.Donde puedo observar y saber los cuartiles medios y medianos y puedo con solo observar esta tabla, puedo decir que la edad promedio de 1000 usuarios que compran o no bicicleta es 44.

[ ]: data\_bike.describe()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.014.png)

[ ]: ID Income Children Cars Age

count 1000.000000 994.000000 992.000000 991.000000 992.000000 mean 19965.992000 56267.605634 1.910282 1.455096 44.181452

std 5347.333948 31067.817462 1.626910 1.121755 11.362007 min 11000.000000 10000.000000 0.000000 0.000000 25.000000

25% 15290.750000 30000.000000 0.000000 1.000000 35.000000

50% 19744.000000 60000.000000 2.000000 1.000000 43.000000

75% 24470.750000 70000.000000 3.000000 2.000000 52.000000

max 29447.000000 170000.000000 5.000000 4.000000 89.000000

**Visualizar los datos** Para este apartado mostraremos 4 graficas para poder vizualizar mejor los datos

- Grafica de barras (Marital Status): En esta grafica podremos observar los tipos de estado civil de los usarios como tambien la cantidad que hay por cada tipo .
- Grafica de barras (Regiones): En esta grafica podremos observar cuantas usarios hay por region como tambien cuantos de estos usuarios compraron una bicicleta.
- Gráfico circular (Nivel educativo): En esta grafica podremos observar el porcentaje que hay por cada tipo de nivel educativo que los usarios. Para su mejor comprension tambien invluimos una tabla donde podemos observar las cantidades de dicho porcentaje.
- Gráfico circular (Ocupación): Para esta grafica observaremos los tipos de ocupaciones que hay en la data set como tambien el porcentaje por tipo de ocupación , tambien para su mejor compresion creamos una tabla que muestra las cantidades de usarios por ocupación.

tambien para poder distingir los valores de otros usaremos un arreglo de colores [ ]: colores = ['blue', 'green', 'red', 'orange', 'purple']![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.015.png)

Grafica 1

[ ]: tabla\_frecuencia\_status = pd.value\_counts(data\_bike['Marital Status']) fig![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.016.png) = ply.Figure(data=[ply.Bar(x=tabla\_frecuencia\_status.index,␣ ↪y=tabla\_frecuencia\_status.values, marker=dict(color=colores))]) fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.017.png)

- black;">Distribucion de estado civil</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis\_title="Estado Civil",

yaxis\_title="Cantidad",

width=600,

height=400

)

fig.show()

Grafica 2

[ ]: tabla\_frecuencia\_region = data\_bike['Region'].value\_counts()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.018.png)

compradores\_bicicleta = data\_bike[data\_bike['Purchased Bike'] == 'Yes'] tabla\_frecuencia\_compradores = compradores\_bicicleta['Region'].value\_counts() fig = ply.Figure(data=[

ply.Bar(x=tabla\_frecuencia\_region.index, y=tabla\_frecuencia\_region.values,␣ ↪name='Total de usuarios por region'),

ply.Bar(x=tabla\_frecuencia\_compradores.index,␣ ↪y=tabla\_frecuencia\_compradores.values, name='Compradores de Bicicleta')

])

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Ventas de bicicletas por region</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis\_title="Región", yaxis\_title="Cantidad de Registros", width=600,

height=400,

barmode='overlay', template='plotly\_white'

)

fig.show()

Grafica 3

[ ]: tabla\_frecuencia\_education = data\_bike['Education'].value\_counts()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.019.png)

fig = ply.Figure(data=[ply.Pie(labels=tabla\_frecuencia\_education.index,␣

↪values=tabla\_frecuencia\_education.values)])

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.020.png)

- black;">Distribucion de nivel educativo</span></b>',

'x': 0.5,

'y': 0.95,

},

showlegend=**True**,

width=600,

height=400

)

fig.show()

[ ]: tabla = []![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.021.png)

**for** tipo\_education, frecuencia **in** tabla\_frecuencia\_education.items():

tabla.append([tipo\_education, frecuencia])

pd.DataFrame(tabla, columns=['Education', 'Cantidad'])

[ ]: Education Cantidad

0 Bachelors 306 1 Partial College 265 2 High School 179 3 Graduate Degree 174

4  Partial High School 76

Grafica 4

[ ]: tabla\_frecuencia\_ocupacion= data\_bike['Occupation'].value\_counts()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.022.png)

fig = ply.Figure(data=[ply.Pie(labels=tabla\_frecuencia\_ocupacion.index,␣

↪values=tabla\_frecuencia\_ocupacion.values)])

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Distribución ocupacional</span></b>',

'x': 0.5,

'y': 0.95,

},

showlegend=**True**,

width=600,

height=400

)

fig.show()

[ ]: tabla = []![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.023.png)

**for** ocupacion, frecuencia **in** tabla\_frecuencia\_ocupacion.items():

tabla.append([ocupacion, frecuencia])

pd.DataFrame(tabla, columns=['Ocupacion', 'Cantidad']) ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.024.png)[ ]: Ocupacion Cantidad

0  Professional 276
0  Skilled Manual 255

2 Clerical 177

3 Management 173

4 Manual 119

4. **Verificar la calidad de los datos![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.025.png)**

[ ]: *# Muestra información sobre las columnas, tipos de datos y valores no nulos*

print(data\_bike.info())

<class 'pandas.core.frame.DataFrame'> RangeIndex: 1000 entries, 0 to 999

Data columns (total 13 columns):

- Column Non-Null Count Dtype

\--- ------ -------------- -----

0  ID 1000 non-null int64
0  Marital Status 993 non-null object
0  Gender 989 non-null object
0  Income 994 non-null float64
0  Children 992 non-null float64
0  Education 1000 non-null object
0  Occupation 1000 non-null object
0  Home Owner 996 non-null object
0  Cars 991 non-null float64
0  Commute Distance 1000 non-null object
0  Region 1000 non-null object
0  Age 992 non-null float64
0  Purchased Bike 1000 non-null object

dtypes: float64(4), int64(1), object(8)

memory usage: 101.7+ KB

None

Para vizualizar mejor esta tabla usaremos grafico donde mostrara a los datos de cada columna . Las lineas blancas que se observan en la grafica representan los datos vacios que hay en cada columna.

[ ]: msno.matrix(data\_bike) ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.026.png)[ ]: <Axes: >

![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.027.png)

Teniendo conocimiento en que columna se encuentran los valores vacios o nulos procederemos a encontrar la cantidad mediante una grafica de barras .

[ ]: null\_counts = data\_bike.isnull().sum()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.028.png)

fig = ply.Figure(data= ply.Bar(x=null\_counts.index, y=null\_counts.values)) fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Valores nulos o vacios por coolumna</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis\_title='Columna',

yaxis\_title='Cantidad de Valores Nulos'

)

fig.show()

Ahora procederomos a ubicar lso valores vacios de acuerdon con los ID de los usuarios y lo mostraremos en una tabla para su mejor vizualisacion.

[ ]: columnas\_verificar = ['Marital Status', 'Gender', 'Income', 'Children', 'Home␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.029.png)

↪Owner', 'Cars', 'Age']

registros\_vacios = data\_bike[data\_bike[columnas\_verificar].isnull().any(axis=1)]

registros\_vacios['User ID'] = registros\_vacios.index registros\_vacios.rename(columns={'User ID': 'ID de Usuario'})

<ipython-input-219-337ddea59a4b>:4: SettingWithCopyWarning:

A value is trying to be set on a copy of a slice from a DataFrame. Try using .loc[row\_indexer,col\_indexer] = value instead

See the caveats in the documentation: https://pandas.pydata.org/pandas- docs/stable/user\_guide/indexing.html#returning-a-view-versus-a-copy

[ ]: ID Marital Status Gender Income Children Education \

3 24381 Single NaN 70000.0 0.0 Bachelors

6 27974 Single Male 160000.0 2.0 High School

8  22155 NaN Male 20000.0 2.0 Partial High School
8  19280 Married Male NaN 2.0 Partial College

12 11434 Married Male 170000.0 5.0 Partial College

27 18283 NaN Female 100000.0 0.0 Bachelors

49 14939 NaN Male 40000.0 0.0 Bachelors

98 19441 NaN Male 40000.0 0.0 Graduate Degree

110 21006 Single Female NaN 1.0 Partial College

117 24065 Single Female 20000.0 NaN High School

150 26154 NaN Male 60000.0 1.0 Partial College

154 23426 Single NaN 80000.0 5.0 Graduate Degree

191 26944 Single Male NaN 2.0 High School

196 16209 Single Female 50000.0 0.0 Graduate Degree

202 18626 Single Male 40000.0 2.0 Partial College

217 13673 Single Female 20000.0 NaN Partial High School

225 14135 Married Male 20000.0 1.0 Partial College

234 24611 NaN Male 90000.0 0.0 Bachelors

301 17926 NaN Female NaN 0.0 Bachelors

335 24369 Married NaN 80000.0 5.0 Graduate Degree

351 13572 Single Male 10000.0 3.0 High School

365 22636 Single Female 40000.0 0.0 Bachelors

371 22918 Single Male 80000.0 5.0 Graduate Degree

386 28957 Single Female 120000.0 NaN Partial High School

441 11061 Married Male NaN 2.0 Partial College

448 11383 Married Female 30000.0 3.0 Graduate Degree

509 24357 Married Male NaN 3.0 Bachelors

511 12207 Single Male 80000.0 4.0 Bachelors

549 13453 Married Female 130000.0 NaN Bachelors

554 18580 Married Female 60000.0 2.0 Graduate Degree

561 27218 Married Female 20000.0 2.0 Partial High School

601 29231 Single NaN 80000.0 4.0 Partial College

615 11538 Single Female 60000.0 4.0 Graduate Degree

638 18949 Single Male 70000.0 NaN Graduate Degree

646 16247 Single Female 60000.0 4.0 Graduate Degree

688 11699 Single NaN 60000.0 NaN Bachelors

695 18390 Married NaN 80000.0 5.0 Partial College

770 17699 Married Male 60000.0 1.0 Graduate Degree

805 26778 Single Female 40000.0 NaN High School

11

867 26693

908 23195

933 11941

943 24322

951 22296

960 23491

973 11734

986 23704

997 11809

Married NaN

Single NaN

Single Male Married Female Married NaN

Single Male Married NaN

Single Male Married NaN

70000.0 3.0 50000.0 3.0 60000.0 0.0 60000.0 4.0 70000.0 0.0 100000.0 NaN 60000.0 1.0 40000.0 5.0 60000.0 2.0

Partial College Bachelors

Partial College

Bachelors Bachelors

Partial College Partial College

High School Bachelors

12

Occupation Home Owner 3 Professional Yes 6 Management NaN 8 Clerical Yes 9 Manual Yes 12 Professional Yes 27 Professional No 49 Clerical Yes 98 Clerical Yes 110 Manual No 117 Manual Yes 150 Skilled Manual Yes 154 Management Yes 191 Manual Yes 196 Skilled Manual Yes 202 Clerical Yes 217 Manual No 225 Manual Yes 234 Professional No 301 Clerical No 335 Management No 351 Manual Yes 365 Clerical NaN 371 Management Yes 386 Professional Yes 441 Skilled Manual Yes 448 Clerical Yes 509 Professional Yes 511 Management Yes 549 Management Yes 554 Professional Yes 561 Clerical No 601 Professional No 615 Skilled Manual No 638 Management Yes 646 Skilled Manual NaN 688 Skilled Manual No

Cars Commute Distance

1\.0 5-10 Miles

4\.0 0-1 Miles

2\.0 5-10 Miles

1\.0 0-1 Miles NaN 0-1 Miles

1\.0 5-10 Miles

0\.0 0-1 Miles

0\.0 0-1 Miles

0\.0 0-1 Miles

0\.0 0-1 Miles

1\.0 5-10 Miles

3\.0 0-1 Miles

0\.0 0-1 Miles NaN 1-2 Miles NaN 1-2 Miles

2\.0 0-1 Miles

0\.0 1-2 Miles

4\.0 10+ Miles

0\.0 0-1 Miles

2\.0 0-1 Miles NaN 0-1 Miles

0\.0 0-1 Miles

3\.0 0-1 Miles

4\.0 10+ Miles

2\.0 5-10 Miles NaN 0-1 Miles

1\.0 2-5 Miles NaN 5-10 Miles

3\.0 0-1 Miles

0\.0 2-5 Miles NaN 0-1 Miles

2\.0 0-1 Miles NaN 0-1 Miles

2\.0 5-10 Miles

0\.0 1-2 Miles

2\.0 0-1 Miles

Region Age \ Pacific 41.0 Pacific 33.0 Pacific 58.0 Europe NaN Europe 55.0 Pacific 40.0 Europe 39.0 Europe NaN Europe 46.0 Europe 40.0 Pacific 43.0 Pacific 40.0 Europe 36.0 Europe 36.0 Europe 33.0 Europe 25.0 Europe NaN Pacific 35.0 Pacific 28.0 Pacific 39.0 Europe 37.0 Europe 38.0 Pacific NaN Pacific 34.0 Pacific 52.0 Europe 46.0

North America 48.0 North America 66.0 North America 45.0 North America NaN North America 48.0 North America 43.0 North America 47.0 North America 74.0 North America 47.0 North America NaN



695 Professional

770 Skilled Manual

805 Skilled Manual

867 Professional

908 Skilled Manual

933 Skilled Manual

943 Skilled Manual

951 Professional

960 Professional

973 Skilled Manual

986 Professional

997 Skilled Manual

Yes 2.0 0-1 Miles

No 0.0 0-1 Miles Yes 2.0 5-10 Miles Yes 1.0 5-10 Miles Yes 2.0 2-5 Miles Yes NaN 5-10 Miles NaN 2.0 0-1 Miles

No 1.0 0-1 Miles

No 4.0 1-2 Miles

No 1.0 0-1 Miles Yes 4.0 10+ Miles Yes 0.0 0-1 Miles

North America 44.0 North America NaN North America 31.0 North America 49.0 North America 41.0 North America 29.0 North America 42.0 North America 38.0 North America 45.0 North America 47.0

North America NaN North America 38.0

13

Purchased Bike ID de Usuario

3 Yes 3 6 Yes 6 8 No 8 9 Yes 9 12 No 12 27 No 27 49 Yes 49 98 Yes 98 110 Yes 110 117 Yes 117 150 Yes 150 154 No 154 191 Yes 191 196 No 196 202 Yes 202 217 No 217 225 No 225 234 Yes 234 301 Yes 301 335 No 335 351 Yes 351 365 Yes 365 371 No 371 386 Yes 386 441 Yes 441 448 No 448 509 Yes 509 511 Yes 511 549 Yes 549 554 Yes 554 561 No 561 601 No 601 615 Yes 615 638 Yes 638 646 No 646 688 No 688 695 No 695 770 No 770 805 No 805 867 No 867 908 Yes 908 933 No 933 943 No 943 951 No 951 960 No 960 973 No 973 986 Yes 986 997 Yes 997

Ahora procederemos a encontrar los valores que pueden estar fuera de rango.Para eso usaremos dos tipos de grafica un histograma y y la otra una grafica de cajas

[ ]: *# Histograma de Income![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.030.png)*

fig1 = px.histogram(data\_bike, x='Income', nbins=20, title='Histograma de␣

↪Income',width=600, height=400)

fig1.show()

En esta grafica podemos observar que hay un liguero salto en los ingresos desde 130k a 150k. [ ]: fig = ply.Figure()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.031.png)

fig.add\_trace(ply.Box(y=data\_bike['Children'], name='Children')) fig.add\_trace(ply.Box(y=data\_bike['Cars'], name='Cars')) fig.add\_trace(ply.Box(y=data\_bike['Age'], name='Age'))

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Datos fuera de rango</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis=dict(

title={

'text':'<b><span style="font-family:Calibri;>Variables</span></b>'

}

),

yaxis=dict(

title={

'text':'<b><span style="font-family:Calibri;>Valores</span></b>'

}![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.032.png)

),

boxmode='group' )

fig.show()

Para esta grafica usamos tres graficos de cajas tanto para las columnas children , cars , age que son valores numericos . Como podermos observar , solo la columna cars y age tienen bigotes es decir tienen posibles datos fuera de rango.

Ahora pasaremos a ubicar dichos valores fuera de rango . Para eso creamos una función llamado **Outliers(columna)** que calcula los valores atípicos (outliers) de una columna específica en el dataframe data\_bike. Para este caso como observamos en la grafica solo evaluaremos para las columnas **Cars y Age**

[ ]: **def** Outliers(columna):![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.033.png)

Q1 = data\_bike[columna].quantile(0.25)

Q3 = data\_bike[columna].quantile(0.75)

IQR = Q3 - Q1

lower\_limit = Q1 - 1.5 \* IQR

upper\_limit = Q3 + 1.5 \* IQR

outliers = data\_bike[(data\_bike[columna] < lower\_limit) | (data\_bike[columna]␣ ↪> upper\_limit)]

outliers\_table = outliers[['ID', columna]]

**return** outliers\_table

esta funcion trabaja con los cuartiles , estos datos lo podemos ubicar en la Tablas de frecuencia [ ]: print("Valores atipicos Income(Ingresos) : " , len(Outliers('Income')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.034.png)

print("---------------------------------")

Outliers('Income')

Valores atipicos Income(Ingresos) : 10 ---------------------------------

[ ]: ID Income

6 27974 160000.0

12 11434 170000.0

43 17185 170000.0

121 15922 150000.0

178 14191 160000.0

259 12705 150000.0

321 16675 160000.0

356 23608 150000.0

829 16009 170000.0

993 11292 150000.0

[ ]: print("Valores atipicos Cars : ",len(Outliers('Cars')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.035.png)

print("---------------------------------") Outliers('Cars')

Valores atipicos Cars : 59 ---------------------------------

[ ]: ID Cars

6 27974 4.0

11 12697 4.0

21 21564 4.0

51 20619 4.0

57 20567 4.0

70 14238 4.0

72 24857 4.0

75 12678 4.0

87 19608 4.0

121 15922 4.0

123 23627 4.0

125 29301 4.0

156 12664 4.0

170 17203 4.0

184 28918 4.0

188 20606 4.0

193 26032 4.0

213 11451 4.0

223 18711 4.0

234 24611 4.0

245 18494 4.0

247 21568 4.0

252 12666 4.0

258  14193 4.0
258  12705 4.0

286 29120 4.0

333 18160 4.0

338 15926 4.0

374 16179 4.0

386 28957 4.0

400 25792 4.0

409 22821 4.0

420 18153 4.0

456 26385 4.0

458 21560 4.0

486 26415 4.0

503 20339 4.0

505 15940 4.0

544 24397 4.0

577 16917 4.0

598 24398 4.0

613  25184 4.0
613  14469 4.0

620 11259 4.0

665 14443 4.0

675 18517 4.0

702 13314 4.0

708 18069 4.0

721 13287 4.0

733 23027 4.0

768  13313 4.0
768  18952 4.0

829 16009 4.0

850 12205 4.0

869 26065 4.0

917 22719 4.0

960 23491 4.0

981 15982 4.0

986 23704 4.0

[ ]: print("Valores atipicos Age : ",len(Outliers('Age')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.036.png)

print("---------------------------------") Outliers('Age')

Valores atipicos Age : 4 ---------------------------------

[ ]: ID Age

250 22931 78.0

375 15628 89.0

401 11555 80.0

595 18058 78.0

[ ]: print("Mid-range para Income:", ((data\_bike['Income'].min() +␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.037.png)

↪data\_bike['Income'].max()) / 2)) *#Mid-range = (max+min)/2*

print("Mid-range para Age:", ((data\_bike['Age'].min() + data\_bike['Age'].max())␣

↪/ 2))

print("Mid-range para Children:", ((data\_bike['Children'].min() +␣

↪data\_bike['Children'].max()) / 2))

print("Mid-range para Cars:", ((data\_bike['Cars'].min() + data\_bike['Cars'].

↪max()) / 2))

Mid-range para Income: 90000.0 Mid-range para Age: 57.0 Mid-range para Children: 2.5 Mid-range para Cars: 2.0

[ ]: print("Max-Min para Age:", data\_bike['Age'].max() - data\_bike['Age'].min()) ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.038.png)print("Max-Min para Income:", data\_bike['Income'].max() - data\_bike['Income'].

↪min())

print("Max-Min para Children:", data\_bike['Children'].max() -␣

↪data\_bike['Children'].min())

print("Max-Min para Cars:", data\_bike['Cars'].max() - data\_bike['Cars'].min())

Max-Min para Age: 64.0 Max-Min para Income: 160000.0 Max-Min para Children: 5.0 Max-Min para Cars: 4.0

La correlación más alta entre la edad y los niños. [ ]: data\_bike.corr()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.039.png)

<ipython-input-228-fecffa8fb0bd>:1: FutureWarning:

The default value of numeric\_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric\_only to silence this warning.

[ ]: ID Income Children Cars Age

ID 1.000000 -0.075081 -0.028747 0.022125 -0.054238 Income -0.075081 1.000000 0.261053 0.439980 0.170845 Children -0.028747 0.261053 1.000000 0.280243 0.531668 Cars 0.022125 0.439980 0.280243 1.000000 0.186398

Age -0.054238 0.170845 0.531668 0.186398 1.000000

3. **3.3 Preparacion de los datos**
1. **Limpiar Datos** En esta primera parte del preprocesamiento, se identifican los valores NULL o ”” y los combertimos a NA, Con el fin de sustituirlos por una tendencia central como la mediana o la moda.

[ ]: data\_bike = data\_bike.replace(['""', 'NULL'], 'NA')![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.040.png)

Creaamos una funcion que nos dara la mediana o la moda, pasandole como parametro el tipo de tendencia central y la columna de la tabla

[ ]: **def** change(columna, tipo):![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.041.png)

**if** tipo =="mediana":

valor = columna.median()

**elif** tipo == "moda":

valor1 = columna.mode()

valor = valor1[0]

columna.fillna(valor, inplace = **True**)

Tras la visuzalizacion anterior nos percatamos de ciertas columnas que tiene valores NA, por lo que aahora se tiene que cambiar por el de la mediana o la moda.

[ ]: **from pandas.core.dtypes.astype import** astype\_nansafe![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.042.png)

change(data\_bike["Marital Status"], "moda") change(data\_bike["Gender"], "moda") change(data\_bike["Income"], "mediana") change(data\_bike["Children"], "mediana") change(data\_bike["Home Owner"], "moda") change(data\_bike["Cars"], "mediana") change(data\_bike["Age"], "mediana")

Visualizamos

[ ]: msno.matrix(data\_bike) ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.043.png)[ ]: <Axes: >

![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.044.png)

Ahora tenemos que pasar los datos objetos a datos categorico Y para ver el tipo de dato, usamos info.

[ ]: print(data\_bike.info())![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.045.png)

<class 'pandas.core.frame.DataFrame'> RangeIndex: 1000 entries, 0 to 999

Data columns (total 13 columns):

- Column Non-Null Count Dtype

\--- ------ -------------- -----

0  ID 1000 non-null int64
0  Marital Status 1000 non-null object
0  Gender 1000 non-null object
3  Income 1000 non-null float64
3  Children 1000 non-null float64
3  Education 1000 non-null object
3  Occupation 1000 non-null object
3  Home Owner 1000 non-null object
3  Cars 1000 non-null float64
3  Commute Distance 1000 non-null object
3  Region 1000 non-null object
3  Age 1000 non-null float64
3  Purchased Bike 1000 non-null object

dtypes: float64(4), int64(1), object(8)

memory usage: 101.7+ KB

None

**outliers**

Para este caso, se obervo que los datos como cars, income y age presentaban valore atipicos o outliers, donde la cantidad de valores en cars seria 59 valores, mientras que en income 10 y age son 4, dichos outliers no son una datos errados, si no que son casos contextuales atipicos.

Como se muetra en las tablas de arriba, para fines didacticos, se volveran a motrar [ ]: print("Valores atipicos Income(Ingresos) : " , len(Outliers('Income')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.046.png)

print("---------------------------------")

Outliers('Income')

Valores atipicos Income(Ingresos) : 10 ---------------------------------

[ ]: ID Income

6 27974 160000.0

12 11434 170000.0

43 17185 170000.0

121 15922 150000.0

178 14191 160000.0

259 12705 150000.0

321 16675 160000.0

356 23608 150000.0

829 16009 170000.0

993 11292 150000.0

[ ]: print("Valores atipicos Income(Ingresos) : " , len(Outliers('Income')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.047.png)

print("---------------------------------")

Outliers('Cars')

Valores atipicos Income(Ingresos) : 10 ---------------------------------

[ ]: ID Cars

6 27974 4.0

11 12697 4.0

21 21564 4.0

51 20619 4.0

57 20567 4.0

70 14238 4.0

72 24857 4.0

75 12678 4.0

87 19608 4.0

121 15922 4.0

123 23627 4.0

125 29301 4.0

156 12664 4.0

170 17203 4.0

184 28918 4.0

188 20606 4.0

193 26032 4.0

213 11451 4.0

223 18711 4.0

234 24611 4.0

245 18494 4.0

247 21568 4.0

252 12666 4.0

258  14193 4.0
258  12705 4.0

286 29120 4.0

333 18160 4.0

338 15926 4.0

374 16179 4.0

386 28957 4.0

400 25792 4.0

409 22821 4.0

420 18153 4.0

456 26385 4.0

458 21560 4.0

486 26415 4.0

503 20339 4.0

505 15940 4.0

544 24397 4.0

577 16917 4.0

598 24398 4.0

613  25184 4.0
613  14469 4.0

620 11259 4.0

665 14443 4.0

675 18517 4.0

21

702 13314 4.0

708 18069 4.0

721 13287 4.0

733 23027 4.0

768  13313 4.0
768  18952 4.0

829 16009 4.0

850 12205 4.0

869 26065 4.0

917 22719 4.0

960 23491 4.0

981 15982 4.0

986 23704 4.0

[ ]: print("Valores atipicos Income(Ingresos) : " , len(Outliers('Income')) )![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.048.png)

print("---------------------------------")

Outliers('Age')

Valores atipicos Income(Ingresos) : 10 ---------------------------------

[ ]: ID Age

250 22931 78.0

375 15628 89.0

401 11555 80.0

595 18058 78.0

Para la exportacion a un archivo csv:

[ ]: **def** guardar\_datos\_en\_csv(datos, nombre\_archivo):![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.049.png)

**try**:

datos.to\_csv(nombre\_archivo, index=**False**)

print(f"Los datos se han guardado en el archivo **{**nombre\_archivo**}**.") **except IOError as** e:

print(f"Error al guardar los datos en el archivo CSV: **{**e**}**")

guardar\_datos\_en\_csv(data\_bike, "data\_bike\_clean.csv")

Los datos se han guardado en el archivo data\_bike\_clean.csv.

Para seguir trabajando con la data ya limpia guadaremos el bike\_buyers\_clean.csv en una variable. [ ]: data\_bike\_clean = pd.read\_csv('/content/data\_bike\_clean.csv')![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.050.png)

data\_bike\_clean = pd.DataFrame(data\_bike\_clean)

data\_bike\_clean.head()

[ ]: ID Marital Status Gender Income Children Education \

0  12496 Married Female 40000.0 1.0 Bachelors
1  24107 Married Male 30000.0 3.0 Partial College
1  14177 Married Male 80000.0 5.0 Partial College
1  24381 Single Male 70000.0 0.0 Bachelors
1  25597 Single Male 30000.0 0.0 Bachelors

Occupation Home Owner Cars Commute Distance Region Age \

0 Skilled Manual Yes 0.0 0-1 Miles Europe 42.0 1 Clerical Yes 1.0 0-1 Miles Europe 43.0

2  Professional No 2.0 2-5 Miles Europe 60.0
2  Professional Yes 1.0 5-10 Miles Pacific 41.0

4 Clerical No 0.0 0-1 Miles Europe 36.0

Purchased Bike

0 No 1 No 2 No 3 Yes 4 Yes

2. **Construir los datos![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.051.png)**

[ ]: categoric=[x **for** x **in** data\_bike\_clean.columns **if** data\_bike\_clean[x].

↪dtypes=='object']

categoric

[ ]: ['Marital Status',

'Gender',

'Education',

'Occupation',

'Home Owner',

'Commute Distance',

'Region',

'Purchased Bike']

[ ]: numeric=[y **for** y **in** data\_bike\_clean.columns **if** data\_bike\_clean[y].dtypes!![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.052.png)

↪='object']

numeric

[ ]: ['ID', 'Income', 'Children', 'Cars', 'Age']

trasformaremos a las variables que sean binarias en 1 y 0 para poder trabajar en el modelado transformar género sí a 1 no a 0 es más útil para el modelado.

[ ]: data\_bike.head()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.053.png)

[ ]: ID Marital Status Gender Income Children Education \

0  12496 Married Female 40000.0 1.0 Bachelors
1  24107 Married Male 30000.0 3.0 Partial College
1  14177 Married Male 80000.0 5.0 Partial College
1  24381 Single Male 70000.0 0.0 Bachelors
1  25597 Single Male 30000.0 0.0 Bachelors

Occupation Home Owner Cars Commute Distance Region Age \

0 Skilled Manual Yes 0.0 0-1 Miles Europe 42.0 1 Clerical Yes 1.0 0-1 Miles Europe 43.0

2  Professional No 2.0 2-5 Miles Europe 60.0
2  Professional Yes 1.0 5-10 Miles Pacific 41.0

4 Clerical No 0.0 0-1 Miles Europe 36.0

Purchased Bike

0 No 1 No 2 No 3 Yes 4 Yes

[ ]: data\_bike\_clean['Gender'] = np.where(data\_bike\_clean['Gender'] == 'Female', 1,␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.054.png)

↪0)

data\_bike\_clean.head()

[ ]: ID Marital Status Gender Income Children Education \

0  12496 Married 1 40000.0 1.0 Bachelors
0  24107 Married 0 30000.0 3.0 Partial College
0  14177 Married 0 80000.0 5.0 Partial College
0  24381 Single 0 70000.0 0.0 Bachelors
0  25597 Single 0 30000.0 0.0 Bachelors

Occupation Home Owner Cars Commute Distance Region Age \

0 Skilled Manual Yes 0.0 0-1 Miles Europe 42.0 1 Clerical Yes 1.0 0-1 Miles Europe 43.0

2  Professional No 2.0 2-5 Miles Europe 60.0
2  Professional Yes 1.0 5-10 Miles Pacific 41.0

4 Clerical No 0.0 0-1 Miles Europe 36.0

Purchased Bike

0 No 1 No 2 No 3 Yes 4 Yes

[ ]: *#transformar Bicicleta\_Comprada sí a 1 no a 0![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.055.png)*

data\_bike\_clean['Purchased Bike'] = np.where(data\_bike\_clean['Purchased Bike']␣

↪== 'Yes', 1, 0)

[ ]: *#transformar Home Owner si es dueño de una propiedad sí a 1 no a 0 ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.035.png)*data\_bike\_clean['Home Owner'] = np.where(data\_bike\_clean['Home Owner'] ==␣

↪'Yes', 1, 0)

[ ]: *#no se puede trasformar a 1 y 0 porque no es binario![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.056.png)*

data\_bike\_clean.Occupation.unique

[ ]: <bound method Series.unique of 0 Skilled Manual

1 Clerical

2 Professional

3 Professional

4 Clerical

…

995 Professional

996 Professional 997 Skilled Manual 998 Management

999 Professional

Name: Occupation, Length: 1000, dtype: object>

[ ]: data\_bike\_clean.Region.unique![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.057.png)

[ ]: <bound method Series.unique of 0 Europe

1 Europe

2 Europe

3 Pacific

4 Europe

…

995  North America
995  North America
995  North America
995  North America
995  North America

Name: Region, Length: 1000, dtype: object>

[ ]: display(data\_bike\_clean.dtypes)![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.058.png)

ID int64 Marital Status object Gender int64 Income float64 Children float64 Education object Occupation object Home Owner int64 Cars float64 Commute Distance object Region object Age float64 Purchased Bike int64 dtype: object

[ ]: data\_bike\_clean['Cars'] = data\_bike\_clean['Cars'].astype(int)![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.059.png)

data\_bike\_clean['Age'] = data\_bike\_clean['Age'].astype(int) data\_bike\_clean['Children'] = data\_bike\_clean['Children'].astype(int)

display(data\_bike\_clean.dtypes)

ID int64 Marital Status object Gender int64 Income float64 Children int64 Education object Occupation object Home Owner int64 Cars int64 Commute Distance object Region object Age int64 Purchased Bike int64 dtype: object

3. **Requerimientos**

**1. ¿Cuánto es el promedio de ingresos de los clientes?![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.060.png)**

[ ]: promedio\_income = data\_bike\_clean['Income'].mean()

fig = ply.Figure()

fig.add\_trace(ply.Scatter(x=data\_bike\_clean.index, y=data\_bike\_clean['Income'],␣

↪mode='lines', name='Income(Ingreso)')) fig.add\_trace(ply.Scatter(x=[data\_bike\_clean.index[0], data\_bike\_clean.

↪index[-1]], y=[promedio\_income, promedio\_income],

mode='lines', name='Promedio Income'))

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Promedio de Income (Ingreso)</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis\_title='ID',

yaxis\_title='Income') fig![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.061.png).show()

Como podemos observar en la grafica lineal , el promedio de los ingresos de los clientes es de 56267.605634 dolares y esta representada en la grafica con una linea horizontal de color rojo.

\##### 2. ¿Cuánto es el promedio de ingresos según el estado civil del cliente?

[ ]: promedio\_ingresos = data\_bike\_clean.groupby('Marital Status')['Income'].mean().![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.062.png)

↪reset\_index()

fig = ply.Figure(data=[ ply.Bar(x=promedio\_ingresos[promedio\_ingresos['Marital Status'] ==␣ ↪'Married']['Marital Status'],

y=promedio\_ingresos[promedio\_ingresos['Marital Status'] ==␣ ↪'Married']['Income'],

name='Casado',

marker=dict(color='blue')),

ply.Bar(x=promedio\_ingresos[promedio\_ingresos['Marital Status'] ==␣ ↪'Single']['Marital Status'],

y=promedio\_ingresos[promedio\_ingresos['Marital Status'] ==␣ ↪'Single']['Income'],

name='Soltero',

marker=dict(color='green'))

])

fig.update\_layout(title='Promedio de Ingresos según Estado Civil',

xaxis\_title='Estado Civil', yaxis\_title='Promedio de Ingresos', barmode='group',

showlegend=**True**)

fig.show()

3. **Crear una nueva variable llamado Con\_hijos** Dónde Si: Children > 0, No: Children=0, para los clientes que si tienen hijos ¿Cuánto es el promedio de hijos según el nivel educativo del cliente?

[ ]: data\_bike\_clean["Con\_hijos"] = data\_bike\_clean["Children"].apply(**lambda** x: **True**␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.063.png)

↪**if** x > 0 **else False**)

data\_bike\_clean['Con\_hijos'] = data\_bike\_clean['Con\_hijos'].astype(str) promedio\_hijos = data\_bike\_clean.groupby('Education')['Con\_hijos'].

↪value\_counts(normalize=**True**).mul(100).reset\_index(name='Percentage')

colors = ['#FF8C00', '#008000']

fig = ply.Figure() fig.add\_trace(ply.Bar(x=promedio\_hijos[promedio\_hijos['Con\_hijos'] ==␣

↪'True']['Education'],

y=promedio\_hijos[promedio\_hijos['Con\_hijos'] ==␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.064.png)

↪'True']['Percentage'],

name='Con hijos',

marker=dict(color=colors[0]))) fig.add\_trace(ply.Bar(x=promedio\_hijos[promedio\_hijos['Con\_hijos'] ==␣ ↪'False']['Education'],

y=promedio\_hijos[promedio\_hijos['Con\_hijos'] ==␣ ↪'False']['Percentage'],

name='Sin hijos',

marker=dict(color=colors[1]))) fig.update\_layout(title='Promedio de Hijos según Nivel Educativo', xaxis\_title='Nivel Educativo',

yaxis\_title='Porcentaje de Clientes', legend\_title='Estado de hijos')

fig.show()

4. **Crear una nueva variable llamado Con\_vehiculo** Dónde Si: Cars>0, No: Cars=0, para los clientes que si tienen vehículo ¿Cuánto es el promedio de vehículos según la ocupación del cliente?

Primero creamos una nueva columna llamada “Con\_vehiculo” y la condicional

[ ]: data\_bike\_clean['Con\_vehiculo'] = data\_bike\_clean['Cars'].apply(**lambda** x: 'Si'␣![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.065.png)

↪**if** x > 0 **else** 'No')

Luego mostramos los clientes que tienen vehiculos de acuerdo con su ocupacion

[ ]: fig1 = ply.Figure(data=[![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.066.png)

ply.Bar(

name='Con vehículo',

x=data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] ==␣ ↪'Si']['Occupation'].value\_counts().index,

y=data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] ==␣ ↪'Si']['Occupation'].value\_counts().values

),

ply.Bar(

name='Sin vehículo',

x=data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] ==␣ ↪'No']['Occupation'].value\_counts().index,

y=data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] ==␣ ↪'No']['Occupation'].value\_counts().values

)

])

[ ]: fig1.update\_layout(![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.067.png)

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.020.png)

- black;">Cantidad de Clientes con y sin Vehículo por Ocupación</span></b>', 'x': 0.5,

'y': 0.95,

},

xaxis=dict(title='Ocupación'),

yaxis=dict(title='Cantidad de Clientes'),

barmode='stack'

)

fig1.show()

Luego procedemos a sacar el promedio de vehiculos a las personas que si tienen vehiculos de acuerdo a su tipo de ocupacion.

[ ]: promedio\_vehiculos = data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] == 'Si'].![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.068.png)

↪groupby('Occupation')['Cars'].mean().reset\_index(name='Prom Cars')

datos\_clientes\_vehiculo = data\_bike\_clean[data\_bike\_clean['Con\_vehiculo'] ==␣

↪'Si'].groupby('Occupation').size().reset\_index(name='Cantidad')

- *Unir los datos de promedio de vehículos y cantidad de clientes con vehículo*␣ ↪*por ocupación*

tabla\_final = promedio\_vehiculos.merge(datos\_clientes\_vehiculo, on='Occupation') pd.DataFrame(tabla\_final)

[ ]: Occupation Prom Cars Cantidad

0 Clerical 1.480000 100 1 Management 2.345912 159 2 Manual 1.441860 86

3  Professional 2.126126 222
3  Skilled Manual 1.712821 195

Para visualizar mejor los datos mostrados en la tabla mostraremos en una grafica de burbujas [ ]: **import plotly.graph\_objects as ply![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.069.png)**

- *Crear el gráfico de burbujas*

fig = ply.Figure(data=ply.Scatter(

x=tabla\_final['Occupation'],

y=tabla\_final['Cantidad'],

mode='markers',

marker=dict(

size=tabla\_final['Cantidad'],

sizemode='diameter',

sizeref=2, *# Ajustar este valor para reducir el tamaño de las burbujas* sizemin=1,

color=tabla\_final['Cantidad'],

colorscale='Viridis',

showscale=**True![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.070.png)**

),

text=["Promedio de Vehículos: **{:.2f}**<br>Cantidad de Clientes: **{}**". ↪format(promedio, cantidad) **for** promedio, cantidad **in** zip(tabla\_final['Prom␣ ↪Cars'], tabla\_final['Cantidad'])],

hoverinfo='text'

))

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Promedio de Vehículos por Tipo de Ocupación</span></b>',

'x': 0.5,

'y': 0.95,

},

xaxis=dict(title='Tipo de Ocupación'), yaxis=dict(title='Cantidad de Clientes con Vehículo')

)

- *Mostrar el gráfico* fig.show()
5. **¿Cuánto es el promedio de edad de acuerdo con si el cliente es o no propietario de una vivienda?![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.071.png)**

[ ]: promedio\_edad\_propietarios = data\_bike\_clean[data\_bike\_clean['Home Owner'] ==␣

↪1]['Age'].mean()

promedio\_edad\_no\_propietarios = data\_bike\_clean[data\_bike\_clean['Home Owner']␣

↪== 0]['Age'].mean()

print("Promedio de Edad para Propietarios de Vivienda:",␣

↪promedio\_edad\_propietarios)

print("Promedio de Edad para No Propietarios de Vivienda:",␣

↪promedio\_edad\_no\_propietarios)

Promedio de Edad para Propietarios de Vivienda: 45.024781341107875 Promedio de Edad para No Propietarios de Vivienda: 42.30891719745223

Para poder entender mas estos datos , pasaremos a mostrarlos en graficos donde primero veremos un grafico de Pie Charts donde veremos la cantidad de clientes si/no tienen vivienda

[ ]: *# Obtener la cantidad de clientes propietarios y no propietarios de vivienda![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.072.png)*

propietarios = data\_bike\_clean[data\_bike\_clean['Home Owner'] == 1].shape[0] no\_propietarios = data\_bike\_clean[data\_bike\_clean['Home Owner'] == 0].shape[0]

- *Crear el gráfico de pastel*

labels = ['Propietarios', 'No Propietarios']

sizes = [propietarios, no\_propietarios] colors![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.073.png) = ['lightblue', 'lightgreen']

fig = ply.Figure(data=[ply.Pie(labels=labels, values=sizes, textinfo='value',␣

↪marker=dict(colors=colors))])

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Distribución de Clientes Propietarios y <br> No Propietarios de␣ ↪Vivienda</span></b>',

'x': 0.5,

'y': 0.95,

},

width=600,

height=400

)

- *Mostrar los valores numéricos en el gráfico* fig.update\_traces(textposition='inside', textfont=dict(color='white'))

fig.show()

Luego otra grafica de Box Plots donde observaremos el promedio de edades de las personas que si/no tienen viviendas

[ ]: promedio\_edad = data\_bike\_clean.groupby('Home Owner')['Age'].mean()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.074.png)

fig = ply.Figure()

**for** propiedad, edad **in** promedio\_edad.items(): fig.add\_trace(ply.Box(y=data\_bike\_clean[data\_bike\_clean['Home Owner'] ==␣

↪propiedad]['Age'],

name=f'**{**propiedad**}** (Promedio de Edad: **{**edad**:**.2f**}**)')) *#*␣ ↪*0: Sin propiedad 1: Con propiedad*

- *Configurar el diseño del boxplot*

fig.update\_layout(

title={

'text': '<b><span style="font-family: Little Pat; font-size: 20px;color:

- black;">Promedio de Edad según Propiedad de la Vivienda</span></b>',

'x': 0.5,

'y': 0.95,

},

yaxis=dict(title='Edad'),

showlegend=**False**

)

- *Mostrar el boxplot ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.075.png)*fig.show()

**¿Que variable se correlaciona con otra?![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.056.png)**

[ ]: **import math**

**import seaborn as sns**

[ ]: corelation = data\_bike\_clean.corr()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.076.png)

corelation

<ipython-input-262-006389c694f4>:1: FutureWarning:

The default value of numeric\_only in DataFrame.corr is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric\_only to silence this warning.

[ ]: Gender Income Children Home Owner Cars Age \

Gender 1.000000 -0.050775 0.009290 -0.001957 -0.063651 -0.001611 Income -0.050775 1.000000 0.258856 0.014271 0.433564 0.170326 Children 0.009290 0.258856 1.000000 0.158384 0.275364 0.525683

Home Owner -0.001957 0.014271 0.158384 1.000000 -0.075976 0.111436

Cars -0.063651 0.433564 0.275364 -0.075976 1.000000 0.184295 Age -0.001611 0.170326 0.525683 0.111436 0.184295 1.000000 Purchased Bike 0.015179 0.047483 -0.121342 -0.017103 -0.198774 -0.106472

Purchased Bike Gender 0.015179 Income 0.047483 Children -0.121342 Home Owner -0.017103 Cars -0.198774 Age -0.106472 Purchased Bike 1.000000

[ ]: covariance=data\_bike\_clean.cov()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.077.png)

covariance

<ipython-input-263-2f3b26b46af5>:1: FutureWarning:

The default value of numeric\_only in DataFrame.cov is deprecated. In a future version, it will default to False. Select only valid columns or specify the value of numeric\_only to silence this warning.

[ ]: Gender Income Children Home Owner \

Gender 0.250129 -7.865966e+02 0.007529 -0.000454 Income -786.596597 9.594954e+08 12992.802803 205.265265 Children 0.007529 1.299280e+04 2.625705 0.119173 Home Owner -0.000454 2.052653e+02 0.119173 0.215620 Cars -0.035575 1.500822e+04 0.498638 -0.039425

Age -0.009117 5.970783e+04 9.639948 0.585594 Purchased Bike 0.003795 7.352452e+02 -0.098289 -0.003970

Cars Age Purchased Bike Gender -0.035575 -0.009117 0.003795 Income 15008.218218 59707.827828 735.245245 Children 0.498638 9.639948 -0.098289 Home Owner -0.039425 0.585594 -0.003970 Cars 1.248848 2.330759 -0.111042 Age 2.330759 128.072488 -0.602334 Purchased Bike -0.111042 -0.602334 0.249889

[ ]: sns.heatmap(corelation, xticklabels=corelation.columns,![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.078.png)

yticklabels=corelation.columns, annot=**True**, cmap=sns.color\_palette( as\_cmap=**True**))

[ ]: <Axes: >

![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.079.png)

observando la grafica podemos decir que la correlación entre hijos y edad es máxima. En segundo lugar coche e ingresos.

**¿Existe alguna relación entre el género y la bicicleta comprada? ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.080.png)**[ ]: correlacion = pd.crosstab(data\_bike\_clean['Purchased Bike'],␣

↪data\_bike\_clean['Gender'], margins=**True**)

correlacion

[ ]: Gender 0 1 All

Purchased Bike

0 269 250 519

1 242 239 481

All 511 489 1000

4. **3.4 Modelado**
4. **Escoger la técnica de modelado**

Para este trabajo escojeremos el entrenamiento de un modelo de regresión lineal Primero necesitare- mos dividir nuestros datos en una matriz X que contenga las características para entrenar, y una matriz y con la variable de destino, en este caso la columna Precio. No consideramos la columna Dirección porque solo tiene información de texto que el modelo de regresión lineal no puede usar.

Con este modelo comprobaremos si existe una relación entre las variables de entradas y la de salida, luego, intentaremos predecir el valor de la variable de salida en función de nuestra variable de entrada.

Matrices X e y Intentaremos explicar el comportamiento de una variable a partir de los datos de otras variables.

Para este modelado consideramo que la variable ID es irrelevante ya que podemos encontrar los datos segun el numero de fila

[ ]: data\_bike\_clean.drop('ID', inplace=**True**, axis=1) ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.081.png)[ ]: o=[]![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.082.png)

**for** i **in** data\_bike\_clean.columns:

**if** data\_bike\_clean[i].dtype=='object':

o.append(i)

Xenc=pd.get\_dummies(data\_bike\_clean,columns=o)

[ ]: Xenc.head()![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.083.png)

[ ]: Gender Income Children Home Owner Cars Age Purchased Bike \

0 1 40000.0 1 1 0 42 0 1 0 30000.0 3 1 1 43 0 2 0 80000.0 5 0 2 60 0 3 0 70000.0 0 1 1 41 1 4 0 30000.0 0 0 0 36 1

Marital Status\_Married Marital Status\_Single Education\_Bachelors … \                0 1 0 1 … 1 1 0 0 … 2 1 0 0 … 3 0 1 1 … 4 0 1 1 …

Occupation\_Professional Occupation\_Skilled Manual \         0 0 1 1 0 0 2 1 0 3 1 0 4 0 0

Commute Distance\_0-1 Miles Commute Distance\_1-2 Miles \

0 1 0 1 1 0 2 0 0 3 0 0 4 1 0

Commute Distance\_10+ Miles Commute Distance\_2-5 Miles \

0 0 0 1 0 0 2 0 1 3 0 0 4 0 0

Commute Distance\_5-10 Miles Region\_Europe Region\_North America \

0 0 1 0 1 0 1 0 2 0 1 0 3 1 0 0 4 0 1 0

Region\_Pacific

0 0 1 0 2 0 3 1 4 0

[5 rows x 27 columns]

A la variable objeto de estudio se la denomina variable de salida o de respuesta: y Purchased Bike

A las variables que nos ayudarán en el estudio se las llama variables de entrada, explicativas o predictoras: X

[ ]: X = Xenc.drop("Purchased Bike", axis=1)![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.084.png)

y = Xenc[["Purchased Bike"]]

Obtener conjunto de datos de Entrenamiento (Train) y de Prueba (Test)

Ahora dividimos los datos en un conjunto de entrenamiento y un conjunto de prueba. Entrenaremos el modelo en el conjunto de entrenamiento y luego usaremos el conjunto de prueba para evaluar el modelo.

6. **Generar el plan de prueba**

[ ]: **from sklearn.model\_selection import** train\_test\_split![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.085.png)

**from sklearn.linear\_model import** LogisticRegression **from sklearn.metrics import** classification\_report

- *División de los datos en entrenamiento y prueba*

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.2,␣

↪random\_state=42)

- *Entrenamiento del modelo de regresión logística* model = LogisticRegression()

model.fit(X\_train, y\_train)

- *Evaluación del modelo*

y\_pred = model.predict(X\_test) print(classification\_report(y\_test, y\_pred))

precision recall f1-score support

38

0 1

accuracy macro avg

weighted avg

0.58 0.61

0\.53 0.49

0\.55 0.55

0\.55 0.56

0.59 106

0\.51 94

0\.56 200

0\.55 200

0\.55 200



/usr/local/lib/python3.10/dist-packages/sklearn/utils/validation.py:1143: DataConversionWarning:

A column-vector y was passed when a 1d array was expected. Please change the shape of y to (n\_samples, ), for example using ravel().

7. **Construir el modelo**

[ ]: *# Generación del scoring de venta para nuevos clientes![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.086.png)*

new\_data = pd.DataFrame({

'ID': [11147, 54321],

'Marital Status': ['Married', 'Single'],

'Gender': ['Female', 'Male'],

'Income': [50000, 20000],

'Children': [2, 0],

'Education': ['Partial College', 'High School'], 'Occupation': ['Skilled Manual', 'Unemployed'], 'Home Owner': ['No', 'Yes'],

'Cars': [1, 0],

'Commute Distance': ['0-1 Miles', '1-2 Miles'], ![](Aspose.Words.cf614454-d33e-4167-a074-1031129d4d09.087.png)'Region': ['Europe', 'Pacific'],

'Age': [35, 28]

})

new\_data\_encoded = pd.get\_dummies(new\_data, columns=['Marital Status',␣

↪'Gender', 'Education', 'Occupation', 'Home Owner', 'Commute Distance',␣ ↪'Region'])

new\_X = new\_data\_encoded.reindex(columns=X.columns, fill\_value=0)

scores = model.predict\_proba(new\_X)[:, 1]

print("Scoring de venta:")

**for** i **in** range(len(new\_data)):

print(f"ID: **{**new\_data['ID'].iloc[i]**}**, Scoring: **{**scores[i]**}**")

Scoring de venta:

ID: 11147, Scoring: 0.4938523721733299 ID: 54321, Scoring: 0.631335082782635

**1.4 4. Conclusion**

Con lo que hemos visto de las gráficas tenemos estás conclusiones: 1. El pormedio de ingresos en general rondan cerca de los 60 000 $. Siendo los casados, los que tienen mayor ingresos 2. Casi todos los clientes sin importar su nivel educativo, tienen hijos 3. La mayoría de los clientes que poseen vehículo son profesionales 4. El 100% de los clientes son propietarios de una vivienda 5. El promedio de edad de las personas sin vivienda es de 42 años, mientras que las que si tienen son de 45 6. La correlación entre hijos y edad es máxima. En segundo lugar coche e ingresos.

Enlace al git :https://github.com/AbigailBG153/FDS-2023-1-CC52.git
39
