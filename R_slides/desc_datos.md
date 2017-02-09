name: inverse
layout: true
class: center, middle, inverse
---
name: Inicio
#Curso de R y estadística básica
[Felipe de J. Muñoz González]

[fmunoz@lcg.unam.mx](mailto:fmunoz@lcg.unam.mx)
.footnote[Descripción de Datos<br>[Descargar Presentación](https://github.com/gnab/remark)]
---
## Descripción de Datos en Estadística
---

layout: false
.left-column[
  ## ¿Tipos de Datos?
]
.right-column[
<br><br><br><br>
**_datum_** se refiere a la información concreta, cualquier pieza de información colectada.

Un **"Data set"** o set de datos es una colección de datos relacionadas de alguna forma.

Se definen 5 tipos de datos:

 - Cuantitativos

 - Cualitativos

 - Logicos

 - Faltantes

 - Otros tipos

]
---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ###  - Datos cuantitativos
]
.right-column[
<br><br><br><br><br><br>
Son datos que se pueden medir o son asociados a alguna cantidad. 

Se subdividen en:

 - Datos discretos

 - Datos continuos (datos escalares o de intervalos)
<br><br><br><br>

**Nota** Cuando no se sabe que tipo de dato es, considerese continuo

]

---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos (Ejemplo)
]
.right-column[
<br><br><br><br><br><br>
Ejemplo Precipitaciones anuales en ciudades de EE.UU. El vector contiene la cantidad promedio de lluvia (en pulgadas) para cada una de las 70 ciudades de los Estados Unidos.

```
> str(precip)
```
<br><br>
```
> precip[1:4]
```

**Ejercicio**

Describir los datos dentro de los dataset "rivers" y "discoveries"

]


---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Gráficas de puntos
]
.right-column[
<br><br><br><br>

Una de las cosas básicas que debe de manejarse cuando se describen los datos son gráficas que nos permitan tener mas información.


 1. Graficas de puntos (Strip charts). Existen 3 metodos:
   - overplot
   - jitter
   - stack

```
> stripchart(precip, xlab = "rainfall") 
```
<br>
```
> stripchart(rivers, method = "jitter", xlab = "length")
```
<br>
```
> stripchart(discoveries, method = "stack", xlab = "number")
```

]


---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Histogramas
]
.right-column[
<br><br><br><br>


 1. Histogramas (Bar Graphs)

Normalmente se usan para datos continuos y se requiere decidir un conjunto de clases o compartimientos que dividen la linea real en un conjunto de cajas a los cuales caen los valores.

```
> hist(precip, main = "Histograma de lluvias en U.S.A")
```
<br>
```
> hist(precip, freq = FALSE, main = "") #Frecuencias Relativas
```

<br>
<br>
Consideraciones:
 - La gráfica depende de los "bins" elegidos
 
]

---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Histogramas
]
.right-column[
<br><br><br><br>

**Ejercicios**

 - Genera dos histogramas de los datos de precipitación, el primero con 10 divisiónes y el segundo con 200
]

---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Ejercicios
]
.right-column[
<br><br><br><br>

**Ejercicios**

 - Genera dos histogramas de los datos de precipitación, el primero con 10 divisiónes y el segundo con 200



```
> hist(precip, breaks = 10, main = "")
```
<br>
```
> hist(precip, breaks = 200, main = "")
```


]

---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Gráficas de tallo
]
.right-column[
<br><br><br><br>

**Definición**

Las Gráficas de tallo tienen dos partes básicas: tallos y hojas.
El último dígito de los valores de datos se toma como una hoja y el (los) dígito (s) principal (es) se toma (n) como
tallos.


**Ejemplo**
UKDriverDeaths serie de datos en el tiempo que contiene las muertes en accidentes automovilisticos o con lesiones fuertes en Reino Unido de Enero de 1969 a Diciembre de 1984. ?UKDriverDeaths.

```
> install.packages("aplpack")

> library(aplpack)

> stem.leaf(UKDriverDeaths, depth = FALSE)

```


]


