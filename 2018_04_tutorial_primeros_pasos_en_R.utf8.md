# Tutorial: primeros pasos en R

Tutorial en construcción del Taller organizado por [RLadies Santiago](https://meetup.com/rladies-scl) y realizado por [Riva Quiroga](https://twitter.com/rivaquiroga)


## Instalación de R y RStudio

En este taller utilizaremos R a través del IDE RStudio. ¿Qué es un IDE? IDE es el acrónimo de *Integrated Development Environment*, es decir, un *Entorno de Desarrollo Integrado*. Esto quiere decir que RStudio es una aplicación que nos entrega herramientas para hacer más fácil el desarrollo de proyectos usando R.  

Para poder instalar R y RStudio, sigue los siguientes pasos:

- Descarga R desde https://cran.r-project.org/. Debes elegir la opción que corresponda según tu sistema operativo.
- Instala R en tu computador, tal como lo haces con cualquier programa. 
- Una vez que R ha quedado correctamente instalado, descarga RStudio desde https://www.rstudio.com/products/rstudio/download/. Elige la primera opción, es decir, "RStudio Desktop Open Source License" (gratuita). 
- Instala RStudio en tu computador, tal como lo haces con cualquier programa. 

Si quedó todo bien instalado, cuando abras RStudio deberías ver algo así:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio.png)

En este tutorial usaremos al última versión de R y RStudio, así que si tienes instalada una versión previa, puede que algunas cosas se vean un poco distintas.

Si te aparece algún error durante este proceso, lo más probabable es que sea por alguna configuración de tu sistema operativo. En ese caso, la mejor manera de buscar una solución es copiar el error que arroja R, pegarlo en tu motor de búsqueda favorito y ver cómo alguien que se enfrentó a eso antes lo resolvió. 

## Instalación de los paquetes de R que usaremos

Cuando instalamos R por primera vez en nuestro computador, lo que estamos instalando es lo que se conoce como "R Base", es decir, los elementos centrales del lenguaje de programación. Una de las ventajas de R es que se trata de un lenguaje extensible: la propia comunidad de usuarios puede desarrollar nuevas posibilidades para utilizarlo. La manera de compartir estos nuevos desarrollos es a través de "paquetes", que incluyen, entre otras cosas, código y datos.

En este taller usaremos tres paquetes: `gapminder`, `babynames` y `tidyverse`. `gapminder` y `babynames` son paquetes de datos que nos servirán para algunos de los ejercicios que realizaremos. `tidyverse`, por su parte, es un "megapaquete" que incluye otros paquetes en su interior. Todos los paquetes del Tidyverse comparten la misma visión sobre el trabajo con datos. Quizás ahora eso suene un poco enigmático, pero más adelante explicaremos qué quiere decir. 

Para instalarlos, 

1. copia el siguiente código:

```r
install.packages("tidyverse")
install.packages("gapminder")
install.packages("babynames")
```

2. pégalo en la consola (_Console_) de RStudio:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/install.packages.png)

3. presiona 'enter'. 
El último paquete es un poco más pesado que el resto, así que, dependiendo de tu conexión, podría tomar un minuto. El resultado se debería ver parecido a esto:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/paquetes_instalados.png)

Si no tienes la última versión de R, puede que aparezca un `Warning`al instalar alguno de los paquetes que diga que el paquete fue construido bajo la versión 3.4.4 y que tú tienes la 3.4.3. Un `Warning` es distinto a un error: R ejecuta el código pero te advierte que no todo puede resultar como esperas. 

## Utilización de RStudio

Como señalamos antes, RStudio es un entorno que facilita el trabajo con R. Si solo abres R en tu computador, lo que verás es una consola. En ella se escribe directamente el código que uno quiere ejecutar.

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/r_consola.png)

Si abres RStudio verás que te aparece la misma consola, pero además te encontrarás con otros paneles. Estos paneles nos ayudan a organizar nuestro trabajo y hacen todo el proceso más sencillo. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio.png)

El panel de abajo a la derecha tiene varias pestañas. 

Files muestra el directorio (la carpeta) en la que te encuentras actualmente. En mi caso, no hay nada ahí, porque por defecto me muestra el Escritorio (_Desktop_). Es posible que a ti te muestre otra carpeta (por ejemplo, _Documentos_). 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_files.png)

