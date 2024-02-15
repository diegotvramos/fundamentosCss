

# _FUNDAMENTOS CSS_

[link](https://diegotvramos.github.io/fundamentosCss/)

## INTRODUCCION A CSS

CSS es un lenguaje de definicion de estilos, es la presentacion de los documentos html.
css no es un leguaje de programacion, pero tiene caracteristicas propias de lenguaje de programacion.
debemos empesar a despertar cierta logica para porder crear ciertos efectos visuales, llamado tambien arte digital atraves de css.

## SINTAXIS BASICA.

Una regla de CSS consta de 2 partes
1 _*selector*_- es el elemento html al que nosotros podemos aplicarle el bloque de declaracion de estilos, y un selector podria ser cualquier etiqueta html, ele selector mas basico son las etiquetas.
2 _*Bloque de declaraciones*_
    //Es cada uno de los atributos que vamos a modificar.

    ```css
        {
        atributo: valor.
        atributo-de-mas-dos-palabras: otro-valor
        }
    ```

## COMENTARIOS EN CSS.

/**/este seria un comentarios en css

## FORMAS DE INVOCACION.

Hay 3 formas de invocarlos.
* internamente dentrod el documento Html.
* en linea (en la propida etiqueta).
* mediante una hoja externa (que es lo ideal)
Es una mala practica importar en CSS son bloqueantes a la hora de que el navegador lee esta instruccion.
No es mala practica para preprocesadores como SAS

## Versiones, documentacion y enlaces de referencia

Html ya se está trabajando por modulos(animacion, maquetacion con la tecnica de flexbox, tema de maquetacion con grid), es decir cada implementacion. todo estos modulos van a ir avanzando en su momento.
 ahorita hablar de CSS4  vamos a hablar de que los diferentes modulos que tiene CSS van a ir evolucionando poco a poco
 CSS4 no va ser lanzado por que todo se actualiza por modulos

* https://www.w3.org/TR/css-2023/
* https://developer.mozilla.org/es/docs/Web/CSS (documentacion de primera mano)
* https://cssreference.io/
* https://caniuse.com/
* https://codeguide.co/  guia para buenas practicas (de ortografia para escribir buen codigo html y css) de github.

## Selectores basicos: Etiquetas, Identificadores y Clases

Selectores Basicos.
1. etiquetas - son elementos html
2. Identificadores - atributo id -#
3. Clases - atributo class- .

la escritura de codigo css es el guion medio (-) nomenclatura.
cuando aplicas estilos a etiquetas, le va aplicar estilos a todas las etiquetas.

Dar estilos con ID  se considera un AntiPatron(mala practica) por que el id es UNICO; por que css nos va permitir la reutilizacion del codigo de estilos, por eso es una mala practica definir estilos CSS con identificadores EVITALOS. tiene mas peso sobre otros estilos.

RECOMENDACION: maqueta y diseña todo tu codigo css con CLASSES en el codio html te permite agregar mas de una clase a un elemento.

`trata que tus nombres de clase sean alusivos a lo que hacen` uno de los  frameworks (tailwile) usa muchas clases para dar estilos.

## Selectores Avanzados.

### seletores de hijos

#### Selector de hijos directos

usa este codigo para emet: `ul>li*4>b`
```html
    <ul>
        <li><b></b></li>
        <li><b></b></li>
        <li><b></b></li>
        <li><b></b></li>
    </ul>
```

```css
    .hijos-directos >li {
    background-color: thistle;
    }
```
aplica los estilos a los elementos de primer nivel

#### Selector de hijos descendientes

con esto, solo se colorea el texto

```css
    .hijos-descendientes b {
    background-color: thistle;
}
```

### Selector de hermanos

#### Selector de hermanos (en general)

Aplicale el color de fondo a las li que sean hermanas por debajo.

```css
.hermanos-general ~ li{ 
    background-color: thistle;
}
```

#### Selector de hermanos (adyacente)

del elemento de referencia hacia abajo.

```css
    .hermanos-adyacentes + li{ 
    background-color: thistle;
}
```

### selectores de atributos

Podemos aplicar estilos css tomando referencia de cualquier atributo de cualquier etiqueta html
para escribir mas rapido usa el siguiente comando emet `ul>li*6>a[target="_blank"]`

```html
    <ul>
        <li><a href="" target="_blank">Inicio</a></li>
        <li><a href="" target="_blank">Cursos</a></li>
        <li><a href="" target="_blank">Blog</a></li>
        <li><a href="" target="_blank">Cv</a></li>
        <li><a href="" target="_blank">Ahora</a></li>
        <li><a href="" target="_blank">Notas</a></li>
    </ul>
```

El comodin del * aplica el estilo si contiene el texto encuestion en cuelquier parte.
```css
    .selectores-atributos a[href*="hola"]
    /*el comodin del circunflejo (^) aplica el estilo si contiene el texto en cuestion al inicio*/
    .selectores-atributos a[href^="http:"]
```

### Selector universal

Aplica los estilos a todos los elementos html que tengas dentro de tu documento, contextualmente es decir depende de donde nos encontremos

    ```css
        *{
            font-family: sans-serif;
        }
    ```

## Pseudoclases

Dan estilos dependiendo el contexto la posicion del elemento al que le queremos aplicar estilos o dependiendo de ciertos estados que tenga el elmento HTML

- _https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes_

```css
    /*como es una pseudoclase interactiva es mejor ponerla al final*/
        .menu-pseudoclases a:hover{
            color: orange;
        }
    /*cuando el elmento ID llamado "Temario" tenga el TARGET(tenga en la url el ID activo...)
    es el principio basico para hacer menús moviles  sein la necesidad de java script, de tal manera que cuando
    pulsamos un enlace activamos el menú y lo abrimos y cuando perdemos el target se cierra.
    */
    #temario-css:target{
        background-color: lightgreen;
    }
```
### Pseudoclases por posicion y tipo

```css
    /*[p] no es el primer elemento hijo*/
    .articulo-pseudoclases p:first-of-type{
        background-color: pink;
    }
```

## Pseudoelementos

Dan estilos a partes especificas de un elemento, se usa el `::` para diferenciarlos de las pseudoclases

```css
    .p-pseudoelementos::first-letter{
    font-weight: bold;
    font-size: 32px;
    }

    .input-pseudoelementos::placeholder{
    color: green;
    }
```

>- https://github.com/jonmircha/youtube-html-css/blob/main/02-CursosCSS/index.html
>- https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-elements

## Agrupar Selectores

Imagina que a ciertos elementos html necesitas aplicarle los mismos estilos entonces para eso nos va servir  la (COMA)

```css
    /*Agrupar Selectores  (la coma nos va servir como agrupador)*/
    .form-agrupar-selectores input[type= "text"],
    .form-agrupar-selectores input[type= "email"],
    .form-agrupar-selectores textarea{
        border-color: yellow;
        border-width: 2px; /*ancho del borde para todo los elementos*/
        border-style: dashed;
        background-color: black;
        font-size: 20px;
        display: block; /*hace que cada elemento ocupe una linea*/
        width: 300px;
}
```

---

## El Algoritmo de CSS

El Algoritmo de CSS es la forma en que el navegador aplica los estilos a los documentos html, es de vital importancia entender este concepto para que entiendas como se plican y an algunas ocaciones se sobreescriben las reglas CSS, cuando tengas problemas de que algunos estilos no se apliquen, es por que seguramente no estas cumpliendo con estas caracteristicas

1. La cascada.
2. La especificidad.
3. La herencia.

### La Cascada

Va ser el mecanismo que tiene el navegador web para ir aplicando los estilos, toma tres aspectos en particular:

* Por defecto - el origen del codigo
    *  `user Agent` son los estilos que ya por defecto le va aplicando el navegador a las etiquetas,
    * La personalizada - la configuracion de mi sistema operativo influye en el navegador, ejemplo el modo oscuro, el taño de letra, etc.
    * Estilos del Autor css.
* Especificidad del selector. (el que tiene mayor peso)
* Orden de aparicion. (el navegador lee de arriba hacia abajo, y de izquierda a derecha)

![estilos en el elemento h1](/assets/aplicacion%20css%20a%20h1.JPG)

### La especificidad

Imagina que cada selector tiene un puntaje(peso) acá no tiene importancia la cascada.

> La Especificidad es el peso que tiene un selector cuando hay conflicto de estilos. Se calcula de la siguiente forma:
-       Etiquetas y pseudoelementos -------------- 0,0,0,1 (sumas en el ultimo digito)
-       Clases, atributos y pseudoclases ------------0,0,1,0 (por clada clase o tributo sumas en el 2do digito de R a L)
-       Identificadores -------------------------------0,1,0,0
-       Estilos en línea--------------------------------1,0,0,0
-       !important ------------------Rompe la especificidad


hay 2 casos de herramientas que se suelen utilizar en el desarrollo web, suelen utilizar malas practicas, el tratar de modificar el codigo css de una plantilla que tu compres en marketplace eje Wordpress pues si no tienes los suficientes conocimientos de CSS es muy dificil saber las modificaciones derepente dices, estoy aplicando estos estilos y no hacen efecto entonces muchas veces como para no seguir indagando el problema del por que no está cargando dicho estilo y seguramente es un problema de especificidad por que seguramente en las hojas del estilo del template hay un selector que tiene mayor peso que el que nosotros estamos escribiendo entonces a mucha genge se le hace facil  el `IMPORTANT` altos valores de especificidad se considera mala práctica. En la medida de lo posible traten de utilizar clases para maquetar sus interfaces, utiliza una classe y aplico estilo a los elementos hijos a las b que estan dentro de este selector evita que pasen de 2  0.2.0

```css
    .hijos-descendientes b {
    background-color: thistle;
    }
```

#### Practicando cascada y especificidad.

`blockquote` texto que hace mencion a una cita



* ![especificidad](/assets/especificidad.JPG)

```css
    /*
    Cuando aplicas estilos a las etiquetas se las aplicas a todas las que existan en el documento html
    */



    blockquote#cita-marco.cita-marco{
        background-color: lightskyblue;
    }

    blockquote{
        background-color: burlywood;
    }

    #cita-marco{
        background-color: lightgreen;
    }

    /*ser muy especifico es mala practica*/

    blockquote.cita-marco {  /*especificidad 0,1,1*/
    background-color: tomato;
    }

    .cita-marco{ /*especificidad 0,1,0*/
        background-color: cornflowerblue;
    }

    .cita-marco {
        background-color: mediumaquamarine !important;
    }

    blockquote#cita-marco{
        background-color: lightsalmon;
    }

    .cita-marco {
        background-color: moccasin !important; /*esto se considera una mala practica*/
        background-color: darkorange !important;
        font-size: 32px;
        border-style: dotted;
        border-color: red;
    }
```

https://cdn.jsdelivr.net/npm/bootstrap@5.3.x/dist/css/bootstrap.css 
la hoja de estilo css viene mimificada para que pese menos.

### La herencia.

La Herencia, es la capacidad de un selector de obtener (heredar) los valores de sus ancestros más cercanos, para aplicarla se usa el valor inherit, si queremos evitarla podemos asignar otro valor o inicializar la propiedad en cuestión con el valor initial

para mayor informacion: 

https://web.dev/learn/css/inheritance/#which-properties-are-inheritable

```css
    .cita-marco {
    background-color: moccasin !important; /*esto se considera una mala practica pero no es prohibido usarlo, musho frameworks lo usan como bootstrap, materializa etc. */
    background-color: darkorange !important;
    font-size: 32px;
    border-style: dotted;
    border-color: red;
    } 
  
.cita-marco cite{
    background-color: pink;
    background-color: inherit; /*heredalo*/
    font-size: 24px;
    font-size: initial;
    border-style: inherit;
    border-color: inherit;
    }
```

>- el color no se hereda.
>- todo lo que tiene que ver con tipografia si se hereda

## Reseteo y Normalizacion de estilos.

la mayoria de los navegadores van a la par y tratan de estandarizarse hay 2 formas populares de resetear las hojas de estilo

https://meyerweb.com/eric/tools/css/reset/ 

https://necolas.github.io/normalize.css/   te combiene está.  o tu puedes hacerla.

estas hojas de estilo recetean y normalizan las etiquetas html por defecto lo ideal es que por cascada aplique estos estilos y despues nuestra hoja particular **`esto no lo pegues en tu hoja de estilos propia`** 

si vas a usar alguna de estas herramientas de normalizado y reseteo te recomiendo que sea la herramienta de normalize.

## Prefijos de los navegadores.

html, css son estandares abiertos que viven en nuestros navegadores web, no debemos descargar nada. html (para contenido) css (presentacion) y js (programacion) entonces no debemos instalar absolutamente nada basta con un navegador web.  el navegador ya debe tener capacidad de detectar estas heramientas. Cada navegador web es desarrollado por una empresa chrome - google firefox - la fundacion mozilla  edge - microsoft safari - aple, cada una destas empresas tiene su ruta critica de implementacion que se van dando en los comites de la `w3e`. 

https://caniuse.com/?search=grid 

opera tenia su propio motor que interpretaba el codigo css pero de algunos años para aca cambio al motor de webkit que es navegador que tiene chrome, safari brave

```css
/* 
https://autoprefixer.github.io/
https://caniuse.com/

Prefijos de los navegadores
-webkit-user-select: none;
-moz-user-select: none;
-ms-user-select: none;
user-select: none;
*/

```

## Modelo de Caja.

es la forma en como css interpreta las etiquetas HTML para css  cada una de las etiquetas o elementos de html son una caja que pueden ser cajas de linea  o caja de bloque

![box-model](/assets/box-model.JPG).

>- Padding -  distancia interna existente del borde de la caja al contenido como tal
>- Margin - distancia externa es la distancia que hay de un elemento html a otro  o a su contenedor eje body.

hacen referencia en pixeles.

https://developer.mozilla.org/es/docs/Learn/CSS/Building_blocks/El_modelo_de_caja

Modelo de Caja: Es la forma en que CSS ve a los elementos HTML y ¿cómo los ve? como si fueran cajas con las siguientes propiedades:
  1. El contenido (content): El contenido (texto) del elemento HTML, tomando en cuanta sus dimensiones (width & height)
  2. El borde (border): Lo que delimita cada uno de los elementos HTML
  3. El relleno (padding): Son las distancias internas (La distancia del borde al contenido)
  3. El márgen (margin): Son las distancias externas (La distancia entre el elemento html y sus elementos hermanos o padres)

Dentro del modelo de caja hay que considerar que una caja tendrá 4 lados: en base a las manecillas del reloj

                        1. Arriba (top)
    4. Izquierda (left)                   2. Derecha (right)
                        3. Abajo (bottom)
  

![reloj](/assets/png-transparent-rolex-gmt-master-ii-fashion-clothing-watch-rolex.png)

## Width & Height. (anchura y altura)

  El contenido (content): El contenido (texto) del elemento HTML, tomando en cuanta sus dimensiones (width & height)

  > **Note:** view port es la parte que visualiza contenido en el navegador.


## Border.

El borde (border): Lo que delimita cada uno de los elementos HTML tiene 3 propiedades. (color)color, (width)ancho y (style)estilo.

```css
    h1{
    width: 400px;
    height: 200px;
    /*Propiedades de tipo shorhand -  quiere decir que aplica estilos a los 4 lados*/
    border-color: green;
    border-top-color: red;
    border-width: medium;/*thin - delgado 1px, medium - 3px,  thick - 5px || puedes usar las palabas o la unidad de media en px*/
    border-style: solid;
    /*con este comando simplificamos o sintetisar aun más esto depende de las necesidades que tengas, entre
    cada propiedad debes dar espacio en blanco y el 2 no debes separarlo de su unidad de media que es el PX*/
    border: 2px dashed blue;
}
```

para consultar la [documentacion](https://cssreference.io/property/border-style/)

## Margin & Padding

> **Nota:** ✍ a los `divs` los navegadores no le aplican ningun espaciado por defecto como si pasa con los parrafos o con los titulos que es mas gramatical y semantico.
> El padding son las distancias internas.

![margin de user agent stylesheet](/assets/margin_UserAgent_de_body.JPG)

los siguientes cursos que tendrias que tomas son: `flex-box y grid || taller de maquetacion`.

> _Nota: no olvider mirar tu modelo de caja en el navegador._

## Cajas de linea VS cajas de Bloque.

Caja de Línea
  - **Ocupan el espacio necesario** para mostrar su contenido.
  - No tienen dimensiones modificables (alto, ancho).
  - Permiten otros elementos a su lado.
  - Padding y margin solo empujan a elementos adyacentes en horizontal, NUNCA EN VERTICAL.
Caja de Bloque
  - Ocupan todo el ancho disponible, lo que genera **saltos de línea**.
  - Tienen dimensiones modificables (alto, ancho).
  - No permiten otros elementos a su lado (aunque especifique un ancho, siguen ocupando todo el espacio disponible a lo ancho, generando saltos de línea).


![tabla periodica de los elementos](/assets/html-periodic-table.png)

> **📝las de color amarillo 🟨, las de abajo color moradas🟪 que son elementos multimedia y las de color verde 🟩 salvo el `form` son elementos que trabajan en linea y los demas elementos trabajan en bloque**.

> _Diferencia entre altura anchura y los lados_


Anchura y altura(contenido) | Cuatro Lados de la caja |
---                 | --- | 
Width               | 1. Arriba (top)|
Height              | 2. Derecha (right)|
- | 3. Abajo (bottom) |
- | 4. Izquierda (left) |
---                 | --- |

## Propiedad Display

Nos va permitir mostrar nuestras cajas.

Propiedad Display(visualizacion)

- inline
- block
- inline-block - Se comporta como un elemento de línea pero acepta modificar sus dimensiones (alto y ancho)
- none

```css
    .caja-none{
  display: none;
}
```
user agent stylesheet pone un display a las tablas. estan hechas para tablas, no hay necesidad e ponerlas en un parrafo.

```html
    <table>
        tr*3>td*3{Celda $}
    </table>

    <table>
        <tr>
            <td>Celda 1</td>
            <td>Celda 2</td>
            <td>Celda 3</td>
        </tr>
        <tr>
            <td>Celda 1</td>
            <td>Celda 2</td>
            <td>Celda 3</td>
        </tr>
        <tr>
            <td>Celda 1</td>
            <td>Celda 2</td>
            <td>Celda 3</td>
        </tr>
    </table>
```

```css
td {
    display: table-cell;
    vertical-align: inherit;
}
```
## Propiedad Visibility

se puede confundir con display.

imagina que tienes que ocultar el elemento pero concervar el espacio

```css
    .caja-hidden{
        visibility: hidden;
    }
```
>- **Conclucion!** cuando necesitas ocultar un elemento sin conservar el espacio que ocupaba en le interfaz usa **`display: none;`** cuando necesites que se oculte pero que conserver el espacio que ocupaba usa: **`visibility: hidden;`**

## Propiedad Overflow

cuando ocurre un desbordamiento. ocurre cuano aplicas tamaño especifico al contenido.

![overflow](/assets/overflow.JPG)

esta propiedad nos va sacar de apuros cuando nosotros no sepamos cuando el contenido que va tener una caja lo desborde.

```css
    .overflow{
  background-color: darkcyan;
  width: 200px;
  height: 100px;
  overflow: visible;
  overflow: hidden;
  overflow: scroll;
  overflow: auto;
  /* overflow-y: scroll;
  overflow-x: scroll; */
}
```

## Tamaño de Caja

```css
    .box-sizing-content,
    .box-sizing-border {
    background-color: deepskyblue;
    box-sizing: content-box;
    }

    .box-sizing-border {
        box-sizing: border-box;
    }
```

está propiedad considera el tamaño de la caja desde el borde, todo los valores que hemos aplicado de padding y de borders están considerados en la altura y anchura que tu especificaste en las propiedades width y height.

Hoy en dia el valor por defecto de está propiedad es _**content-box**_. 

>- Hoy en dia en todo los proyectos hacemos un reseteo para que toda las cajas empiencen a considerar su tamaño desde el **borde** 

APLICAMOS EL RESETEO AL PRINCIPIO DE NUESTRA HOJA DE ESTILOS. https://www.paulirish.com/2012/box-sizing-border-box-ftw/ 

```css
    /* 
        apply a natural box layout model to all elements, but allowing components to change
    */
    html {
    box-sizing: border-box;
    }

    *,
    *:before,
    *:after {
    box-sizing: inherit;
    }
```

La gente de bootstrap tambien aplica este reseteo

## Porpiedad Float & Clear

nos permite fotar hacia la izquierda o hacia la derecha elementos, pero hace que pierda la capacidad de seguir el flujo de la etiqueta html, salen de la disposicion y alineacion del documento html y flotan, antes de que tubieramos los modelos de maquetacion **Flexbox & Grid**  no teniamos una manera de acomodar en columnas y filas los elementos de la interfaz de la IU.  y float ayudo mucho pero ya hoy se considera una mala practica trabajar con está propiedad, el efecto secundario que sufren es que despues de flotar despues hay un problema de superposicion con los siguientes elementos que siguen y que no flotan como tal ademas de que si no defines altura o anchura no aplica color.

Dejar un Html vacio es una muy mala practica.

```css
    .float-left{
        float: left;
    }
```

>- **Conclucion!** En la medida de lo posible trata de evitar el uso de _Floats_  https://960.gs/ aprende a maquetar con grid y flexbox que son los modulos adecuados de Css.

## Colapso de Márgenes Verticales

los margenes se superponen se enciman **no se suman**, los margenes horizontales si se suman

![margin](/assets/margin-vertical.JPG)

¿que se puede hacer? cuando vayamos a aplicar margenes verticales solo utilizar una de estas propiedades,

>- o todos `margin-top: 16px;`
>- o todos `margin-bottom: 16px;`

pero no trates de usar ambos.

> cuando vayas a trabajar en las interfaces entre las distancias de un elemento a otro trata de siempre ocupar margin top o margin botton.

## adicion de margenes orizontales.

```css
    .margin-collapse span{
        border: thin solid black;
        display: inline-block;
        margin-left: 16px;
        margin-right: 16px;
        }
```

## Centrado de Cajas

quiero centrarlo con respecto a la ventana del navegador.

```css
    .sitio-web{
  border: thin solid black;
  background-color: #0d1117;
  color: white;
  width: 800px;
  height: 1000px;
  padding: 16px;
  margin-top: 200px;
  text-align: center;/*Centra el contenido mas no la caja*/
  margin-left: auto; /*lo centra proporcionalmente a ambos margenes*/
  margin-right: auto;/* aplicarlo a ambos lados*/
  /*margin: 0 auto;/* SHOR HAND no es buena idea por que aplia valores 0 arriba y abajo.*/
}
```

## Posicionamiento CSS

La propiedades FLOAT y POSITION nos permiten modificar la posición natural de cualquier elemento del documento HTML.


El navegador coloca cada elemento teniendo en cuenta el orden en el que aparece en el documento y su tipo de visualización dependiendo si es un elemento de línea o de bloque.

Con FLOAT y POSITION podemos modificar este comportamiento.

    imagina una fila para el banco, y uno empieza a flotar con un globo de helio. 🍧

Elementos Flotantes
- float: Convierte un elemento en flotante desplazándolo hasta la zona más a la izquierda o más a la derecha de la posición en la que originalmente se encontraba.
- clear: Limpia la flotación (left, right, both)

Tipos de Posicionamiento:
- static (default)
- relative
- absolute
- fixed
- sticky

Para mover los elementos posicionados se activan las propiedades:
- top (vertical - eje Y)
- bottom (vertical - eje Y)
- left (horizontal - eje X)
- right (horizontal - eje X)
- z-index (profundidad - eje Z)

Las propiedades top y left van a tener preferencia por sobre bottom y right respectivamente.

Estás 5 propiedades no funcionan con el valor de static.


## Posicionamiento Static

```css
    .static{
    background-color: yellow;
    position: static;/*es  el valor po defecto*/
    top: 10px;
    left: 10px;
    }
```
## Posicionamiento Relative

el navegador respeta el espacio original del elemento posicionado

```css
    .relative {
    background-color: turquoise;
    position: relative;
    width: 300px;
    height: 50px;
    /*  top: 50px;
    left: 50px; */
    bottom: 50px;
    right: 50px;
    top: -30px;
    left: -10px;
    top: 300px; /*tiene preferencia sobre botton y right*/
    left: 50px; /*tiene preferencia sobre botton y right*/
  }
```    

![positions](/assets/positions.JPG)

> **Recuerda, se alejan del margen**

## Posicionamiento absolute

absolute: El elemento pierde sus dimensiones y posición original en el flujo del documento. Si se mueve puede tomar como referencia 2 elementos:
  1) El primer ancestro(pader) con posicionamiento relativo
  2) Si no encuentra un ancestro relativo, se mueve respecto del documento HTML. 