---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cuantitativos 
   ### - Gráficas de Índice
]
.right-column[
<br><br><br><br>

Estas se realizan utilizando la función **plot** y son buenas para visualizar datos que han sido ordenados, cuando los datos fueron medidos a traves del tiempo.

Es una gráfica de dos dimensiones que tiene una variable índice (x) y una variable medida (y). 

Existen los siguientes métodos:

 - picos (spikes).  code: (type = "h")

 - puntos (points) code: (type = "p"=)



**Ejemplo**
Mediciones anuales (En pies) del lago Huron de 1875-1972. Los datos son en el tiempo. ?LakeHuron


```
> plot(LakeHuron, type = "h")

```
<br>



```
> plot(LakeHuron, type = "p")

```



]


---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
]
.right-column[
<br><br><br><br>
Datos **no numericos** o que no representan cantidades numericas.

Ej. Nombre, genero, grupo etnico, estado socioeconomico, numero de seguridad social, licencia, ...

Algunos datos parecen ser cuantitativos pero no lo son por que no representan cantidades numericas medibles ni conservan reglas matemáticas.

Ej. Tamaño del pie de una persona (si sumas el tamaño del pie de dos personas no tiene sentido)

La información cuantitativa que se puede utilizar para subdividir información en diversas categorias se le llama **factor** 

]

---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Presentación de Datos
]
.right-column[
<br><br><br><br>

**Tablas** 
Una forma de mostrar resumenes de datos estadisticos es con el uso de las tablas. 


```
> str(state.abb)
```

Frecuencias absolutas

```
> Tbl <- table(state.division)
> Tbl
```

Frecuencias Relativas

```
> Tbl/sum(Tbl)
```

```
> Tbl/sum(Tbl)
```

]


---

layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Descripción
]
.right-column[
<br><br>


Los datos de state.region enumera cada uno de los 50 estados y la región a la que pertenece, ya sea en el noreste, sur, norte central u oeste.

```
> str(state.region)
```

```
> state.region[1:5]
```

```
> str(state.abb)
```

Frecuencias absolutas

```
> Tbl <- table(state.division)
> Tbl
```

Frecuencias Relativas

```
> Tbl/sum(Tbl)
```

```
> prop.table(Tbl) # same thing
```

]

---


layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Gráficas de Barras
]
.right-column[
<br><br><br><br>


Un gráfico de barras es el análogo de un histograma para datos categóricos. Se muestra una barra
Para cada nivel de un factor, con las alturas de las barras proporcionales a las frecuencias de observaciones
Pertenecientes a las respectivas categorías. Una desventaja de los gráficos de barras es que los niveles están ordenados alfabéticamente (por defecto), lo que a veces puede oscurecer los patrones en la pantalla.

```
> barplot(table(state.region), cex.names = 0.5)
```

```
> barplot(prop.table(table(state.region)), cex.names = 0.5)
```

]



---


layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Diagramas de Pareto
]
.right-column[
<br><br><br><br>


Un diagrama pareto es muy parecido a un gráfico de barras excepto que las barras se reordenan de tal manera que disminuyen en altura, pasando de izquierda a derecha. La reorganización es útil porque puede revelar visualmente la estructura (si es que hay) en la velocidad de las barras disminuyen - esto es mucho más difícil cuando las barras se mezclan.

```
> library(qcc)
```

```
> pareto.chart(table(state.division), ylab = "Frequency")
```

]


---


layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Gráfica de puntos
]
.right-column[
<br><br><br><br>


Estos se parecen mucho a un gráfico de barras que se ha girado en su lado con las barras reemplazadas por puntos en líneas horizontales. No transmiten más (o menos) información que el gráfico de barras asociado, pero la fuerza reside en la economía de la pantalla. Los gráficos de puntos son tan compactos que es fácil graficar interacciones multi-variables muy complicadas en un gráfico.

```
x <- table(state.region)
```

```
> dotchart(as.vector(x), labels = names(x))
```

]



---


layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Gráfica de pastel
]
.right-column[
<br><br><br><br>


These can be done with R and the R Commander, but they fallen out of favor in recent years because researchers have determined that while the human eye is good at judging linear measures, it is notoriously bad at judging relative areas.

```
> slices <- c(10, 12,4, 16, 8)
> lbls <- c("US", "UK", "Australia", "Germany", "France")

```

```
> pie(slices, labels = lbls, main="Pie Chart of Countries"
```
]

---


layout: false
.left-column[
  ## ¿Tipos de Datos?
   ### - Datos cualitativos
   ### - Gráfica de pastel
]
.right-column[
<br><br><br><br>


These can be done with R and the R Commander, but they fallen out of favor in recent years because researchers have determined that while the human eye is good at judging linear measures, it is notoriously bad at judging relative areas.

```
> slices <- c(10, 12,4, 16, 8)
> lbls <- c("US", "UK", "Australia", "Germany", "France")

```

```
> pie(slices, labels = lbls, main="Pie Chart of Countries"
```
]


---


layout: false
.left-column[
  ## Distribuciones de datos
]
.right-column[
<br><br><br><br>

**Centroide:** Conjunto de datos está asociado con un número que representa una tendencia media o general de los datos.

La **Dispersión** de un conjunto de datos está asociada con su variabilidad; Los conjuntos de datos con una dispersión grande tienden a cubrir un gran intervalo de valores, mientras que los conjuntos de datos con dispersión pequeña tienden a agruparse fuertemente alrededor de un valor central.

**Forma:** Forma exhibida por una pantalla gráfica asociada. La forma puede decirnos mucho sobre cualquier estructura subyacente a los datos, y puede ayudarnos a decidir qué procedimiento estadístico debemos usar para analizar los.

]

---
layout: false
.left-column[
  ## Distribuciones de datos
  ### Forma
]
.right-column[
<br><br><br><br><br>


**Simetría** y **asimetría** 
   - **positivamente sesgada**
   - **negativamente sesgada**


La **curtosis** (o apuntamiento) es una medida de forma que mide cuán escarpada o achatada está una curva o distribución. 


]


---
layout: false
.left-column[
  ## Observaciones Extremas
]
.right-column[
<br><br><br><br>

Problemas que pueden implicar estimaciones exageradas e "inestabilidad" estadística. Podemos considerar que estos datos pueden ser:

 - Error tipográfico (typoo)

 - Observaciónes que no eran para el estudio. (Ej. Complicaciones medicas)

 - Indican un fenomeno o una tendencia más profunda

]

---

layout: false
.left-column[
  ## Estadistica descriptiva 
  ### Rangos intercuantiles y MAD
]
.right-column[
<br><br><br><br>

suceptibilidad de la media, mediana a valores extremos.

Rango intercuartil (**IQR**) definido por IQR = q_{0.75} - q_{0.25}

Otro método más robusto que el IQR es la Media de la desviación absoluta (**MAD**).

1. Calculamos la media (prom) 
 
2. mediana(|x{i} - prom(X)|) , para toda i

]

---

layout: false
.left-column[
  ## Estadistica descriptiva 
]
.right-column[
<br><br><br><br>

Utilizando R. Calcula las siguientes cosas del vector 

```
x<-round(runif(20, min=1, max=100))

```
- rango
- media
- mediana
- quantiles/quintiles/septiles
- varianza
- desviación estandar


**Nota Rcmdr**

Statistics > Summaries > Numerical Summaries

calculamos los cuantiles automaticamente

]

---


layout: false
.left-column[
  ## Estadistica descriptiva 
   ### Medidas de Forma
]
.right-column[
<br><br><br><br>


La **asimetría** (Fisher) de la muestra, se define por la fórmula

<img src="http://www.universoformulas.com/imagenes/formulas/estadistica/descriptiva/coeficiente-asimetria-fisher.jpg" width=400px>

donde S es la desviación estandar (o tipica)

<img src="http://www.universoformulas.com/imagenes/estadistica/descriptiva/coeficiente-asimetria-fisher.jpg" width=400px>

]
---