En la pestaña Plots tampoco hay nada por ahora. Cuando hagas algún gráfico, es es el lugar en el que aparecerán.

Packages muestra la lista de paquetes que tienes instalados. Lo que verás será di

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_packages.png)

Help, como su nombre lo indica, es la pestaña en la que podemos encontrar ayuda. Si ingresamos algún término (por ejemplo, el nombre de un paquete o de una función), RStudio nos remitirá a la documentación asociada. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_help.png)

El cuarto panel (que probablemente todavía no te aparece) es el que ocuparemos para escribir el código que queremos que luego R ejecute, es decir, el panel para nuestro _script_. Para crear un nuevo script podemos ir a File > New File > R Script, ocupar el atajo de teclado `shift(mayúscula)` + `comando` + `n` (Mac) o `shift(mayúscula)` + `control` + `n` o seleccionarlo desde la barra superior de la ventana:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/nuevo_script.png)

### Creación de un proyecto 

Una de las ventajas de RStudio es que permite crear "proyectos". [EXPLICAR VENTAJAS]

Para crear un proyecto, debes ir al menú File > New Proyect. 

<img src="https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_newproject1.png)" width="200">

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_newproject1.png)

Lo primero que nos pregunta es en qué carpeta de nuestro computador queremos que el proyecto viva. Elegiremos esta vez que viva en una carpeta nueva, así que seleccionaremos _New Directory_. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_newproject2.png)

La siguiente pregunta es qué tipo de proyecto queremos crear. En esta ocasión, elegiremos la primer _New Project_ (¡en futuros talleres ocuparemos las otras opciones!).

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_newproject3.png)

Finalmente, le damos un nombre al proyecto y decidimos en qué parte de nuestro computador queremos guardar la carpeta que lo contiene. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_newproject4.png)

Luego de apretar _Create Project_ RStudio se reinicia y se producen algunos cambios. El panel _Files_ (abajo a la derecha) ahora nos muestra la carpeta de nuestro projecto y el único archivo que hay en ella por ahora. Ese es el archivo mágico que mantiene unido todo lo que hay dentro de la carpeta. Cuando queramos volver a trabajar en nuestro projecto, solo tenemos que abrir ese archivo. 

![]() [IMAGEN FALTA]

También apareció un nuevo panel arriba a la izquierda: es el panel para escribir nuestro script, es decir, la serie de códigos que queremos ejecutar en R. 

![]() [IMAGEN carpeta FILES]

Otra cosa que ocurre es que en la barra superior aparece ahora la ruta a la carpeta de nuestro projecto. 

![]() [IMAGEN BARRA]

Por último, algo cambia en el ícono de R: aparece el nombre que le dimos a nuestro archivo:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/rstudio_icono.png)

Esto último es muy muy muy útil: RStudio se ejecuta para cada proyecto de manera independiente. Es decir, si tuvieras otro proyecto abierto te aparecería otro ícono. De esta forma, podemos trabajar en dos proyectos en paralelo sin que se nos mezclen los objetos del entorno, el código, los archivos, etc.

¡Ya estamos listas para empezar programar!

## Cargar los paquetes necesarios

Antes del taller instalaste los tres paquetes que ocuparemos en esta sesión. Cuando instalamos los paquetes, estos quedan en nuestro computador y podemos chequear eso revisando el panel "Packages" abajo a la izquierda. Sin embargo, que los hayamos instalado no quiere decir que estén listos para ser usados. Tenemos que decirle explícitamente a R qué paquetes queremos ocupar. ¿Por qué? Para ahorrar memoria: activamos solo los que necesitamos. 
La función para hacer eso es `library(nombre_del_paquete)`, así que escribiremos eso al inicio de nuestro script. RStudio trata de hacernos la vida más simple, así que cuando empezamos a escribir el nombre de la función se despliega un menú con posibles opciones que indican el nombre y el paquete al que está asociada (en este caso, sugiere `{base}`). Lo que aparece en amarillo es la estructura de la función, algo sobre lo que no hablaremos por ahora:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/sugerencia_funcion.png) 

Lo mismo ocurre cuando empezamos a escribir el nombre del paquete. RStudio nos va ofreciendo sugerencias de nombres de los paquetes que tenemos instalados- 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/sugerencia_argumento.png) 