```css
    .absolute{
    background-color: tomato;
    position: absolute;

  }

  .relative-parent{
    background-color: khaki;
    position: relative;

  }

  .absolute-child{
    background-color: lightcoral;
    position: absolute;

  }
```

perdio sus dimenciones, parece una caja de linea

## Posicionamiento fijo

fixed: El elemento pierde sus dimensiones y posición original en el flujo del documento. 
  Si se mueve toma como referencia el documento HTML y queda fijo en la posición, cuando 
  el scroll se mueva, el elemento no lo hará, queda FIJO

    ```css
        .fixed{
        background-color: lightgreen;
        position: fixed;
        width: 300px;
        height: 50px;
        }
    ```
## Posicionamiento Sticky  

sticky: es un combinación de posicionamiento relative y fixed, para este posicionamiento las propiedades de top,
left, bottom y right no mueven el elemento, sirven como un punto de referencia, mientras no lleguen a ese valor 
el elemento se comporta como relative, cuando llega se convierte en fixed

Para que este comportamiento funcione el elemento sticky debe ser hijo directo del body o su elemento 
contenedor debe tener dimensiones definidas y sólo será sticky dentro de las dimensiones de su contenedor padre.

Cuando 2 elementos se superponen, gana el que tiene posicionamiento diferente al estatico

