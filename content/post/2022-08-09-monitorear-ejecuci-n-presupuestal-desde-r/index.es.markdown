---
title: Monitorear ejecución presupuestal desde R
author: Samuel Calderon
date: '2022-08-09'
slug: monitorear-ejecuci-n-presupuestal-desde-r
categories: []
tags:
  - r
  - Open source
subtitle: ''
summary: ''
authors: []
lastmod: '2022-08-09T17:15:42-05:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---




Este post marca el lanzamiento oficial de un nuevo paquete para R llamado `{perutranspaeconomica}`. El paquete cuenta con [sitio web oficial](https://perutranspaeconomica.samuelenrique.com/) y [repositorio en Github](https://github.com/calderonsamuel/perutranspaeconomica). Su objetivo es acceder a los datos de ejecución presupuestal de las unidades ejecutoras (entidades públicas) que operan en el país. 

El paquete es mejor aprovechable para las personas que estén familiarizadas con el [Portal de seguimiento a la ejecución de gasto presupuestal](https://apps5.mineco.gob.pe/transparencia/Navegador/default.aspx) del Ministerio de Economía y Finanzas. Hasta el momento, sirve para hacer consultas a partir del 2012. Con el paso del tiempo (y con algo de apoyo de la comunidad) puede ampliarse para abarcar años anteriores.

Como ejemplo, podemos ver cuánto se presupuesto y gastó en el año 2021 en todo el país. Comenzamos por cargar el paquete y la colección `tidyverse` para facilidad de tratamiento de los datos.


```r
library(perutranspaeconomica)
library(tidyverse)
```

Para hacer la consulta, podemos usar la función `gasto()`. Con esto obtenemos una tabla muy similar a la de la plataforma del MEF. Para apreciar mejor la información, la convierto en un objeto JSON.


```r
gasto(year = 2021) |> 
    jsonlite::toJSON(pretty = TRUE)
```

```
## [
##   {
##     "year": 2021,
##     "total": "TOTAL",
##     "pia": 183029770158,
##     "pim": 227932217930,
##     "certificacion": 212449395064,
##     "compromiso_anual": 205012945543,
##     "atencion_de_compromiso_mensual": 200846585155,
##     "devengado": 198917822202,
##     "girado": 198458518497,
##     "avance_percent": 87.3
##   }
## ]
```

Para ver una evolución en el tiempo, podemos usar una consulta iterativa. Así aprovechamos mejor las oportunidades del paquete.


```r
consulta <- 2012:2021 |> 
    map_dfr(~gasto(year = .x))

consulta
```

```
## # A tibble: 10 × 10
##     year total       pia     pim certificacion compromiso_anual atencion_de_com…
##    <int> <chr>     <dbl>   <dbl>         <dbl>            <dbl>            <dbl>
##  1  2012 TOTAL   9.55e10 1.22e11  104861748780     103676969380     103265692076
##  2  2013 TOTAL   1.08e11 1.34e11  117497648037     116299419400     116001333132
##  3  2014 TOTAL   1.19e11 1.45e11  131410018397     129777581135     129309328261
##  4  2015 TOTAL   1.31e11 1.53e11  138661851148     136447733062     135941953193
##  5  2016 TOTAL   1.38e11 1.58e11  144536534140     137792009934     137287507523
##  6  2017 TOTAL   1.42e11 1.76e11  161079975365     153594474517     151589903264
##  7  2018 TOTAL   1.57e11 1.88e11  173249001094     164833451778     160620562945
##  8  2019 TOTAL   1.68e11 1.89e11  174833598326     167350028122     162601350696
##  9  2020 TOTAL   1.77e11 2.17e11  199474122166     191603296844     185640104242
## 10  2021 TOTAL   1.83e11 2.28e11  212449395064     205012945543     200846585155
## # … with 3 more variables: devengado <dbl>, girado <dbl>, avance_percent <dbl>
```

Por último, podemos graficar los datos obtenidos. En este caso, para conocer la evolución en la ejecución presupuestal del Estado peruano desde el 2012 al 2021.


```r
consulta |> 
    ggplot(aes(year, avance_percent)) +
    geom_line() +
    geom_label(aes(label = avance_percent))
```

<img src="{{< blogdown/postref >}}index.es_files/figure-html/unnamed-chunk-4-1.png" width="672" />

Como se puede ver, la ejecución presupuestal ha sido superior al 80% en los últimos años, pero nunca alcanzó el 90% de lo presupuestado.

Sin usar el paquete habría sido necesario:

1. Navegar la plataforma año por año 
2. Para cada año, descargar un archivo excel con la información
3. Juntar todas las tablas en un solo archivo.
4. Procesar la información y generar el gráfico

¡El paquete permitió saltarse los tres primeros pasos! Una consulta más compleja hubiese requerido más tiempo repetido en los pasos 1 y 2. Este es un ejemplo simple para demostrar las posibilidades de usar la información que tenemos a la mano. 