Todavía no hemos 'ejecutado' el código, así que nada ha pasado. Como todo en R, hay varias opciones para ejecutar el código. 
Si hacemos clic en el botón Run que está en la barra del script, se ejecutará la línea de código en la que está actualmente el cursor y este se moverá automáticamente a la siguiente línea. Es decir, si ponemos el curso en la línea en la que llamamos por primera vez la función `library`y hacemos clic tres veces, se ejecutarán las tres líneas. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/ejecutar_codigo.png)

Eso mismo podemos hacerlo usando un atajo del teclado `ctrl` + `shift (mayúsculas)` + `enter` (si estás en Linux o Windows) o `comando` + `shift (mayúsculas)` + `enter` si estás en Mac. 

Cuando queremos ejecutar más de una línea de código, lo que podemos hacer es seleccionar todo el fragmento y hacer clic sobre Run o usar el atajo del teclado. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/seleccion_para_ejecutar_png.png)

¡Ejecutemos el código y veamos qué pasa!



Cuando ejecutamos código de nuestro script esté pasa a la consola. En el caso de la primera línea, la consola nos da dos avisos. El primero, cuáles son todos los paquetes que estamos activando al usar `library(tidyverse`). Como comentamos antes, este es un metapaquete que incluye otros paquetes en su interior. Al llamarlos a través de `library(tidyverse)` se activan estos 8 paquetes (pese a que incluye más) y eso es lo que nos está avisando R en la consola. El otro aviso es de un "Conflicto". Nos dice que las funciones `filter()`y `lag()` del paquete `dplyr` tienen el mismo nombre que funciones de paquete `stats`. Como cargamos `dplyr`después (el instalar `tidyverse`), lo que R nos avisa es que las de este paquete son las que van a prevalecer por sobre las del paquete `stats`(que es parte de R base). 

En este punto es importante sugerir dos buenas prácticas. La primera, es hacer lo que ya hicimos: llamar todos los paquetes que ocuparemos al inicio de nuestro script. De este modo, cuando volvemos a utilizarlo más adelante u otra persona quiere ejecutarlo puede tener claro qué paquetes se utilizan. Obviamente, cuando comienzo a escribir un script puedo no saber cuáles son todos los paquetes que necesitaré, pero si en la mitad decido usar un nuevo paquete, la idea sería volver a las primeras líneas del script y agregarlo. 

La segunda buena práctica es comentar nuestro script. En R podemos agregar comentarios anteponiendo un `#` al fragmento que cumple esa función. En una línea de nuestro script, todo lo que está después de un `#` no se ejecuta como código. 

¿Por qué es importante comentar nuestro script? Porque así podemos recordar qué es lo que un determinado fragmento de código hace o  dejar registro de por qué hicimos algo de determinada manera. Esto es muy útil para que nuestro futuro yo o las personas con las que compartiremos nuestro script entiendan lo que hicimos. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/comentarios.png)

También es útil agregar al inicio de nuestro script una descripción de lo que hace. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/comentario_inicio_script.png) 

Antes de seguir, es important que guardemos nuestro script. 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/guardar_script.png)

## Miremos los datos

`babynames` es un paquete que contiene datos sobre nombres registrados en Estados Unidos entre los años 1880 y 2015. El objeto que contiene los datos dentro del paquete se llama también `babynames`. No vemos ese objeto en nuestro `Gobal Environment` porque el objeto existe dentro del paquete, pero si fueramos a ver el entorno de ese paquete en particular, lo encontraríamos:

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/entorno_babynames.png)

En R, podemos ver un objeto simplemente ejecutándolo: 

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/objeto_babynames.png)

En este caso, el objeto `babynames` es una `tibble`, que es un tipo particular de conjunto de datos. No nos detendremos aún en los tipos de objetos que existen en R, lo importante por ahora es saber que R nos muestra en la consola las primeras diez filas para que nos hagamos una idea de lo que contiene y no los casi dos millones totales (mejor así, ¿no?)

Si quisiéramos tener una visión general de los datos, hay una función que resulta muy útil para esto, ya que nos los muestra en una pestaña distinta y con un formato tipo planilla:

``` r
View(babynames)
```

![](https://github.com/rivaquiroga/RLadies-Santiago/blob/master/images/babynames.png)