```css
    .sticky{
  background-color: lightblue;
  position: sticky;/*Tiene que ser hijo directo del body*/
  top: 50px;
}

.sticky-parent{
  border: thin dashed black;
  height: 600px; /*El contenedor padre debe tener contenedor definido con height o width*/
}

.sticky-child{
  background-color: lightslategray;
  position: sticky;
  top: 70px;
}
```
### Propiedad z-index

z-index: propiedad que permite controlar la profundidad de los elementos posicionados, 
su valor por defecto es auto, acepta número positivos, negativos y cero.

> A mayor valor el elemento esta más al frente, a menor valor más al fondo.

Un elemento padre nunca podrá estar sobre sus elementos hijos, sin embargo 
los elementos hijos si pueden dándoles un valor negativo **y que el elemento padre no tenga definido valor de z-index** 

el primer documento que aparesca posicionado en nuestro html es el que va al fondo, es la misma logica de los editores de foto como photoshop o figma.

Cuando estas diseñando una interfaz y empiezas por la cabecera el menú, el contenido, el pie de pagina, pero cuando ya esamos trabajando en la practica https://www.youtube.com/watch?v=ErtR07GLq54 hay cosas que derepente surgen y tienes que ir agregando elementos html e irles dando estilos. z-index 999

```css
     .z-index-1,
 .z-index-2{
  background-color: mediumaquamarine;
  position: relative;/*Z-indez funciona a cualquier valor menos el estático.*/
  border: thin solid black;
  width: 200px;
  height: 200px;
 }

 .z-index-1{
  z-index: 1;
  z-index: -1;
 }

 .z-index-2{
  top: -200px;
  left: 100px;
  z-index: 2;
 }

 .z-index-parent{
  background-color: mediumorchid;
  width: 300px;
  height: 300px;
  position: relative;
  /*z-index: 2; /*es muy raro que un elemento que tiene mas cosas tenga que sobreponerse sobre sus hij@s*/
 }

 .z-index-child{
  background-color: mediumvioletred;
  position: relative;
  width: 150px;
  height: 150px;
  top: -75px;
  left: 75px;  
  z-index: -30;/*aplicas numero negativo y funciona*/
}
```

## Cabecera Fixed VS Cabecera Sticky

siempre hay que tener Orden. 

Como el position fixed pierde su lugar usamos `Sticky` cuando quiereas posicionar una cabecera el ganador es:

```css
    .sticky-top{
    position: sticky;
    top: 0;
    }
```

## Efecto de Slides con position sticky

```css
    .slide{
    background-color: paleturquoise;
    width: 100%;
    /* height: 100vh; */ /*Lo comente por que desbordaba el contenido*/
}

.slide:nth-child(odd){
    background-color: palevioletred;
}

.slide-title{
    background-color: palegreen;
    padding: 16px;
    text-align: center;
    position: sticky;
    top: 50px;
    margin-top: 0;
    margin-bottom: 0;
}
```
## Ventana Modal / Menú Movil con posicionamiento fixed

te recomiendo hacer posicion fixed te puede servir para un menú de navegacion movil que a la hora de pulsar el boton que abre el menu en lugar de que lo abra hacia ariba o hacia abajo o hacia los lados que aparesca con un efecto de opacidad o tambien vistos en las ventanas modales

```css
    .modal-window{
    background-color: black;
    /* position: absolute; */
    color: antiquewhite;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    opacity: 0.5;
    display: none;
}

.modal-window:target{
    display: block;
}
```

## Margenes Negativos

valores negativos dentro del BOX model solo lo podemos aplicar para las distancias externas `margin's`

```css
    
.box{
    background-color: sandybrown;
    padding: 20px;
    margin-top: -30px; /*los margenes funcionan muy similar a las propiedades left top boton y right*/
    margin-left: -30px;
    padding-right: -30px; /*no aplica*/
}
```

***

---

## **Colores en CSS**



>- Color al fondo `backgraund-color:;`
>- Color al al texto `color: ;`
>- Color al borde de la caja `border`

hay 4 formas diferentes de trabajar con los colores: https://htmlcolorcodes.com/

>- a traves de los nombres
>- Sistema hexadecimal
>- Sistema **RGB**
>- HSl.


### Colores a traves de los nombres

¿Donde sale la lista de los colores? https://htmlcolorcodes.com/color-names/

Cuando estas haciendo un trabajo de investigacion en microsoft word y agregar una imagen, y si alguna vez haz impreso fisicamente, quizá ves una gran diferencia entre el color que imprimio tu impresora  contra lo que tu vez en la pantalla y eso es por que microsoft word está pensado para pantallas digitales no para imprimir entonces el sistema de colores es RGB  en cambio CMYK es para impresos pero en la web no vamos a usar el CMYK peero con esto de demuestro que está pagina te muestra los colores en diferentes sistemas

```css
    .color-by-name{
    background-color: coral;
    color: rebeccapurple;
    border: thick solid greenyellow;
    }
```

**Comvertidor de colores**

en el buscador debes poner:

>- RGB to hex

### Sistema Hexadecimal

está basado en el sistema de numeracion hexadecimal

> 0123456789ABCDEF

> RedGreenBlue (Medios Digitales)  vs CyanMagentaYellowKey(Medios Impresos) Sofware de diseño  que son pensados para impresos como Adobe InDesign, Adobe Illustrator inclulso Photoshop tiene este sistema CMYK.

los colores en HEX van a tener 6 digitos eje:

>- `#FF6600`

los 2 primeros valores son para el canal Rojo, los 2 siguientes son para el canal Verde, y los 2 ultimos es para el Azul, si son iguales los digitos, se pueden simplificar a 3 valores: 

>- `#f60`

```css
    .color-hex{
    background-color: #FF6600;
    background-color: #F60; /*lo podemos simplificar*/
    background-color: #00000050; /*agregando canal de opacidad al 50 % no hay nesecidad de poner 100 ya con el color es suficiente*/
    background-color: #0005;
    color: rebeccapurple;
    border: thick solid #ff0000;
    border: thick solid #f00;
    }
```

en los colores hexadecimales tambien podemos controlar la opacidad (transparente o la presencia 100%)

### Sistema RGB

Debemos utilizar una funcion RGB() y debemos poner el color de 0-255.
    Acepta 8 bits por canal
    Bit(0/1) para asignar cada uno de los colores que existen en la gama de paleta de colores para cada canal tenemos 8 posiciones
    ¿por que 255? 2 elevado a la potencia 8 = 255
    Por cada canal de color tenemos valores que van de 0 a 255