layout: false
.left-column[
  ## Estadistica descriptiva 
   ### Medidas de Forma
]
.right-column[
<br><br><br><br>


La **curtosis**  de la muestra, se define por la fórmula

<img src="http://www.universoformulas.com/imagenes/formulas/estadistica/descriptiva/curtosis.jpg" width=400px>

donde S es la desviación estandar (o tipica)

<img src="http://www.universoformulas.com/imagenes/estadistica/descriptiva/curtosis.jpg" width=400px>

]
---


layout: false
.left-column[
  ## Estadistica descriptiva 
   ### Medidas de Forma
]
.right-column[
<br><br>

Asimetria
 
```
> library(e1071)
> skewness(discoveries)
```

```
> 2 * sqrt(6/length(discoveries))
```

**Nota** si 2 * sqrt(6/n) < skewness(x) => existe un sesgo dado el signo del calculo.


Curtosis
 
```
> kurtosis(UKDriverDeaths)
```

```
> 4 * sqrt(6/length(UKDriverDeaths))
```

**Nota** abs(4 * sqrt(6/n)) < kurtosis(x) => presenta curtosis



]

---


layout: false
.left-column[
  ## Estadistica descriptiva 
   ### Grafica de caja
]
.right-column[
<br><br>

Estas gráficas son buenas para visualizar mucha información descriptiva de nuestros datos al mismo tiempo:

**Centroide** (estimada por la mediana)

**Dispersión**

**Forma**

**Observaciones extremas**

**Outliers** Observaciones que pasan 1.5 veces el tamaño de la caja para cualquier extremo. 


Para observar los valores outliers

```
> boxplot.stats(rivers)$out #1.5 default
```
```
> boxplot.stats(rivers, coef = 3)$out #coef=3
```

```
> boxplot(rivers, horizontal=T)

```



]

---


layout: false
.left-column[
  ## Estadistica descriptiva 
   ### Z-value
]
.right-column[
<br><br>

Valor estandarizado, cuando queremos comparar datos en escala que es independiente a la medida.

Dado X=x[1], x[2], x[3], ... ,x[n] los z-scores son z[1], z[2],...z[n] se ven definidos como

z[i]=(x[i]-median(x))/s 

donde s es la sd()


```
> ?scale

```
]

---



name: last-page
template: inverse

## Datos Multivariados y DataFrames



---


layout: false
.left-column[
  ## Datos multivariados
   ### Introducción
]
.right-column[
<br><br>
 
Los estudios estadísticos requieren mas de un factor o medición asociado a cada objeto, para esto utilizamos otra **estructura de datos**.

Para esto existen dos tipos de estructuras en R:

 - Matrices
 - DataFrames

Ambas son estructuras arreglas en dos dimensiones en forma rectangular y estaremos considerando que (a menos que se indique lo contrario):

  - Las lineas son objetos
  - Las columnas contienen diferentes mediciones o factores

Ejemplo:

```
> x <- 5:8
> y <- letters[3:6]
> z <- 1:4*pi
> A <- data.frame(v1 = x, v2 = y, v3=z)
```
]

---



layout: false
.left-column[
  ## Datos multivariados
   ### Acceso a DataFrames
]
.right-column[
<br><br>

```
> A[3, ]
```

<br>
```
> A[1, ]
```

<br>
```
> A[, 2]
```
<br>

```
> names(A)
```
<br>
```
> A$v1
```

]


---



layout: false
.left-column[
  ## Datos multivariados
   ### Matrices
]
.right-column[
<br><br>

```
> A = matrix( 
+   c(2, 4, 3, 1, 5, 7), # the data elements 
+   nrow=2,              # number of rows 
+   ncol=3,              # number of columns 
+   byrow = TRUE)        # fill matrix by rows 
 
> A                      # print the matrix 

```

```
> dimnames(A) = list( 
+   c("row1", "row2"),         # row names 
+   c("col1", "col2", "col3")) # column names
``` 


```
> A[, 2] 
```

DataFrames vs Matrices:

Las **Matrices** son solamente arreglos numericos de dos dimensiones mientras que los **DataFrame** contienen diferentes tipos de valores


]

---


name: last-page
template: inverse

## Datos bivariados
---


name: last-page
template: inverse

## That's all folks (for now)!

Slideshow created using [remark](http://github.com/gnab/remark).