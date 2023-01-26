
### Definición de grafo

Un **grafo simple** consiste en un set finito y no vacio denominado V(G)
de elementos llamados **vertices o nodos** y, un set finito E(G) de
**aristas** que unen los pares no ordenados de V(G).

``` r
#Importar librerias
library(igraph)         # Biblioteca para análisis de redes.
```

    ## Warning: package 'igraph' was built under R version 4.2.2

    ## 
    ## Attaching package: 'igraph'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     decompose, spectrum

    ## The following object is masked from 'package:base':
    ## 
    ##     union

``` r
library(tidyverse)      # Colección de bibliotecas para manipulación de datos.
```

    ## Warning: package 'tidyverse' was built under R version 4.2.2

    ## ── Attaching packages
    ## ───────────────────────────────────────
    ## tidyverse 1.3.2 ──

    ## ✔ ggplot2 3.4.0      ✔ purrr   0.3.5 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.3      ✔ forcats 0.5.2

    ## Warning: package 'ggplot2' was built under R version 4.2.2

    ## Warning: package 'tibble' was built under R version 4.2.2

    ## Warning: package 'tidyr' was built under R version 4.2.2

    ## Warning: package 'readr' was built under R version 4.2.2

    ## Warning: package 'purrr' was built under R version 4.2.2

    ## Warning: package 'dplyr' was built under R version 4.2.2

    ## Warning: package 'stringr' was built under R version 4.2.2

    ## Warning: package 'forcats' was built under R version 4.2.2

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::as_data_frame() masks tibble::as_data_frame(), igraph::as_data_frame()
    ## ✖ purrr::compose()       masks igraph::compose()
    ## ✖ tidyr::crossing()      masks igraph::crossing()
    ## ✖ dplyr::filter()        masks stats::filter()
    ## ✖ dplyr::groups()        masks igraph::groups()
    ## ✖ dplyr::lag()           masks stats::lag()
    ## ✖ purrr::simplify()      masks igraph::simplify()

``` r
library(viridis)        # Biblioteca con paletas de colores.
```

    ## Warning: package 'viridis' was built under R version 4.2.2

    ## Loading required package: viridisLite

    ## Warning: package 'viridisLite' was built under R version 4.2.2

``` r
# Generamos una red aleatoria de 4 nodos no dirigida.
# Para poder reproducirla, dado que tiene componentes aleatorios,
# Fijamos la semilla del generador de números pseudoaleatorios.
set.seed(22051996)
g <- sample_gnp(4, 1, directed = FALSE, loops = FALSE)
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

Calcularemos el set de vertices **V(G)** y el set de aristas **V(E)**
del grafo generado arriba, el cual sería considerado un **grafo
simple**, en el cual por lo menos una arista esta uniendo un dado par de
vertices.

``` r
V(g) #Calcular nodos
```

    ## + 4/4 vertices, from bbfae05:
    ## [1] 1 2 3 4

``` r
E(g) #Calcular aristas 
```

    ## + 6/6 edges from bbfae05:
    ## [1] 1--2 1--3 1--4 2--3 2--4 3--4

A continuación se presentara un **grafo general** o simplemente un
**grafo**, dicho objeto permite la presencia de loops y aristas
multiples. Un **loop** es aquella arista que conecta un nodo con si
mismo. Las **aristas multiples** son aquellas aristas que conectan dos
vertices distintos más de una vez.

``` r
set.seed(22051996)
g <- sample_gnp(6, 1, directed = FALSE, loops = TRUE) #Crea un grafo aleatorio con 6 nodos, no dirigido y con loops
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
V(g) #Calcular nodos
```

    ## + 6/6 vertices, from bc0e780:
    ## [1] 1 2 3 4 5 6

``` r
E(g) #Calcular aristas
```

    ## + 21/21 edges from bc0e780:
    ##  [1] 1--1 1--2 1--3 1--4 1--5 1--6 2--2 2--3 2--4 2--5 2--6 3--3 3--4 3--5 3--6
    ## [16] 4--4 4--5 4--6 5--5 5--6 6--6

En el grafo creado todos los nodos tienen un loop,ninguna de las aristas
es multiple. \###Isomorfismo Se dice que entre dos grafos G1 y G2 cuyos
nodos no estan etiquetados existe isomorfía si al etiquetarlos cada una
de los nodos se corresponde a la perfección con el grafo de referencia.
Así el grafo recien creado es isomorfo con el anterior.

``` r
set.seed(22051998)
g <- sample_gnp(6, 1, directed = FALSE, loops = TRUE) #Crea un grafo aleatorio con 6 nodos, no dirigido y con loops
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
V(g) #Calcular nodos
```

    ## + 6/6 vertices, from bc1521f:
    ## [1] 1 2 3 4 5 6

``` r
E(g) #Calcular aristas
```

    ## + 21/21 edges from bc1521f:
    ##  [1] 1--1 1--2 1--3 1--4 1--5 1--6 2--2 2--3 2--4 2--5 2--6 3--3 3--4 3--5 3--6
    ## [16] 4--4 4--5 4--6 5--5 5--6 6--6

\###Conectividad Se dice que un grafo es **conectado** si no puede ser
expresado como la unión de dos grafos (G= G1 U G2) . Así, todo grafo que
pueda ser expresado de esa forma Es un grafo **desconectado**

``` r
set.seed(22051996)
g <- sample_gnp(6, 0.3, directed = FALSE, loops = FALSE) #Crea un grafo aleatorio con 6 nodos, no dirigido y con loops
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