```css
    .color-rgb{
    background-color: rgb(255, 255, 255);
    background-color: rgb(255, 0, 0);
    background-color: rgb(0, 255, 0);
    background-color: rgb(0, 0, 255);
    background-color: rgb(0, 0, 0);
    background-color: rgba(0, 0, 0, .5); /*'A' representa el canal alfa*/
    color: rgb(255, 102, 0);
    border: thick solid rgb(128, 109, 7);
}
```
### Sistema HSL

Contempla los 2 sistemas, tanto para el sistema de color para medios impresos
    como el que va para medios digitales.

    HueSaturationLightness(Tono-Saturacion-Luminosidad)

    El primer valor es Hue (Circulo Cromático)

    0º -> red
    60º -> yellow
    120º -> green
    180º -> cyan
    240º -> blue
    300º -> magenta

    El segundo valor es la saturacion (Intensidad del Color)

    0% -> Escala de grises
    100% -> color puro

    El tercer valor es Lightness (luminosidad del Color)

     0% -> negro
     50% -> color puro
     100% -> blanco

```css
    .color-hsl{
    background-color: hsl(0, 100%, 50%);
    background-color: hsl(120, 100%, 50%);
    background-color: hsl(240, 100%, 50%);
    background-color: hsl(30, 100%, 50%);
    background-color: hsla(30, 100%, 50%, 0.5);/*canal alpha para la opacidad va de 0 - 1*/
    color: hsl(0, 0%, 0%);
    color: hsl(0, 0%, 100%);
    border: thick solid hsl(210, 74%, 65%);
}
```

### ¿Que sistema de colores uso?

la verdad es que cualquier sistema de colores que quieras usar es bien venido no es que uno sea mejor que otro,cualquier sistema de color el navegador lo computa con el sistema RGB O RGBA.

> _depende tambien de las guias de estilo que tu equipo de trabajo tenga_ si tu trabajas independientemente pues ahi tu evalua que sitema de colores de combiene, lo que si note recomiendo es estar mesclando varios sistemas de colores en un mismo proyecto.

### Transparent & currentColor

imaginate  que aveces vas a tener la necesidad de en version movil (responsive design otro tema) pero ya en la version de tableta o computadora necesitas quitarle el color ¿Como le puedes quitar el color a un elemento? pues hay un valor especial que se llama transparent.

```css
    .color-transparent-current{
    background-color: darkmagenta;
    background-color: currentColor;/*El siguiente ancestro seria el body, lo cual el color de texto es negro,*/
    /* color: white; */
    background-color: transparent; /*RGBA*/
    color: olive;
    border: thick solid currentColor; /*hace referencia al valor de la propiedad color del elemento y si el
    elemento no tiene color definido entonces va buscando al ancestro mas inmediato*/
    }
```

### Propiedad Opacity

cuando aplicamos la propiedad `opacity` aplica para toda las propiedades css que tenga el selector al que le estamos aplicando la opacidad

```css
    .opacity-00{
    opacity: 0;   
}

.opacity-10{
    opacity: 0.1;   
}
```

## Unidades de medida en CSS

Unidades de Medida
1) Absolutas (Su valor no cambia, son unidades del mundo real)
    pc, cm, mm, in, Q
    pt (1/72in) (puntos)
    px (1/96in)
2) Relativas (Su valor es relativo a un contexto)
**em, rem, ex, ch - al tamaño de la fuente (_estan basados en el tamaño del contenedor padre_)**
    em - basada en la anchura de la "m" de la fuente del elemento (por que es el caracter más ancho)
    rem -  basada en la anchura de la "m" de la fuente del elemento raíz (html)
    ex - basada en la altura de la "x" de la fuente del elemento
    ch - basada en la anchura del "0" de la fuente del elemento
    % - el contexto que toman como relativo es el (al) tamaño del contenedor
**vw, vh, vmin, vmax - al tamaño del viewport**
    vw - ancho(with) del viewport van de 1 a 100
    vh - alto del viewport van de 1 a 100
    vmax - entre vw y vh toma el que tenga mayor valor
    vmin - entre vw y vh toma el que tenga menor valor

  Conversiones entre unidades - https://pxtoem.com/

  ![imagen](/assets/units.png)

  ### PIXELES

  es muy importante que todo proyecto que inicies tenga el siguiente reseteo.

```css
    html{
    box-sizing: border-box;
    }

    /*pool erich*/
    *,
    *::after,
    *::before{
        box-sizing: inherit;
    }

    .pixels{
    background-color: cadetblue;
    width: 500px;
    height: 400px;
    padding: 20px;
    font-size: 16px; /*valor por defecto que los navegadores aplican al tamaño de la letra es de 16 px en la medida de lo posible hay 
    que utilizar unidades de medida relativas ¿Por que? el concepto de responsive design dependiendo de el dispositivo en la que nos 
    encontremos no es bueno usar pixeles por que son unidades absolutas son unidades que no varian por que vienen del mundo real pero 
    si vas a diseñar una interfaz que se va imprimir ahi si puedes usar pixeles cm, pulgadas*/
    border: thick solid rebeccapurple;
    }
```

---

  ### EMS Unidades relativas al tamaño de la fuente.

  los pixeles siempre van a tener el tamaño bien definido en cambio cuando empezamos a aplicar porcentajes EMS estamos tomando como referencia un contexto

  los **ems** siempre van a hacer referencia al tamaño de fuente es decir a la propiedad `font-size` que tenga el contenedor padre que tiene dicho elemento

  ```css
    .ems{
    background-color: cadetblue;
    font-size: 24px; /*se toma como el tamaño de la fuente BASE*/
    padding: 1em; /*pone el mismo tamaño de la fuente font-size*/
    border: thick solid rebeccapurple;
}

.em-child{
    background-color: salmon;
    border: thick solid beige;
    margin: 0.5em; /*se basan en el font-size de este mismo elemento*/
    padding: 1em;
    font-size: 2em; /*Busca el ancestro mas inmediato*/

}
  ```

### REM's 

El tamaño está basado en el tamaño de la fuente `font-zise` del documento `html` no hay tanto problema, por que se basa en el tamoño de letra que tiene asignado nuestro `html`

```css
    html{
    box-sizing: border-box;
    font-size: 16px;/*por defecto es 16px*/
    }

    /*
        REM's no debemos estar buscando entre ancestros padres
    */
    .rems{
    background-color: cadetblue;
    font-size: 24px; 
    padding: 1rem; 
    border: thick solid rebeccapurple;
    }

    .rem-child{
    background-color: salmon;
    border: thick solid beige;
    margin: 0.5rem; 
    padding: 1rem;
    font-size: 2rem; 
    }
```

### EX's 

En la practica no se utilizan mucho.

```css
    .ex{
  background-color: cadetblue;
  font-size: 24px; 
  padding: 1ex; 
  border: thick solid rebeccapurple;
    }
```
### CH's

toma como base de medida el numero `0` tambien son relativos al tamaño de la fuente en ``html``

imaginate que tu tengas que definir el diseño de un boton y el texto que pueda introducirse dentro del boton pero tu sabes que ese boton que estas diseñando es maximo para una palabra que no ocupe mas de 10 caracteres y ahi es donde nos van a ayudar los CHES.

> _utiliza cuando en las dimenciones, necesites que siertos elementos de la interfaz visual conserven cierto numero de caracteres_


```css
    .chs{
  background-color: cadetblue;
  width: 10ch;
    }
```

### Porcentages %

Cuando hablamos de los porcentajes hay que tener en cuenta la naturaleza de la etiqueta (bloque, linea)

> `width: 80%;`

la caja de bloque está al 80% de su contenedor padre el contenedor padre en esté caso es el ``body``

Es muy importante el tamaño que le damos al `font-zise` del `html` por que eso define la base para unidades relativas.

El `body` va ir creciendo conforme baya creciedo su contenido.

Nosotros podemos hacer cambiar este comportamiento sobre todo en la propiedad `heigt` cuando ya tiene un valor establecido

> **``como los pixeles son absolutos, no redimencionan aunque el tamaño de la pantalla sea menor a diferencia de las unidades relativas.``**

en el ancho no hay problema, se va adaptar al ancho del contenedor

### Unidades del Viewport

Es la parte visible donde vemos el contenido html

> Recuerda, los porcentajes son basados en el tamaño del contenedor,  entonces el `body` que tenemos de 8 pixeles a los cuatro lados no afecta cuendo yo tengo un with del ``100%``


> **_en conclucion: usa vh para el alto y 100% para el ancho_**

si quisieras generar componentes como las ``Herro image``  podrias generar una clase tipo full scri

```css
    .viewport{
  background-color: darkcyan;
  width: 50vw; /*estan basados en el tamaño de a pantalla sin importar los devices.*/
  /*Recuerda, que la etiqueta body tiene margenes por defecto y recuerda que las barras de 
  scroll del navegador tambien forman parte del viewport.*/
  width: 100%; /*✅*/
  width: 100vw;
  height: 50vh; 
  height: 100vh;/*✅*/
}
```

> _No importa que un elemento sea hijo de otro, va ignorar los atributos de: alto, ancho font-size, etc. siempre va tomar las dimenciones de la pantalla disponible_

las unidades del viewport son unidades que permiten fluir diferentes valores a la que los aplicamos.

### ¿Cuándo usar cada unidad de medida?

> _1 absolutas: para cuando una pagina se vaya a imprimir_

> _2 Unidades relativas: el font-size siempre definelo en ``px``_

>_Todo lo que tiene que ver con tipografia te sugiero que lo expreses en ``REMS``_ tambien para aplicar distancias de margin y padding.

> _Ems puedes usarlo en las cards_

> _Exs, si ya sabes cuantos reglones va a recivir,  entonces la altura que tenga de esta caja que tenga la descripcion la puedes definir en EXS (se basa en la distancia de los caracteres)._

> _CHS, en los casos donde debes de definir el numero de los caracteres_

en el diseño responsivos se usa mucho en definicion de ancho y alto de ciertas secciones de tu contenido

**las unidades del viewport** cuando tengas que tomar como referencia el tamaño de la pantalla (herro image, textos fluidos) 

## Variables y Funciones en CSS
Una variable es un espacio recervado de de memoria en nuestra computadora que va almacenar un dato, las variables css así como en los lenguajes de programacion van a tener un alcance un ambito en el que existan. ese ambito va ser el selector en el que nosotros definamos la declaracion de la variable y todo sus elementos subsecuentes (hijos)

### Custom Properties y Funcion Var()

las variables se tienen que definir dentro de un selector

- `para definir variables en CSS deben empesar con 2 giones (--)`

las variables se les puede heredar a los elementos hijos. 

Hay ciertar reglas que nuestras variables css deben cumplir y una de esas es el `Ambito` hasta que punto existen nuestras variables.
- > las variables se deben definir dentro de selectores.
- > Y van a existir para todo los elementos hijos 

si quieres que tus variables existan para todo tus elementos html lo que debes hacer es declarar tus variables en la etiqueta html. Pero en lugar de utilizar la etiqueta html vamos a utilizar una pseudoclase llamda ``ROOT`` hace referencia ala etiqueta `html`  con la difirencia que tiene mayor peso, es decir que tiene mayor especificidad (0.0.1) (0.1.0) esto lo vimos en el tema de la especificidad.

- > si quieres que tus variables apliquen para todo tus elementos(etiquetas) html lo ideal es que lo vayas declarando en el selector root. 

herramientas como bootstrap ya empiezan a utilizar en su hoja de estilos en las variables

```css
    :root{
    color: darkgreen;
    --default-bg-color:skyblue;
    }

    html{
        color: red;
    }

    .custom-props-1{
        --primary-color: gray; /*Recuerda _existea en este elemento y sus hijos_ */
        --font-zize:32px;
        background-color: var(--primary-color);
    }

    .custom-props-2{
        background-color: var(--default-bg-color);
        border: thin solid var(--border-color);
        padding: 1rem;
    }

    .custom-props-3{
        font-size: var(--font-zize);
        border: thin solid var(--border-color);
    }

    .title-props{
        --primary-color:navy;
        color: var(--primary-color, orange); /*En el caso de que no exista el primari color aplica Orange*/
        background-color: var(--default-bg-color);
    }
```

### Funcion URL

url()  nos sirve para cargar una hoja de estilos:

`@import url("otra-hoja.css")`

tambien puede servir para mandar a llamar tipografias y fondos, para mandar a cargar contenido externo

### Función Cal()

nos sirve para hacer calculos aritméticos.

```css
    .ch-10{
    --padding-size:4ch;
    --num-ch:10ch;
    background-color: var(--default-bg-color);
    font-size: 2rem;
    padding: var(--padding-size);
    width:calc(var(--num-ch) + var(--padding-size)*2);/*Cuando tenemos operador como (+-*) y los operandos (var, 2)8es importante dejar espacio */
}

/*no podemos tener padding negativos */
```

### Funcion min() & max() 

Son funciones a las que podemos dar diferentes valores separados por comas y siempre va tomar el valor que sea minimo o maximo de la funcio que estemos utilizando

- > Min: va listar va asignar  el que menor valor tenga

- > Max: va listar va asignar  el que mayor valor tenga  

```css
    .min-max{
    background-color: var(--default-bg-color);
    margin-top: 1rem;
    width: min(300px, 20vw, 20rem); /*300px es menor que el 20% de la pantalla de viewport (Siempre va  ganar el que tenga menor valor)*/
    height: max(200px, 25vh);
}
```

### Funcion Clamp()

¿donde lo podemos aplicar espectacularmente?

en los titulos de tamaño dinamico.

```css   
    h1{
        font-size: clamp(2rem, 1rem + 3vw, 3rem);
        background-color: darkgoldenrod;
    }
```
## Estilos de Fuentes y Textos 

[Title](fonts-texts.html) ¿como llego esto?

La familia de fuentes es el conjunto de tipografias.

Font es un shord hand. asi como ``border, margin, padding`` que tiene 4 lados

    font-family
    font-size
    font-weight
    font-style
    font-variant
    line-height  (la altura que va tener en el interlineado)
    font

depende de la familia tipografica si tiene ese peso o no.

``BOLD`` el navegador aplica una negrita ficticia.

en la paractica utilizas:

- > `font-family, font-size, font-weight`

```css
    .font{
    font-family: Georgia, "Times New Roman", Times, serif; /*si la primera opcion está disponible aplicalá*/
    font-family: sans-serif;
    font-size: 32px;
    /*No toda las tipografias tiene el mismo grosor*/
    font-weight: bold;
    font-style: italic; /*se puso en cursiva*/
    font-variant: small-caps; /*Comvierte todo a mayusculas*/
    line-height: 2;
    font: italic small-caps bold 24px / 1.5 monospace; /*Respetando el orden*/
    }
```

### Fuentes Externas (@font-face & font-display)

¿Que pasa si yo tengo la necesidad de agregar una tipografia que no se encuentran en mi sitema operativo?, para eso podemos usar una regla de css que se llama @font face y mandar a llamar una tipografia externa, entonces para eso necesitarmos tener un achivo fisico de la tipografia.

font-display:
  auto - permite que el navegador utilice el método predeterminado que suele ser block
  block - oculta brevemente el texto hasta que la fuente haya sido descargada por completo
  swap - indica al navegador que utilice la fuente alternativa para mostrar el texto hasta que la fuente personalizada se haya cargado por completo
  fallback - es una mezcla de auto y swap
  optional -ocultará el texto, luego lo cargará con la fuente alternativa y finalmente aplicará la fuente personalizada


```css
    @font-face{
    font-family: "Chalet";
    src: url("../assets/Chalet.woff") format("woff"); /*sube un nivel y carga el archivo...*/
    font-display: swap;
    /* 
    src: url("../assets/Chalet.woff") format("woff"),
        url(../assets/Chalet.woff2) format(woff2); */
    
}

.chalet{
    font-family: "Chalet", sans-serif; /*sans-serif en la tipografia alternativa*/
    font-size: 2rem;
}
```

### Google Fonts

cuando decidas elegir una tipografia, tambien revisa y toma en cuenta las necesidades de contenido textual que vas a tener en tu sitio eje: en el Idioma ingles no existe la Ñ. 

https://fonts.google.com/specimen/Raleway?query=raleway 

sé precavido con el numero de estilos y el numero de fuentes ``utilizar 3 o mas tipografias se puede considerar mala practica`` considera que cada archivo tipografico lo tiene que cargar el navegador entonces podemos tener problemas de rendimiento a la hora de visualizar el contenido un uso de fuentes puede ser uno o dos, ademas usar mas de 3 tipografias podemos confundir a usuario

poner atencion el los glifos(Glyphs) que soporta y caracteres especiales. 

### Estilos de Textos.

 
text-align
text-decoration
text-indent
text-overflow
  overflow: hidden;
  white-space: nowrap;
text-transform

letter-spacing

white-space  (nos va decir que hacer con los espacios enblanco)
white-space: pre; respeta todo los espacios en blanco, esto lo vimos en html cuando respeta los espacios*

word-break
word-spacing (e smus similar a letter-spacing solo que este trabaja con palabras)
writing-mode


``siempre puedes consultar a la pagina: cssreference.io``

```css
    .text{
    
    font-size: 2rem;
    text-align: right;
    text-align: center;
    text-align: justify;
    text-align: left;
    text-decoration:overline ;
    text-decoration: none;
    text-indent: 3rem; /*Es la sangria del parrafo. una indentacion a linea que comienza el parrafo*/
    text-transform: capitalize; /*Toda las palabras locombierte en mayuscula en capital leter*/
    text-transform: lowercase; /*los correos siempre se escribe en minusculas*/
    text-transform: uppercase; /*Todo locombiertes a mayuscula*/
    text-transform: none; /*no apliques ninguna transformacion*/
    letter-spacing: 0.5rem; /*ES el espaciado que va tener cada caracter*/
    /*white-space: pre; /*/
    word-break: keep-all;/*normalita*/
    word-break: break-all;/*parte las palabras a */
    writing-mode: horizontal-tb;
    writing-mode: vertical-rl;/*rigt to left*/

}

.text a{
    text-decoration: none;
}

.text-overflow{
    background-color: blanchedalmond;
    border: thin solid black;
    padding: 1rem;
    font-size: 2rem;
    width: 50%;
    overflow: hidden; /*lo va ocultar*/
    white-space: nowrap; /*hace que se vaya a una sola linea*/
    text-overflow: ellipsis;
    
}

.white-space{
    white-space: pre; /*Se comporta como una etiqueta codigo*/
}


.word-spacing{
    font-size: 2rem;
    word-spacing: 1rem;
}
```

## Iconos Tipograficos.

vamos a revisar 3 librerias que nos ofrecen iconos vectoriales que estan basados en tipografias en lugar de generar texto nos va generar iconos.

¿Como implementamos estos iconos de google fonts que nos podrian servir si estamos haciendo un dashboard un administrador?

Estos iconos forman parte del Material Design (que es le lenguaje visual de las gias de estilo de google).

https://fonts.google.com/icons
https://icons.getbootstrap.com/#install 

Bootstrap ya tiene sus iconos CDN: content developen network las grandes empresas tienen cdns CDN: es una infraestructura en internet que nos permite alojar las librertias mas populares de CSS y Js 

otra pagina de Iconos:
https://fontawesome.com/  nos pide que ingresemos nuestro correo electronico entonces usamos una pagina externas netamente de CDN's

https://cdnjs.com/libraries/font-awesome


buscamos la version gratuita
https://fontawesome.com/search?m=free&o=r (tiene iconos regulare, solidos e iconos de marcas)

click en:`Copy ling tag`

> Resumen: _mandar a llamar la hoja de estilos que carga la tipografia de iconos, ir a revisasr los iconitos y obtener el codigo html que  nos permite visualizar esos iconos la ventaja de estos iconos es que no son imagenes, son caracteres_

## Propiedades Border Radius

Una caracteristicas de los bordes es la capacidad de Redondeo

`Border-radius` es un short hands para cuatro propiedades

si se van a la pagina de 

podemos colocar bordes de forma redonda y bordes de forma eliptica.

> https://developer.mozilla.org/en-US/docs/Web/CSS/border-radius

Cuando nosotros aplicamos border radius con la diagonal a 2 valores eso significa que en lugar de hacer un borde totalmente redondeado tomando como referencia una circunferencia perfecta lo vamo hacer como si fuera una elipce

```css
    .box{
    background-color: black;
    margin: 2rem auto;
    width: 400px;
    height: 400px;
    border: thick solid red;
}


.border-radius{   
    border-radius: 2rem;
    border-top-left-radius: 4rem;
    border-top-right-radius: 4rem;
    border-bottom-left-radius: 4rem;
    border-bottom-right-radius: 4rem;
    border-radius: 2rem 4rem;
    border-radius: 2rem 4rem 0;
    border-radius: 4rem 3rem 2rem 1rem; /*en sentido de las manecillas del reloj*/
    border-radius: 2rem;
}

.border-radius-2{
    border-radius: 2rem / 4rem; /*Estoy aplicando '2rem' en X y '4rem' en y*/
    border-radius: 2rem 4rem/ 4rem 8rem;/*expresandolo a n valores*/
    /*border-top-left-radius: 4rem;/*tambien podrian expresarlo con las propiedades que afectan a un solo lado*/
}

/*Circulo*/
.border-radius-3{
    border-radius: 50%; /*Significa que se va redondear a la mitad [Obenemos un circulo]*/
}

/*pero tiene que ser una caja cuadrada en dimenciones a ancho y alto*/
.border-radius-4{
    width: 400px;
    height: 200px;
    border-radius: 50%; /*[Obtenemos una elipce] */
}
```
## Propiedades Outline