En el grafo anterior ejemplificamos un grafo **desconectado** en el que
cada grupo de nodos que estan conectados entre sí, son **componentes**.
Con este mismo grafo podemos ejemplificar el concepto de

\###Proximidad Decimos que dos vertices llamense v y w de un Grafo G son
**incidentes** si hay una arista vw uniendolos.Así, en el ejemplo
arriba, la arista que une el nodo 4 es incidente con el 1 y, las aritas
que unen 1 y 6 son incidentes con el nodo 4. Del mismo modo en el
componente restante, las aristas que unen los vertices 5 y 3 son
incidentes del vertice 2. Por otro lado, se dice que las aristas que
comporten un nodo son **adyacentes**, así, la arista 5,2 es adyacente de
la arista 2,3. Mientras que en el otro componente la arista 1,4 es
adyacente de la arista 4,6.

Cuando hablamos del concepto de **grado** de un nodo v de G, este es el
número de aristas incidentes con v y se denota deg(v)

``` r
set.seed(22051996)
g <- sample_gnp(8, 0.3, directed = FALSE, loops = FALSE) #Crea un grafo aleatorio con 6 nodos, no dirigido y con loops
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
#Calculamos los grados de los nodos en g y ordenamos de mayor a menor.

degree(g) %>% sort(decreasing=TRUE)
```

    ## [1] 3 3 3 2 1 1 1 0

Los nodos 2, 4 y 7 tienen un valor de **grado del nodo** igual a 3; El
nodo 3 tiene un **deg(v)= 2**; el resto dentro de esa componente con más
nodos tiene un **deg(V)= 1**. El nodo restante en la otra componente
tiene **deg(v)= 0**. Aunque en este caso no existe ningún loop, cabe
mencionar que cuando existe un loop este por convención contribuye con 2
en lugar de 1 al valor del grado del nodo. Además a deg(v)= 0 se define
como un **nodo aislado** y deg(v)=1 se define como un **nodo terminal**

La **secuencia de grado** de un Grafo consiste en los grados escritos en
orden ascendente, con repeticiones cuando es necesario, como se muestra
a continuación:

``` r
degree(g) %>% sort(decreasing=FALSE)
```

    ## [1] 0 1 1 1 2 3 3 3

\###Subgraphs Un **Subgrafo** de un grafo G es a su vez un grafo, en el
cual cada uno de sus vertices pertenece a V(G) y cada uno de sus aristas
pertenecen a E(G). En el ejemplo siguiente crearemos un nuevo grafo e,
induciremos un subgrafo donde no se consideren los nodos 5 y 6.

``` r
set.seed(22051996)
g <- sample_gnp(6, 1, directed = FALSE, loops = TRUE) #Crea un grafo aleatorio con 6 nodos, no dirigido y con loops
plot(g,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
g2 <- induced_subgraph(g, 1:4) #Induce un subgrafo del grafo en g que no contenga al nodo 5 y 6
plot(g2,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-9-2.png)<!-- -->

Podemos notar que en el nuevo subgrafo donde no se consideraron los
nodos 5 y 6, también se descartan las aristas que unian estos nodos con
los demás. Podríamos denotar a este subgrafo como **G-S** donde S es un
set de vertices. **G-e** se refiere a un subgrafo donde no se considera
un vertice del grafo original, esto se ejemplifica a continuación:

``` r
g3 <- induced_subgraph(g, 1:5) #Induce un subgrafo del grafo en g que no contenga al nodo 6
plot(g3,
     vertex.color="darkorchid",  # color de los nodos
     vertex.size=20,             # tamaño de los nodos
     edge.color="black")         # color de las aristas
```

![](Introduccion-a-la-teoria-de-grafos_definiciones-y-ejemplos_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->