Es como un borde externo, No forma parte del modelo de caja no existe ``Outline a los 4 lados`` .

Es como un aura  que no va interrumpir el espacio que tienen los demas elementos.

Los elementos que mas aprovechan esto del Outline son los elementos de formulario. Cuando quieras ver pseuda clases en el inspector de elementos click en `:hov` cuando tenemos el foco del puntero del maus sobre un elemento Input

```css
    .outline{
    color: white;
    text-align: center;
    outline-width: 5px;
    outline-style: dashed;
    outline-color: chartreuse;
    outline: thick solid blue;
    /*border-width:100px*/
    /* outline-width:100px; */
    outline-offset: 3rem; /*es la distancia que hay entre el Borde  al Outline*/
   outline-offset: -3rem;
    }
```

## Estilos del Fondo

Usamos mucho `Backgraund-color` y no es la unica propiedad

Hay varias propiedades de ``Background-`` esto lo podemos ver en CSSreference es el short-hands de 8 propiedades. 

> _Te sugiero que lo evites_

**background-color:** define el color de fondo del elemento
**background-image:** define la imagen de fondo del elemento
**background-size:** define el tamaño de la imagen de fondo, primer valor x, segundo y
    - cover: cambia el tamaño de la imagen de fondo para asegurarse de que permanezca completamente visible
    - contain: cambia el tamaño de la imagen de fondo para asegurarse de que el elemento esté completamente cubierto
**background-repeat:** define cómo se repite la imagen de fondo en el elemento
**background-position:**
  define la posición de la imagen de fondo, primer valor x, segundo y, si no se especifica un segundo valor éste será center
  aparte de valores numéricos podemos indicar el posicionamiento con las palabras: center, top, bottom, left and right
**background-clip:** define cuánto debe extenderse el fondo dentro del elemento.
**background-origin:** define el origen de la imagen de fondo.
**background-attachment:** define cómo se comportará la imagen de fondo al desplazarse por la página.

```css
    .box{
    margin: 2rem auto;
    width: 300px;
    height: 300px;
    border: thick dashed red;
}

.bg-color{
    background-color: black;
}

.bg-image{
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
}

.bg-size{
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    /* background-size: 300px 200px; */
    background-size: 300px; /* la proporcion de mi imagen es la misma el ancho es de 300px pero el alto la está calculando automaticamente*/
    background-size: cover; /*cubre con una sola imagen sin deformarla [cora la imagen]*/
    background-size: contain;/*toda la imagen se visualiza en el contenedor*/
}

.bg-repeat{
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-size: 100px;
    background-repeat: repeat;
    background-repeat: repeat-x;
    background-repeat: repeat-y;
    background-repeat: no-repeat;
}

.bg-position{
    background-color: skyblue;
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-size: 100px;
    background-repeat: no-repeat;
    background-position: 10px 20 px; /*puedes utilizar unidades de medida o palabras Recervadas si usas palabras evita usar unidades de medida*/
    background-position: 1rem 2rem;
  background-position: 10% 20%;
  background-position: 10%;
  background-position: 10% center;
  background-position: top center;
  background-position: top right;
  background-position: top left;
  background-position: bottom center;
  background-position: bottom right;
  background-position: bottom left;
  background-position: bottom;
}

.bg-clip { /*Esta orientada hacia el fondo*/
    background-color: skyblue;
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-repeat: no-repeat;
    background-size: 200px;
    background-size: cover;
    background-clip: border-box; /* default */
    background-clip: padding-box;
    background-clip: content-box;/**/
    padding: 1rem;
  }
  
  /*Para la imagen de fondo*/
  .bg-origin {/*de dece la posicion desde donde deberia empezar la imagen de fondo*/
    background-color: skyblue;
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-repeat: no-repeat;
    background-size: 200px;
    background-size: cover;
    background-origin: padding-box; /* default */
    background-origin: border-box;
    background-origin: content-box;
    padding: 1rem;
  }
```


¿Que diferencia hay entre usar Backgraunt y Backgraunt-Color? si solamente vas a trabajar con el color de fondo entonces usa backgrount-color por que te resetea toda las demas propiedades por eso en la medida de lo posible evita el Short hand [bacground: color, size...] por que yo prefiero estar utilizando las propiedades que voy a ir afectando que aprenderme el ORDER primero image color...

Si vas a tener imagenes de fondo lo ideal es que tengas imagenes en formato png con transpariencia

Arte.

```css
 .bg-attachment{
    background-color: skyblue;
    background-image: url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: 50vh;
    background-attachment: scroll;/*default*/ 
    /*Es como si fuera una ventana donde vemos de arriba hacia abajo, LA IMAGEN SE QUEDA FIJA EN EL VIEW PORT*/
    background-attachment: fixed;
  }
/*la imagen que esté mas hacia el punto y coma, la ultima es la que va estár mas al fondo*/
  .bg-multiple{
    width: 50%;
    background-image: 
      url("../assets/png-transparent-rolex-gmt-master-ii-fashion-clothing-watch-rolex.png"),
      url("../assets/Nissan_Skyline_GT-R_R34.jpg");
    background-repeat: repeat-x, no-repeat; /*Respectivamente a las urls*/
    background-size: 10%, cover;/*10% del contenedor || puedes tener efectos bastante interesantes*/
    }

  .bg-art{
    width: 100%;
    height: 700px;
    background: url("../assets/arbol.png") no-repeat center bottom,
    url("../assets/aves.png") no-repeat center bottom fixed,
    url("../assets/cielo.png") no-repeat center top;
  }
```
## Estilos de Imágenes.

quisas me veas muy repetitivo, la mejor forma de aprender es la repeticion entonces que tu me veas hacer esto cosntantemente se va ir formando el habito.

Una de las caracteristicas mas importantes es hacerlas responsivas es decir que las imagenes se vayan adaptando al contenedor. Entonces hacer una imagen que se adapte al tamaño de la pantalla.

¿Cuando tu quieras lograr que una imagen sea responsiva? es buena practica que como estilo de reseteo a tus imagenes le apliques la propiedad ``max-width: 100%;`` 

> _Recuerda! las Imagenes trabajan en linea._

con **relleno-Fill** es esté comportamiento por defecto que está tratando de ajustar las dimenciones de la imagen al tamaño que le hemos especificado sin contar su proporcion



Si tu necesitas que tu imagen se vaya adaptando al tamaño del contenedor con que le apliques esto es suficiente.

```css
    img{
    max-width: 100%;/*hack*/
    height: auto;
}
```

el object fit y el object position lo vas a utilizar cuando necesites medidas concretas a tus imagenes ejemplo una targeta-card

```css
.card img{ /*busca el elemento img dentro de card*/
    background-color: blanchedalmond;
    height: 300px;
    object-fit: fill;/*default*/
    object-fit: cover; /*corta y lo centra Activa la otra propiedad  Object-Position*/
    object-fit: contain; /*Asegura que toda la imagen se vea dentro del contenedor*/
    object-fit: none; /*escala la imagen al tamaño real y como el valor por defecto de object position es 50 50  pues la está centrando agarra el centro de la imagen*/
    object-fit: scale-down; /*toma el valor que sea menor de los valores CONTAIN y  none no es muy utilizado*/
    /*object-position: 50% 50%;/*Default*/
    object-position: right top;
    object-position: right bottom;
    object-position: left top;
    object-position: -50px center;
    object-position: 50% 50%;
}
```

## Estilos de listas.

ir a `cssreferens` o mejor a un a la documentacion de mozilla developmen network [MDN](https://developer.mozilla.org/es/docs/Web/CSS/list-style-type).

al tenr fuera la viñeta se ve una composicion visual mas fluido, bien hecho

``LIST-STYLE-POSITION: outside;`` por defecto 


List-Style es un short-hand tienes que listar el tipo la imagen y la posicion

**Texto en columna**

>No confundas, para maquetacion vamos a usar el modulo de flexbox y el modulo de grid css esto es mas que nada para redacciones 

¿Cuando podriamos usarlo? eje: cuando estemos simulando la maquetacion de un sitio de periodico

hay 4 propiedades que controla esto.

```css
    .list{
    list-style-type:disc; /*default*/
    list-style-type: square;
    list-style-type:circle;
    list-style-type: lower-roman;
    list-style-type: upper-roman;
    list-style-type: decimal;
    list-style-type: decimal-leading-zero;
    list-style-type: lower-greek;
    list-style-type: none;/*si tú le quieres quitar el tipo tambien le puedes poner el valor de none*/
    list-style-type: lower-greek;
    list-style-image: url("../assets/cielo.png"); /*Es muy retro*/
    list-style-image: none; /*default*/
}

.list li{
    list-style-type: none;
}

.list li::before{
    content: "";
    display: inline-block;
    width: 2rem;
    height: 1rem;
    background-image: url("../assets/alcaldia.png"); /*el tamaño  no se visualiza aun*/
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
}

/*LIST-STYLE-POSITION: outside;  bulet: la viñetita que se pone al lado de las listas*/

.list-2 li{
    background-color: coral;
    list-style-position: outside; /*la viñeta está afuera*/
    list-style-position: inside; /*la viñeta está adentro*/
    list-style-position: outside;
}


.list-3 li{
    background-color: cornsilk;
    list-style: lower-latin inside;
    list-style: lower-latin outside;
    list-style: lower-latin url("../assets/cielo.png")outside;
    list-style: lower-latin inside;
}

.text-column-4{
    list-style-position: inside;
    column-count: 4;
    column-gap: 2rem; /*Separacion entre 2 columnas*/
    column-rule: thin dotted red;
    column-width: 100px;/*tamaño minimo de anchura de las columnas*/
}

.text-column-3{
    column-count: 3;
    column-gap: 1rem; /*Separacion entre 2 columnas*/
    column-rule: thin solid gray;
    column-width: 100px;
}
```

## Estilos de Tablas.

Las tablas hoy no sirven para tabular datos a principios de la web se utilizaba para hacer la maquetacion pero gracias a Flexbox es que ya podemos hacer la maquetacion mas profecionalmente pero cuando tengamos la necesidad de tabular datos las tablas siempre van a ser importantes y hay un par de estilos que podemos aplicar.

> Atajo para hacer tablas. ``table.table>tr*3>td*3``

aplicar borde directamente al alemento html ya está muy depreciado actualmente, para poder aplicar bordes lo debemos hacer a travez de CSS con la propiedad border.

```css
    .table{
    font-size: 3rem;
    border-collapse: separate;/* default || Propiedad exclusiva de la tabla*/
    border-collapse: collapse;
    border-collapse: separate;
    empty-cells: show;/*Default*/
    empty-cells: hide;
    }

    table,
    td,
    th{
        border: medium solid rebeccapurple;
        border-spacing: 1rem; /*es el espaciado que hay entre las celdas*/
    }

    /*tr no tiene sentido aplicar bordes por que son filas*/

    /*Html es muy parecido a escribir en un procesador de texto*/
```

## Estilos de formularios

> _Si tu tienes 2 o mas proyectos en vs code lo que te conviene  es abrir lo en una ventana independiente_

vamos a utilizar: bordes anchos, tamaño de letra  no vamos a ver nuevos atributos de css.
Que pasa para elementos de tipo radio-botones o checkbox o listas, los dichosos selects ese tipo de elementos de formulario son elementos que cuestan darles estilos si visitas [bootstrap](https://getbootstrap.com/docs/5.3/forms/overview/#overview)  verás que sus estilos son muy parecidos a los que hacemos nativamente (o los estilos propios que les da los navegadores) y las mejores animaciones la tiene [materializecss](https://materializecss.com/)

## Formulario de Contacto con CSS

Hay que entender que el formulario es un elemento que trabaja en caja.

Los imputs de formulario trabajan en linea

```css
html{
    box-sizing: border-box;
    font-size: 16px;
}

*,
*::after,
*::before{
    box-sizing: inherit;
}


.contact-form{

    --form-text-color: #666;
    --form-placeholder-color: #006999;
    --form-success-color: #4caf50;
    --form-error-color: #f44336;
    --form-bg-color: #eee;
    --form-border-color: #222;

    background-color: var(--form-bg-color);
    border: thin solid var(--form-border-color);
    margin-left: auto;
    margin-right: auto;
    padding: 2rem;
    width: 80%;
}

.contact-form > *{ /*Todo los elementos del html sin importar su naturaleza*/
 display: block;
 width: 100%;
 margin-bottom: 2rem; /*si el paddin es de 2 rem pel margin-bottom tambien deberia ser de 2rems*/
 font-family: sans-serif;
 font-size: 1rem;
 padding: .5rem;/*espaciado a los elementos de formulario*/
 border-radius: .25rem;
 color: var(--form-text-color);
 caret-color: var(--form-placeholder-color); /*Color del cursor*/
}

/*Estilos a nivel de validaciones*/
.contact-form > *::placeholder{
    color: var(--form-placeholder-color)
}

.contact-form > *[required]:invalid{ /*que tengan un valor invalido (Seudoclase)*/
    border:  thin solid var(--form-error-color);
}

.contact-form > *[required]:valid{ /*que tengan un valor invalido (Seudoclase)*/
    border:  thin solid var(--form-success-color);
}


.contact-form input[type="submit"]{
    margin-bottom: 0;
    margin-left: auto;
    margin-right: auto;
    width: 30%;
    background-color: var(--form-placeholder-color);
    font-weight: bold;
    color: #fff;
}

/*le estoy aplicando pointer en un estado hover*/
.contact-form input[type="submit"]:hover{
    cursor: pointer;
    opacity: 0.75;
}

/*para que ya no se cambie el tamaño de la text area*/

.contact-form textarea{
    resize: none;
}
```

## EFECTOS VISUALES Y MOVIMIENTOS EN CSS.

 Si tu algun momento trabajaste con algun software de diseño llamesé photoshop ilustrator corel drow after efects figma xd, scketch sabes que dentro de los paneles de propiedades de estos softwares. a los elementos que arrastramos hacia el camvas hacia la mesa de trabajo podemos aplicarle un sin fin de efectos como mascaras transformaciones filtros modos de mescla sombras blurs degradados si analizamos todos estos softwares están programados internamente pues cada ves que los softwares se van actualizando van sacando nuevos efectos si lo analisas todo lo que podemos hacer fue programado por alguien y lo mas hermoso es que en el mundo del diseño web podemos hacer todo esos efectos con el código y el lenguaje en el que lo podemos hacer es justamente CSS 

 Pagina recomendada:  https://cssreference.io/ 

 ### Estilos iniciales para nuestro documento.

 receteamos el html en css

 ### Sombras a las cajas (Box-shadow)

 Podemos aplicarle sombras a las cajas y a los textos

 ### Sombras de Textos.

 ### Sombras Multiples.

 ```css
 .shadows-multiple{
    font-size: 2rem;
    text-align: center;
    box-shadow: 1rem 1rem 1rem 1rem #0005, 1rem 1rem 1rem 1rem #f00 inset, -0.5rem -0.5rem 0.5rem 2rem hotpink;
    text-shadow: -1rem -1rem 0.5rem navy, 1rem 1rem 0.5rem greenyellow;
    }
```

### Filtro de sombras.

Todo estos filtros vienen vienen en photoshop, ilistrator incluso en figma, cada uno de sos filtros son funciones.

Este filtro de ``drop-shadow`` va aplicar la sombra a imagenes con trasparencia alfa.

``filter: drop-shadow(1rem 1rem 1rem red);`` aplica sombras el contorno de la imagen PNG(Alpha) no aplica las sombras multiples

``box-shadow``  sombras a la caja. Para CSS las etiquetas html son cajas.

```css
    .drop-shadow{
    width: 600px;
    height: auto;
    }

    .drop-shadow img{
        max-width: 100%;
        height: auto;
        /* filter: drop-shadow(mov-x mov-y blur-radius color); */
        box-shadow: 1rem 1rem 1rem 1rem #f00;
        filter: drop-shadow(1rem 1rem 1rem red); /*muy importante, no vayas a poner comas en la separacion, la coma se utiliza en los efectos múltiples.*/
        filter: drop-shadow(1rem 1rem 1rem green); 
    }
```

### Degradados Lineales.

si quieres utilizar una herramienta para los gradientes puedes usar: [cssgradient](https://cssgradient.io/)

¿Cual es la logica para entender los degradados?

los gradientes trabajan en la propiedad background pero la buena práctica te sugiere que trabajes con ``background-image``

En CSS y vayas a dar un ``grado de 0`` si le tienes que especificar el 0 con la palabra ``deg``

La proporcion de colores es similar ¿que hacemos para que el color abarque un porcentaje determinado? 

Podemos hacer degradados que parescan banderas.

```css
    .linear-gradient{
    background-image: linear-gradient(red, green);
    background-image: linear-gradient(red, green, blue);
    background-image: linear-gradient( 0deg, red, green, blue);/*no es necesario que especifiques 0 vwp, 0px*/
    background-image: linear-gradient( 20deg, red, green, blue);
    background-image: linear-gradient(45deg, red, green, blue);
    background-image: linear-gradient( 90deg, red, green, blue);
    background-image: linear-gradient( 180deg, red, green, blue);
    background-image: linear-gradient( 270deg, red, green, blue); 
    background-image: linear-gradient( 180deg, red, green, blue); 
    background-image: linear-gradient( to right, red, green, blue); /*Tambien lo podemos expresar en palabras*/
    background-image: linear-gradient( to top, red, green, blue); /*el que se va aliniear con la palabra es el ultimo color que hayas definido*/
    background-image: linear-gradient( to left, red, green, blue);
    background-image: linear-gradient( to top left,red, green, blue); 
    background-image: linear-gradient( to top right, red, green, blue);
    background-image: linear-gradient( to bottom right, red, green, blue);
    background-image: linear-gradient( to bottom left, red, green, blue); 
    background-image: linear-gradient( 90deg, red 30%, green, blue);  /*puedes ver que la proporcion de colores es igual*/
    background-image: linear-gradient( 90deg, green 33%, white 34% 67%, red 68%); /*Se sobreentiende que va del 0% al 30% & 68% al 100%*/
}
```

### Degradados Radiales (Radial-gradient)

```css
    .radial-gradient{
    background-image: radial-gradient(cyan, magenta);
    background-image: radial-gradient(cyan, magenta, yellow);
    background-image: radial-gradient(circle 4rem, cyan 30%, magenta 80%, yellow); /*el cuan va ir de 0 a 30 por ciento del radio del circulo*/
    background-image: radial-gradient(circle 100px, cyan 30%, magenta 60%, yellow 90%);
    background-image: radial-gradient(circle 100px at top, cyan 30%, magenta 80%, yellow);/*Tambien podemos especificar donde va ir el centro del radio*/
    background-image: radial-gradient(circle 100px at bottom, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px at left, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px at center, cyan 30%, magenta 80%, yellow); /*Valor por defecto*/
    background-image: radial-gradient(circle 100px at top left, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px at top right, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px at bottom left, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(ellipse 100px 50px, cyan 30%, magenta 80%, yellow); /*Para un radio eliptico debemos definir 2 valores*/
    background-image: radial-gradient(circle 100px at top, cyan 30%, magenta 80%, yellow);
    background-image: radial-gradient(circle 100px, red 50%, white 50%);/*Bandera de Japon*/
}
```

### Degradados cónicos (conic-gradient)

piensa en las manecillas del reloj, las 12 seria como el 0 %

Lo podemos controlar con porcentajes, tambien lo podemos controlar por grados 

```css
    .conic-gradient{
    background-image: conic-gradient(red, green);
    background-image: conic-gradient(red, green, blue);
    background-image: conic-gradient(red 0% 50%, green 60%, blue 80%);
    background-image: conic-gradient(red 0deg 90deg, green 120deg 240deg, blue 270deg);
    background-image: conic-gradient(from 90deg,
    red 0deg 90deg,
    green 120deg 240deg,
    blue 270deg); /*Inicio de los grados va ser a los 90*/
    }
```

### Patrones con degradados.

Hay 3 funciones auxiliares al linear gradient, radial-gradient, & conic-gradient que nos permiten generar patrones visuales.

```css
    .repeat-gradient-linear{
background-image: repeating-linear-gradient(red 0 10px, green 10px 20px, blue 20px 30px);
background-image: repeating-linear-gradient(
    45deg,
    red 0 10px, 
    green 10px 20px, 
    blue 20px 30px);
}

.repeat-gradient-radial{
    background-image: repeating-radial-gradient(circle 4rem, cyan 0 10px, magenta 10px 20px, yellow 20px 30px);
}

.repeat-gradient-conic{
    background-image: repeating-conic-gradient(red 0 8%, yellow 8% 16%, black 16% 24% );
}
```

### Gráficas con degradados.

Ésta seccion es un poco más práctica, te voy a enseñar como con CSS construir un par de efectos 

```css
    .chart-gradient{
    background-image: conic-gradient(cyan 0 50%, magenta 50% 80%, yellow 80%);
    border-radius: 50%;
}


/*Es la union de 2 degradados*/
.donut-gradient{
    background-image: 
    radial-gradient(white 30%, black 31%, transparent 33%),
    conic-gradient(cyan 0 50%, magenta 50% 80%, yellow 80%);
    border-radius: 50%;
}
```

### Filtros (filter)

Estos filtros podemos utilizarlos en softwares como photoshop, ilustrator, incluso softwares de interaccion como Figma,  XD, sketch, que se volvieron muy populares por que aplicaciones como Instagram nos permiten aplicar ciertos filtros

hay una gran cantidad de filtros que podemos aplicar a nuestro CSS  los filtros se aprecian mejor cuando lo aplicamos a una imagen

#### Filtros Múltiples

```css
    .filters-multiple{
    filter: blur(0.10rem) hue-rotate(270deg) opacity(0.75) invert(1);
}

.relative{
    position: relative;
}

```

#### Filtros a fondos

La intencion es poner la DIV en medio de la card(la Imagen) 

> recuerda ver los cursos de flex-box y grid-css que son las tecnicas que te van a permitir dominar y maquetar y controlar todo los procesos de maquetacion.

sobre el color de fondo con cierta opacidad un Blur. por que visualmente se ve muy bien

La gente que tiene fundamento y teoria de diseño entendiendo la teoria del color le puede sacar mucho provecho.

```css


.backdrop-filter,
.backdrop-filter-multiple{
    position: absolute; /*Pierde sus propiedades asi que busca a su contenedor padre*/
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}


.backdrop-filter h4{
    border-radius: 1rem;
    padding: 2rem;
    font-size: 3rem;
    color: #000;
    background-color: rgba(255, 102, 255, 0.5);
    background-color: rgba(255, 255, 255, 0.5);
    backdrop-filter: grayscale(1);
    backdrop-filter: sepia(1);
    backdrop-filter: opacity(0.25);
    backdrop-filter: hue-rotate(180deg);
    backdrop-filter: blur(0.5rem);
}

.backdrop-filter-multiple h4{
    border-radius: 1rem;
    padding: 2rem;
    font-size: 3rem;
    color: #fff;
    background-color: rgba(255, 102, 255, 0.5);
    backdrop-filter: blur(1rem) hue-rotate(240deg) opacity(0.75) invert(1);
}
```


Te voy a enseñar una tecnica el cual podemos usar un filtro en particular para hacer el tema oscuro y tema claro


### Modo Dark/Light


```css
    .dark-mode{
    background-color: #fff;
    color: #000; /*para que funcione debemos poner color de texto y color de fondo los colores que le pone el navegador no valen*/
    filter: invert(1);
}

.dark-mode img{
    filter: invert(1);
}
```

La desventaja es que afecta a los elementos hijos, toda imagen que pongas se va ver afectada por la inversion de filtros, no es la mejor opcion.

### Modos de mescla. (mix-blend-mode)

El efecto de los bland-modes lo debemos a plicar directamente a las imagenes no a su contenedor padre CARD

```css
    .blend-modes img{
    mix-blend-mode: normal;
    mix-blend-mode: color;
    mix-blend-mode: color-dodge;
    mix-blend-mode: color-burn;
    mix-blend-mode: screen;
    mix-blend-mode: multiply;
    mix-blend-mode: saturation;
    mix-blend-mode: luminosity;
    mix-blend-mode: hue;
    mix-blend-mode: exclusion;
    mix-blend-mode: difference;
    mix-blend-mode: hard-light;
    mix-blend-mode: soft-light;
    mix-blend-mode: lighten;
    mix-blend-mode: darken;
    mix-blend-mode: overlay;
}
```
es necesario comentar, ya que por cascada aplica todo los modos de mescla y puede que baje el rendimiento de la página.

### Modos de Mezcla a Fondos (background-blend-mode)

Esta propiedad se utiliza para controlar cómo se mezcla una imagen de fondo con el color de fondo de un elemento.

se aprecia mejor en imágenes.

>- ``**RECUERDA: la Propiedad background-blend-mode tiene varios operadores o Valores**``

> EJ: cover es un valor utilizado para la propiedad background-size.

 ```css
   .bg-blend-modes{
    background-image: url("../assets/planeta-tierra.jpg"), url("../assets/fuso-5t.jpg");
    background-size: cover; /*ajusta el tamaño de las imagenes a al tamaño de la CARD*/
    background-blend-mode: normal ;
    background-blend-mode: color;
    background-blend-mode: color-dodge;
    background-blend-mode: color-burn;
    background-blend-mode: screen;
    background-blend-mode: multiply;
    background-blend-mode: saturation;
    background-blend-mode: luminosity;
    background-blend-mode: hue;
    background-blend-mode: exclusion;
    background-blend-mode: difference;
    background-blend-mode: hard-light;
    background-blend-mode: soft-light;
    background-blend-mode: lighten;
    background-blend-mode: darken;
    background-blend-mode: overlay;

    /* background-blend-mode: multiply; */
    
} 
 ```


### Enmascaramiento

Consiste en mostrar parte de la imagen

hay heramientas para generar poligono [clip-path](https://bennettfeely.com/clippy/)

```css
    .clip-path{/*Puede hacer uso de 4 funciones.*/
    clip-path: circle(); /*puede servirme para fotos de perfil*/
    clip-path: circle(5rem);
    clip-path: circle(100px);
    clip-path: circle(100px at top);
    clip-path: circle(100px at left);
    clip-path: circle(100px at bottom);
    clip-path: circle(100px at left bottom); /*podemos hacer combinaciones: izquierda a abajo*/
    clip-path: circle(100px at right top);
    clip-path: circle(100px at 0 0); /*moverlo por coordenadas*/
    clip-path: circle(100px at 30%); /*lo coloca al 30% de la targeta*/
    clip-path: circle(100px at 32% 26%);
    clip-path: ellipse();
    clip-path: ellipse(rem 1rem);
    clip-path: ellipse(200px 100px at left);/*moverlo a:*/
    clip-path: ellipse(200px 100px at right);
    clip-path: ellipse(200px 100px at top);
    clip-path: ellipse(200px 100px at bottom);
    clip-path: ellipse(200px 100px at left bottom);
    clip-path: ellipse(200px 100px at right bottom);
    clip-path: ellipse(200px 100px at left top);
    clip-path: ellipse(200px 100px at right top);
    clip-path: ellipse(200px 100px at 0 1);
    clip-path: ellipse(200px 100px at 300px 50px);
    clip-path: ellipse(200px 100px at 32% 26%);
    clip-path: inset(2rem); /*si o si hay que ponerle valores*/
    clip-path: inset(2rem); /*es como si le colocara padings a todo los lados*/
    clip-path: inset(2rem 1rem);
    clip-path: inset(3rem 2rem 1rem);/*top rigth bottom lefth*/
    clip-path: inset(1rem round 1rem);
    clip-path: inset(1rem round 1rem 2rem);
    clip-path: inset(1rem round 1rem 2rem 3rem); /*como la mancillas del reloj*/
    clip-path: inset(1rem round 1rem 2rem 3rem 4rem);
    clip-path: polygon(0 0, 100%.0, 50% 100%);  


    clip-path: polygon(0% 15%, 15% 15%, 15% 0%, 85% 0%, 85% 15%, 100% 15%, 100% 85%, 85% 85%, 85% 100%, 15% 100%, 15% 85%, 0% 85%);
    clip-path: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
}
```

### Formas (Shape-outside)

Para que las imágenes se vayan fucionando con los parrafos vamos hacer que las 3 imágenes floten.

La flotacion nace para que podamos convivir entre los elementos con nuestro contenido.

Gracias a las formas yo puedo hacer que el texto se adapte como al circulo de la imagen

Ya que trabaja con porcentajes solo se preucupan por las dimenciones de las imágenes (Cuadradas o rectangulares)

Estó te puede servir en una típica seccion informativa donde te cuentan la historia de la empresa, o una breve descripcion de los integrantes de la compañia así que el avatar de la fotografia de la persona y al costado sus datos

```css

    .shapes {
    border: thick solid black;
    padding: 1rem;
    margin: 0 auto 5rem;
    max-width: 800px;
    /* font-size: 1.25rem; */
}

.shapes img{
    border-radius: 50%;
    width: 200px;
    height: 200px;
    object-fit: cover;
    object-position: 0 50%;
}

.float-left{
    float:left;
}

.float-right{
    float: right;
}


.shape-1{
    margin: 4rem 2rem 4rem 0;
shape-outside: circle();
shape-outside: circle(5rem);
shape-outside: circle(); /*Es mejor no poner valores por que el texto ya que el texto se sobrepone a la imagen*/
shape-outside: ellipse();
shape-outside: polygon(50% 0%, 61% 35%, 98% 35%, 68% 57%, 79% 91%, 50% 70%, 21% 91%, 32% 57%, 2% 35%, 39% 35%);
shape-outside: circle(); 
}

.shape-2{
    margin: 4rem 0 4rem 2rem;
    shape-outside: ellipse();
}

.shape-3{
    margin: 2rem 8rem 0 0;
    shape-outside: polygon(50% 0%, 100% 50%, 50% 100%, 0% 50%); /*nos ayudamos de la herramienta: https://bennettfeely.com/clippy/*/
}
```

### Sitio One Page Scroll (scroll-margin & scroll-behaivor)

maquetacion par un sitio de una sola página.

El ``position: sticky;`` 

Al hacer click al enlace la seccion comienza desde donde comienza la etiqueta Section. y lo pone a top 0 de la página, entonces ese es uno de los detalles cuando hacemos sitios de una sola página.

hay 2 soluciones, ponerle mas padding o 

> cuando estan haciendo sitios que van en una página y los enlaces son anclas internas (enlaces internos )

la mejor solucion es con una propiedad llamada: `Scroll margin top` reduce el tamaño en lugar de poner ids  en top 0 de la página entonces lo pondria a la distancia que nosotros le indiquemos

Podemos darle animacio al momento de cambiar las secciones: para eso hay que ir al documento html(es el que se está desplazando) nosotros le podemos dar  una propiedad `scroll-behavior: smooth;` (Comportamiento del Scroll) Smoot hace referencia a un desplazamiento mas suave estó antes se programaba en javascript


```css
    html{
    box-sizing: border-box;
    font-size: 16px;
    font-family: sans-serif;
    scroll-behavior: smooth;
}

*,
*::after,
*::before{
    box-sizing: inherit;
}


body,h1,h2{
    margin: 0;
}


img{
    max-width: 50%;
    height: auto;
}

/*a todo los elementos de esta página  aplica un scroll || el valor de un EX es la mitad de un rem o Em */

[id]{
    scroll-margin-top: 7.8ex; /*un EX es la midad de un Rem o Em*/
}


.header{
    position: sticky;
    top: 0;
    padding: .25rem;
    /* height: 4rem; */
    text-align: center;
    background-color: #000;
    color: #fff;
}

/*estilo a los enlaces */
.header a{
    margin: 0 1rem;
    color: #00c4d6;
}

.header a:hover{
    margin: 0 1rem;
    color: #e94bb4;
}

.slide{
    width: 100%;
    min-height: 100vh;
    color: #d9e8f0;
    background-color: #1e2345;
    /* padding: 4rem; */
    padding: 2em;/*Dos rems a los 4 lado se vé Mejor*/
}

.slide:nth-child(even){
    background-color: #108eb4;
}
```