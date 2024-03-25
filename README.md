

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

La función CSS fija un valor medio dentro de un rango de valores entre un límite mínimo definido y un límite máximo. La función toma tres parámetros: un valor mínimo, un valor preferido y un valor máximo permitido.clamp()

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
/*impares*/
.slide:nth-child(even){
    background-color: #108eb4;
}
```

### Ajustes del Scroll Efecto Slides Vectoriales (scroll-snap-type & scroll-snap-align)

Para no hacer la tipicas aburidas presentaciones con PowerPoint. 😂😂 Sorprende a tus amigos

Snap: es el ajuste del desplazamiento que podemos hacer, y eso te va permitir hacer presentaciones.

en el proximo curso te voy a enseñar las buenas prácticas: como los nombres que debes poner a tus clases, como debes escribirlos, como ordenar si tu hoja de estílo se hace muy grande

> Tiene que tener una altura al tamaño del viewport

> El ajuste del scroll puede hacerlo en horizontal como en vertical.

> La propiedad que hace el efecto de slide al solo precionar el raton se llama: **scroll-snap-type** recibe 2 valores:

>- El primer valor: que eje quieres controlar, podemos poner el valor de X. el valor de Y, el valor de Inline, Block, y Both Si quieres controlar al desplazamiento en X pon X o el eje Inline. Pudes poner Y  o la palabra Block para controlar el Scroll Vertical y pones la palabra recerbada Both, quiere decir que quieres controlar tanto el eje X como el Y.

>- El segundo valor: hay 2 subvalores que pudes poner: Mandatory(obligatoria) Proximity tiene que estár mas hacia la siguiente diapositiva

>- `El contenedor debe cumplir con una altura definida`

>- `Con la propiedad Overflow en el eje que quiero controlar con el valor Scroll`

>- `Con la propiedad Scroll-Snap-type activada`


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

body{
    margin: 0;
}


/*Mandatory es mas sensible y Proximity es menos sensible */
.slides{
    width: 100%;
    height: 100vh; /*si o si debe ser del tamaño del viewport*/
    overflow-y: scroll;/*el eje donde querramos controlar el ajuste del scroll la propiedad over flow tiene que tener si o si el valor de Scroll*/
    /* scroll-snap-type: [x|y|inline|block|both][mandatory|proximity]; Estes son los valores que toma esa propiedad */
    scroll-snap-type: none;
    scroll-snap-type: block mandatory;
    scroll-snap-type: y mandatory;
    scroll-snap-type: block mandatory;
    scroll-snap-type: block proximity;
    scroll-snap-type: block mandatory;
    scroll-snap-type: both mandatory; /*controla tanto en X como en Y*/
}


.slide{
    width: 100%;
    height: inherit; /*heredamos al altura*/
    background-color: #1e2345;

    scroll-snap-align: none; /*tambien deben tenr esta propiedad la Slide.*/
    scroll-snap-align: end;
    scroll-snap-align: start;
    scroll-snap-align: center;
}

.slide:nth-child(even){
    background-color: #108eb4;
}


.slide-container{
    width: 100%;
    width: 80%;
    height: inherit; /*hereda la altura, si queremos que se ajuste a la altura de su contenedor  cada una de las Slides tendria que heredar la altura de su contenedor*/
    margin: 0 auto;
    display: flex; /*Flexbox  por defecto su direccion empieza en fila*/
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 3vw; /*El tamaño de fuente es de 3% a la anchura de la pantalla*/
    color: #d9e8f0;
}
```
### Ajustes del Scroll Efecto Carrusel Horizontal(scroll-snap-type & scroll-snap-align)

Puede servir para hacer carruseles que no estén controlados con JS. el contenido puede ser textos o imágenes.

para hacer el efecto de Scroll-snap hay que cumplir 3 reglas.

>- El contenedor de las Slides debe tener una altura o anchura bien definida.

>- Una propiedad overflow en el eje que quiero controlar Scroll

>- La declaracion de la propiedad ``Scroll-Snap-type`` (las hijas del contenedor necesita tener la propiedad de ``Scroll-snap-align``)

¿Por que necesito dos contenedores?

el contenedor "carousel" va enmascarar el contenido si no lo enmascaro va generar un scroll una barra de scroll horizontal

```css
    /*estilos a nuestro selector carrusel para que oculte el desbordamiento*/

.carousel{
    border: thick solid #d938f0;
    display: flex; /*es más, hace que herede la altura*/
    width: 50%;
    height: 50vh;
    overflow-x: hidden;
}

.carousel-container{
    width: 100%;
    display: grid;
    grid-template-columns: repeat(5, 100%);
    overflow-x: scroll; 
    overflow-y: hidden;/*para evitar barra de Scroll horizontal O PUEDEN PONER AUTO*/
    scroll-snap-type: x mandatory; 
    scroll-snap-type: x proximity;
    scroll-snap-type: inline mandatory; /*inline o x son valores similares*/
    scroll-snap-type: both mandatory; /*hace referencia a  X y Y*/
    scroll-snap-type: both proximity;
}   

.carousel-slide{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: #108eb4;
    scroll-snap-align: none;
    scroll-snap-align: start;
    scroll-snap-align: end;
    scroll-snap-align: center;
}

.carousel-slide:nth-child(even){
    background-color: #1e2345;
}
```
### Textos con Degradado.

las propiedades que nos permiten hacer que el texto herede el degradado del fondo no están bien soportadas entonces debemos hacer los prefijos del navegador

lo ideal es que crearas una clase y se la agregarás solamente a los parrafos que quieras pintar

cuando lleguemos al curso de responsive CSS  en la parte de arquitectura CSS les voy a enseñar algunas herramientas cuando ya organizes y automatizes tus hojas en cascada va ver herramientas como autoprefixer.

```css
    .gradient-text{
    background-image: linear-gradient(45deg, magenta,  yellow);
    -ms-background-clip: text;
    -moz-background-clip: text;
    -webkit-background-clip: text;
    background-clip: text; /*este es el nuevo valor que no está soportado al 100%*/
    -ms-text-fill-color:transparent; /*está es una nueva propiedad: cuando estén bien soportadas ya no vamos a tener la necesidad de aplicar estós prefijos*/
    -moz-text-fill-color:transparent;
    -webkit-text-fill-color:transparent;
}
```

## Movimientos en CSS

Se trata de como hacer tranciciones transformaciones y animaciones.

Para el movimiento hay 3 temas principales que vamos a trabajar: tranciciones transformaciones y animaciones.

### Transiciones.

como voy a estar utilizando tanto en animaciones  transformacionescomo transiciones cajas y targetas estan en una seccion con la clase transition.

Dependiendo de cuantas transiciones tenga, el navegador va tardar un poquito, usar ALL no es mala práctica, sino aplicar cambios a u mismo elemento. Nada con ecceso todo con responsabilidad "un gran poder conlleva una gran responsabilidad".

Aplicar ALL tiene un pequeño detalle, imagínate que a cada una de las propiedades: background-color, border-radius yo quisiera que las transiciones para cada propiedad se dieran con diferentes funciones de aceleración y con diferentes tiempos entonces el ALL ya no me sirve por que estoy diciendo: todo los cambios los voy hacer uniformemente en dos segundos con la misma funcion de transicion EASE-IN-OUT 

```css
    /*Transiciones HAY varias propiedades:
    transition-property
    transition-duration
    transition-timing-function:none, linear, ease, ease-in, ease-out, ease-in-out steps
    transition-delay
    transition: property duration timing-function delay
    https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties
    */
    .transitions .box{
        background-color: magenta;
        transition-property: background-color; /*propiedad que quiero modificar*/
        transition-duration: 500ms;
        transition-timing-function: ease;
        transition-delay: 0.25s;
        transition: border-color 2s linear 1s; /*El short hand reemplaza todo lo anterior definido.*/
        transition: all 2s ease-in-out 250ms; 
    }

    /*Para ver las transiciones es importante definir un estado hover*/

    .transitions .box:hover{
        background-color: cyan;
        border-color: red;
        border-radius: 2rem     ;
    }
```


### Propiedades Animables

segun la documentación de: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties toda las propiedades son animables ¿Contradicción.?


 ```css
 
    .transitions .box:hover{
    background-color: cyan;
    border-color: red;
    border-radius: 2rem;
    /*border-style: dashed; /*Esta propiedad no es animable*/
}
 ```

 ### Transiciones Multiples

 ¿Como es que tu puedes ir aplicando diferentes tiempos y diferentes funciones de transicion a cada una de las propiedades?
 
 ```css
    .transitions .card{
    /* transition: all 2s ease; */ /*para evitar que la transicion sea súbita*/
    transition: opacity 1s ease-out,
        border-color 3s steps(3),/*Sigue 3 pasos*/
        filter 2s ease-in 1s,/*delay un segundo*/
        box-shadow 1.5s linear 2s; 
}


.transitions .card:hover{
    opacity: 0.75;
    border-color: orchid;
    filter: blur(0.15rem);
    box-shadow: 1rem 1rem 2rem 0.5rem #000;
}

.transitions .card img{
    transition: object-position 2s ease-in-out 3s;
}

.transitions .card img:hover{
    object-position: 100% 50%; /*hace el movimiento de la imagen hasta el final.*/
}
 ```

 ### Por que no usar la palabra all en tus transiciones.

 es mentira que baja el rendimiento, por que tendrias que tener mas de 25 cambios de transiciones en un solo elemento ¿pero por que es una mala practica usar ALL? cuando le decimos transition all le estamos diciendo que haga transicion de toda las propiedades, si tu no tienes el contros al 100% de las propiedades que vas a animar entonces si es una mala práctica ALL por que no solamente está haciendo cambio en el estado hover sino tambien la está haciendo en la caja "box" por eso es una mala práctica usar el transition ALL porque cuando cargue tu interfaz web todo los elementos que tengan un transition all vas a ver como se animam.

 las transiciones son una propiedad de CSS y al regirse por el algoritmo de CSS pues estas propiedades son afectadas por la cascada por la especificidad y por la herencia

 ### El algoritmo de CSS y su efecto sobre las transiciones.

 es un error frecuente cuando participo en proyectos que tiene transiciones y que las transiciones de la nada cuando cargas el navegador se empiezan a animar  y es por que la gente no entiende que cuando tu declaras una propiedad en la lista de transiciones que vas a ejecutar esa transicion no solamente se va dar en el cambio, en el estado  que tu le ayas definido como en este caso el hover, sino tambien va a acuar a la hora que cargas la propiedad en el navegador

 transition al ser una propiedad de CSS trabaja bajo las reglas del algoritmo de CSS

 >- `1. Cascada`

 >- `2. Especificidad`

 >- `3. Herencia`

 esta recarga solo aplica para css que no está siendo ejecutada en un entorno de servidor. por que en mi caso solo se aplica la primera vez esa transicion y ahi se queda.


 ```css
    .box{
    border: thick solid black; /*short hands*/
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 5rem;
    width: 200px;
    height: 200px;
}

.card{
    border: thick solid black;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 5rem;
    width: 600px;
    height: 400px;
}

.card img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: 40% 50%;
}

.transitions .box{
    background-color: magenta;
    border-color: green;
    transition-property: background-color; /*propiedad que quiero modificar*/
    transition-duration: 500ms;
    transition-timing-function: ease;
    transition-delay: 0.5s;
    transition: border-color 2s linear 1s; /*El short hand reemplaza todo lo anterior definido.*/
    transition: all 2s ease-in-out 250ms;
    transition: background-color 2s ease-in-out 250ms, /*se activa al momento de recargar el navegador*/
                border-color 2s ease-in-out 250ms,
                border-radius 2s ease-in-out 250ms ;
}

/*Para ver las transiciones es importante definir un estado hover*/

.transitions .box:hover{
    background-color: cyan;
    border-color: red;
    border-radius: 2rem;
    border-style: dashed; /*Esta propiedad no es animable*/
}

.transitions .card{
    /* transition: all 2s ease; */ /*para evitar que la transicion sea súbita*/
    transition: opacity 1s ease-out,
        border-color 3s steps(3),/*Sigue 3 pasos*/
        filter 2s ease-in 1s,/*delay un segundo*/
        box-shadow 1.5s linear 2s; 
}


.transitions .card:hover{
    opacity: 0.75;
    border-color: orchid;
    filter: blur(0.15rem);
    box-shadow: 1rem 1rem 2rem 0.5rem #000;
}

.transitions .card img{
    transition: object-position 2s ease-in-out 3s;
}

.transitions .card img:hover{
    object-position: 100% 50%;
}

 ```


### Transformaciones en 2D

Tenemos dos tipos de transformaciones en 2D y en 3D, hay 4 transformaciones en dos dimenciones que son las mas conocidas y en cualquier software de interfaz de usuario como : Figma, AdobeXD, Sketch software de diseño commo photoshop e ilustrator los encuentras pero que en softwares de diseño de efectos visuales como After Efects o como Animate (antiguo Flash) que es una suit de Adobe.

Los cuatro movimientos son:

1. traslacion en X y Y
2. Rotacion iz y der
2. Escala (aumentar tamaño en X o Y o hacerlo proporcionalmente)
4. Sesgar skiw

para poder ver los estilos del hover lo debemos activar en el navegador así:

![imagen de activacion del hover](/assets/activar-hover.JPG)

```css
    /*Transfomacion en 2D*/
.transform-2d img{
    transition: transform 2s ease-in-out; /*voy aplicar una transicion a la propiedad transform que dure 2s y que sea con un efecto de aceleracion ease-in-out*/
}

.transform-2d img:hover{
    transform: none;
    transform: translateX(4rem);
    transform: translateY(4rem);
    transform: translateY(-4rem);
    /* transform: translateY(-4rem); */
    transform: translate(-4rem, 4rem); /*Short hands el primer valor es para X y el segundo valor es para Y*/
    transform: translate(50%, 50%); /*tomaria como referencia el tamaño del objeto*/
    transform: translate(50%, 100px);
    /*Escala lo agranda a un lado*/
    transform: scaleX(2);
    transform: scaleY(.5);
    transform: scaleZ(1.5); /*no se va ver por que Z es el eje de profundidad*/
    transform: scale(1.5, 1.5);/*Short handed  X Y*/
    transform: scale(-1, -1); /*invierte la imagen*/
    /*Rotar una imagen*/
    transform: rotateX(90deg); /*el valor tiene que ser en grados, radianes  la rotacion en X es una transformacion en 3 dimenciones para poderla a preciar correctamente*/
    transform: rotateY(60deg);
    transform: rotateY(90deg);/*hace que la imagen se desaparesca por que solo se ve su lado*/
    transform: rotateZ(60deg);/*va en sentido de las manezillas del reloj*/
    transform: rotateZ(-60deg);
    transform: rotateZ(360deg);
    transform: rotate(360);/*SHORT HANDED trabaja en función a Z*/
    /*Sesgar*/
    transform: skewX(20deg);
    transform: skewY(20deg);
    transform: skewY(20deg);
    transform: skew(20deg, 20deg); /*El primer valor es para X y el segundo valor es para Y*/

}
```


### Transformación  Matrix 2D

Tiene cierta complejidad por que hay ciertos calculos matemáticos detras de ella

https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/matrix 


```css
.transform-2d img:hover{
     /*matrix(scaleX(), skewY(), skewX(), scaleY(), traslateX(), traslateY())*/

    transform: matrix(1,2,2,1,20,10); /*tiene que ver con cálculos matemáticos*/
    transform: matrix(1, 2, -1, 1, 80, 80);
}
```

### Transformaciones 2D Múltiples

```css
.transform-2d img:hover{
    /*Transformaciones 2D Múltiples son separados por espacios en blanco y en el orden que quieres ejecutar las transformaciones*/
    transform: translate(25%, -50%);
    transform: translate(25%, -50%) rotate(240deg) skew(10deg, 20deg) scale(-0.5, -0.5);
}
```

### Activando la Perspectiva 3D

recuerdem que la web es un espacio bidimencional si podemos aplicar cierta perspectiva de mostrar las 3 dimenciones pero como tal es una ilucion visual.

¿Cómo podemos aplicar la perspectiva?
directamente ponemos perspective al lado del transform o directamente al elemento padre.

si no activas las perspectivas no va funcionar las transformaciones en 3D

```css
    /*TRANSFORMACIONES EN 3D*/
.transform-3d{
    perspective: 10rem;
}

.transform-3d img{
    transition: transform 2s ease-in-out;
}

.transform-3d img:hover{
    transform: translateZ(4rem);
    transform: perspective(1000px) translateZ(4rem);
    transform: perspective(100rem) translateZ(4rem);
    transform: perspective(1rem) translateZ(4rem);
    transform: translateZ(4rem);
    transform: translateZ(-4rem);
}
```

### Transformaciones en 3D

la documentación: https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate3d

>- recuerda la barra de Scroll sempre va abajo y hacia la derecha entonces las imágenes con rotacion z a 90deg se va a perder pero si funciona al lado de la derecha

el sesgo no hay en 3 dimenciones.

### Transformacion Matrix 3D 

la documentacion https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/matrix3d

la web es un cambas es un lienzo de 2 dimenciones

### transformaciones 3D múltiples

```css
    /*TRANSFORMACIONES EN 3D*/
.transform-3d{
    perspective: 10rem;
}

.transform-3d img{
    transition: transform 2s ease-in-out;
}

.transform-3d img:hover{
    transform: translate3d(2rem, 50%, -3rem);
    transform: scaleZ(1.5); /*la imagen no tiene volumen asi que no se puede apreciar estos cambios*/
    transform: scale3d(2, 0.5, 3);
    transform: rotateX(60deg);
    transform: rotateX(90deg);
    transform: rotateY(60deg);
    transform: rotateY(-90deg);
    transform: rotate3d(1,1,1,45deg);/*hace referencia a nodos vectoriales en cada uno de los ejes de la perspectiva 3d*/
    transform: rotate3d(1,0.5,0,-45deg);/*X, Y, Z y un angulo de inclinacion*/
    transform: rotate3d(-1,2.5,-2,60deg);
    /*matriz de 4*4*/
    transform: matrix3d(1,0,0,0,0,1,6,0,0,0,1,0,50,100,0,1.1);

    /*Transformaciones múltiples*/
    transform: rotate3d(-1, 2.5, -2, 60deg);
    transform: rotate3d(-1, 2.5, -2, 60deg) translate3d(2rem, 50%, -3rem) scale3d(2, -0.5, 3);
}
```

### Origen de Transformación (Transform-origin)

Hay una propiedad que dentro de las transformaciones define el **punto de origen** desde donde va partir la transformacion ya sea un skew un sesgo una rotacion una escala una traslacion. El origen es el centro.

Es como en cualquier software de animacion. aplica sobre cualquiera transformacion ` Traslacion, sesgo, rotacion, escala y las 3d` 

```css

    /*Punto de Origen*/
.transform-origin img{
    transition: transform 2s ease-in-out;
    /*transform-origin:x y z; /*Puede recibir hasta 3 valores*/
    transform-origin: 50% 50% 0;
    transform-origin: 0 0;
    transform-origin: 0;/*si solo das un valor aplica para X y Y*/
    transform-origin: top left;
    transform-origin: top right;
    transform-origin: top center;
    transform-origin: bottom center;
    transform-origin: bottom left;
    transform-origin: bottom right;
    transform-origin: center right;
    transform-origin: center left; /*Recuerda! el primer valor es para el eje X y el segundo valor es para el eje Y*/
    transform-origin: center center;
    transform-origin: -2rem -3rem;/*Tambien prodiamos darle valores como: rems, px, %*/
    transform-origin: 2rem 3rem;
    transform-origin: 25% 75%;
    transform-origin: -5% -5%;
    transform-origin: 30%; /*Y sigue girando en su mismo centro*/
    transform-origin: 30% 90%;
}

.transform-origin img:hover{
    transform: rotate(360deg);
}
```

###  Flip Cards con transiciones y transformaciones

Este es una targetita que tiene 2 caras.

vamos a dar estilos muy similar a las targetas anteriores.

back face visibility determina la visualizacion de las caras. cuando tu tienes un elemento de interfaz que va tener como dos lados.

> Recuerda, la propiedad transform-style:; cuando sea padre y que los hijos preserven esa perspectiva debemos de activarlo.

```css
    /*Flip cards*/

.flip-card-1,
.flip-card-2{
    border: thick solid black;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 5rem;
    width: 600px;
    height: 400px;


    position: relative;
    cursor: pointer;
    transition: transform 1s ease-in-out;
    perspective: 10rem;
     /*  si lo hijos de un elemento tienen perspectiva en tres dimenciones, 
     establece el comportamiento en el espacio 3d,
      el valor por defecto es FLAT
      es decir que sobre el mismo plano trabaje los elementos hijos pero si nosotros queremos que los hijos
      de manera independiente tengan su propia perspectiva adicional a la del padre entonces debemos activar 
      una propieda que se llama: preserve-3d*/
      transform-style:flat ;
      transform-style: preserve-3d ; /*Hace que los elementos hijos tengan su perspectiva independiente eso significa que a las Flip face ya ahorita puedo darles una transformacion en 3d entonces ya se acoplarian*/
}


.flip-card-2{
    transform-origin: center right;
}


.flip-card-1:hover{
    transform: rotateY(180deg);
}

.flip-card-2:hover{
    transform: translateX(-100%) rotateY(-180deg);
}


.flip-card-1 img,
.flip-card-2 img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: 55% 45%;
}


.flip-face{
    position: absolute; /*Como no encuentra un contenedor padre relativo se va posicionar respecto del body le agregamos la propiedad relative al padre*/
    width: 100%;
    height: 100%;
    backface-visibility: visible;/*Este es el valor por defecto*/
    backface-visibility: hidden; /*Esta propiedad no tiene efectos sobre transformaciones en dos dimenciones eso significa que necesitamos al prespectiva activada*/
}

.flip-front{
    transform: rotateY(0deg);
}

.flip-back{
    transform: rotateY(180deg);
}
```

### Animaciones.

no tiene sentido pausar una animacion desde CSS 

**`play-state`**
su utilida practica sirve para pausar una animacion.
¿Cuando te conviene pausar una animacion? con javaScript.

si te gusta esto de la animacion podrias complementarlo viendo y probando el software Animete de adobe premier (antes se llamaba Flash) y exportarlo a html, y js.

El lenguaje de programacion que entiende el software Animate es ActionScript que es muy parecido a Js.

```css
    @keyframes myAwesomeAnimation {
    /*debemos poner el fotograma inicial
    Y podemos meter tantas propiedades como querramos pero hay un link donde nos muestra las 
    propiedades que no son animables
    */
    from {
        opacity: 0;
        transform: translateX(0);
    }
    to {
        opacity: 1;
        transform: translateX(100%);
    }
}
.my-animation{
    /*animation: name duration timing-function delay iteration-count direction fill-mode play-state; /*estas son toda las propiedades que existen de la animacion*/
    /*de estas 8 propiedades las mas importantes son NAME y animacion. las otras son opcionales*/

    animation-name: myAwesomeAnimation;
    animation-duration: 3s;
}
```

### Propiedades de Animación en CSS

`animation: name duration timing-function delay iteration-count direction fill-mode play-state;`

[cubic-bezier(1,0,0,1)](https://cubic-bezier.com/) representa una linea de aceleracion en la animacion

```CSS
    .my-animation{
    /*OBLIGATORIAS*/
    animation-name: myAwesomeAnimation;
    animation-duration: 3s;
    animation-duration: 2s;
    /*Aceleracion*/
    animation-timing-function: cubic-bezier(1,0,0,1);
    animation-timing-function: cubic-bezier(.73,0,.95,.29);
    animation-timing-function: ease-in-out;
    /*Retraso que va tener tu animacion*/
    animation-delay: 1500ms;
    animation-delay: 0ms;
    /* número de veces que se hará la animación*/
    
    animation-iteration-count: 3;
    animation-iteration-count: infinite;
    animation-iteration-count: 1;
    /*direccion*/
    animation-direction: normal;
    animation-direction: reverse;
    animation-direction: alternate; /*hace la animacion del punto inicial al punto final y regresa del punto final al punto inicial*/
    animation-direction: alternate-reverse;
    animation-direction: normal;
    /*Al final de la animacion se queda con los estílos finales de la animacion
        Cuando tengan la necesidad de que un elemento se quede con los estilos que definieron en el último fotograma de la animacion    
    */
    animation-fill-mode: none; /*por defecto*/
    animation-fill-mode: forwards;
    /* Al inicio de la animacion se queda con los estilos iniciales de la animacion */
    animation-fill-mode: backwards; /*evita los saltos viusales*/

    /*si quieres tener las ventajas del forwards y del backwards
    
    both aplica al mismo tiempo el valor de fowards y backwards
    */ 
    animation-fill-mode: both; /*conserva los estilos de inicio y de final de la animacion*/
    animation-play-state: running ;/*por defecto*/
    animation-play-state: paused;/*no tiene sentido en css pero si tiene sentido en javaScript*/
    animation-play-state: running;

    /*En el shorthand animation podria utilizar toda las propiedades*/
    animation: myAwesomeAnimation 1.5s ease 250ms 7 alternate both running;
    animation: myAwesomeAnimation 1s;


}
```

### Linea de tiempo y fotogramas claves en CSS

¿Que pasa si yo necesito meter fotogramas intermedios?

en css la linea de tiempo va funcionar por porcentajes

css va adaptar la proporcion de fotogramas por segundo en base al tiempo que tu le des de animación.

```css
    /*En caso de que tengas fotogramas claves intermedios, la linea de tiempo lo debes ver como porcentajes de 0  a 100(el fotograma final)*/
@keyframes myAwesomeAnimation2 {
    /* from{

    }
    to{

    } */

    /*SUMADOS harian 101 fotogramas clave*/
    0%{
        opacity: 0;
        
    }
    50%{
        opacity: 0.5;
        transform: translateX(-50%);
    }

    75%{
        transform: translateX(-75%);
    }
    100%{
        opacity: 1;
        transform: translateX(100%);
    }
}
.my-animation-2{
    animation: myAwesomeAnimation2 2s;
    animation: myAwesomeAnimation2 5s;
    animation: myAwesomeAnimation2 1s;
    animation: myAwesomeAnimation2 6s; /*a mayor tiempo tenga tu animacion mas lenta se pondrá*/

}
```

imagen de toyota https://www.toyota.com.gt/caracteristicas/caracteristicas-de-toyota-land-cruiser-pickup 

### Animaciones Multiples

lo importante es separarlos por comas

```css
    @keyframes multipleAnimation1 {
    0%{
        opacity: 1;
        
    }
    50%{
        opacity: 0;
    }

    100%{
        opacity: 1;
    }
}

@keyframes multipleAnimation2 {
    0%{
        transform: translateY(0);
        
    }
    50%{
        transform: translateY(-100%);
    }

    100%{
        transform: translateY(0);
    }
}

.animation-multiple{
    animation: multipleAnimation1 2s infinite;
    animation: multipleAnimation2 2s infinite;
    /*Por cascada está reemplazando las animaciones.  Cuando querramos multiples animaciones  es hacer lo siguiente*/
    animation: multipleAnimation1 2s infinite,
                multipleAnimation2 1s 3 ease-in-out;

}
```

### Efectos Fadein & fadeout
```css
    @keyframes fadeIn {
    0%{
        opacity: 0;
        
    }
    100%{
        opacity: 1;
    }
}

.fade-in{
    font-size: 5vw;
    animation: fadeIn 2s linear 2s infinite alternate both; /*el nombre de la animacion es "fadeIn" que dure 2 segundos que sea con una aceleracion lineal */
}

@keyframes fadeOut {
    0%{
        opacity: 1;
        
    }
    100%{
        opacity: 0;
    }
}

.fade-out{
    font-size: 5vw;
    animation: fadeOut 2s linear 2s infinite alternate both; /*el nombre de la animacion es "fadeIn" que dure 2 segundos que sea con una aceleracion lineal */
}
```

### Efecto shake (Sacudida)

para que la cajita solo aplique para que el efecto del hover solo sobre la tasita

```css
    @keyframes pulse{
    0%{
        transform: scale(1.1);
    }
    50%{
        transform: scale(0.8);
    }
    100%{
        transform: scale(1);
    }
}

.pulse{
    font-size: 5vw;
    animation: pulse 1s linear infinite;
}
```

### Eres el CSS de mi HTML ♥

Mucho del dibujo que se hace en CSS nos ayudamos de los seudoelementos before y after para dibujar ciertas cosas.

```css
    @keyframes heartColor {
    10%{
        background-color: #d00;
    }
}
.heart{
    position: relative;
    margin-left: auto;
    margin-right: auto;
    width: 10vw;
    height: 10vw; /*quiero un cuadrado por eso uso las unidades del VW*/
    /* background-color: #888 ; */
    animation: pulse 1s infinite;
}

.heart::after, /*Usamos los pseudoelementos*/
.heart::before{
    position: absolute;
    content: "";
    left: 5vw;
    top: 0;
    width: 5vw;
    height: 8vw;
    background-color: #a00;
    transform: rotate(-45deg);
    transform-origin: 0 100%;
    border-radius: 5vw 5vw 0 0;
    animation: heartColor 1s infinite;
}

.heart::after{
    left: 0;
    transform: rotate(45deg);
    transform-origin: 100% 100%;
}
```

### Spinner / Loader animado

```css
    /*loader.
    Puedes trabajar en la unidad de medida que se te de la gana.
*/


@keyframes spinner {
    0%{
        transform: rotate(0deg);
    }
    100%{
        transform: rotate(360deg);
    }
}


.spinner{
    /* background-color: purple; */
    width: 5vw;
    height: 5vw;
    margin-left: auto;
    margin-right: auto;
    /* border-radius: 50%; */
    border: 0.5vw solid rgba(0, 0, 0, 0.1);
    border-left-color: #09f;
    animation: spinner 1s ease-out infinite;
}
```

### Botones Animados (maquetación)

En esta seccion aprenderemos algunos efectos para botones animados en le mundo de IUX y IAI (iux y iuai) se conoce como micro-interracciones por que no es que aplique efectos como muy vistosos sinó son algunos pequeños cambios de algunas propiedades en nuestros botones.

En está seccion vamos a enfocarnos en hacer los estilos de los botones y en la otra seccion ya aplicamos las animaciones

Ve la importancia de ir aplicando (utilitie ferst) que cada clase haga una **utilidad en particular** 

### Botones Animados (micro interacciones)

¿Que propiedades vamos a animar?

> Recuerda! no es buena práctica utilizar el valor ``ALL`` 

```css
    /*Animaicon a Botones*/

/*estilos del boton*/
.btn{
    position: relative; /*las animaciones las voy a generar con elementos After y Before*/
    border: none;
    border-radius: 0.25rem;
    padding: 0.2rem;
    width: 15rem;
    height: 2.5rem;
    font-size: 1.25rem;
    font-weight: bold;
    cursor: pointer;
    overflow: hidden; /*En caso de que el texto del boton desborde es mejor que lo oculte*/
    box-shadow: 0.25rem 0.25rem 0.5rem 0.25rem rgba(0, 0, 0, 0.15);
}

/*es una cajita que mide de altura 0.25 rem, en este caso lo que vamos hacer es una transicion sobre esa propiedad Width
    por eso esa propiedad debe empesar en 0 por ciento, por que lo que vamos hacer es jugar con el posicionamiento en x 
    con left y right respectivamente dependiendo del boton y simplemente vamos hacer una transicion sobre la propiedad width
    y sobre la propiedad left o right  dependiendo del boton para que se anime y entonces se vea el desplazamieto
*/
.anim-bottom::after{ /*despues del boton*/
    content: "";
    position: absolute; /*se posiciona respecto de su elemento padre en este caso el RELATIVE*/
    bottom: 0;
    width: 0%;
    height: 0.25rem; /*es un diez por ciento menos de la altura original 2.5rem*/
    background-color: #d00;
    transition: width 0.5s ease, left 0.5s ease, right 0.5s ease;
}

.anim-bottom:hover::after{
    width: 100%;
}

.to-left::after{
    left: 0;
}
.to-center::after{
    left: 50%;
}

.to-center:hover::after{
    left: 0;
}

.to-right::after{
    right: 0;
}
```
### Botones con Gradientes Animados

```css
    /*Botones con Gradientes Animados
    Lo que vamos a hacer es extender la posicion del fondo, para que nada mas nos muestre los primeros colores el 
    rosa y el violeta, esté oculto la parte del anaranjado el naranja y el naranja rojo y con el efecto del 
    hover podamos modificar eso. siempre y cuando conozcas a fondo CSS puedes lograr este tipo de efectos

*/
.anim-bg-gradient{
    background-image: linear-gradient(to right, pink, violet, orange, orangered);
    background-size: 300% 100% ; /*ancho y un alto de 100%*/
    transition: background-position 0.5s ease-in-out; /*para que el cambio no  se vea muy súbito hacemos esta transicion*/
}

/*a esta clase en el estado hover.
recuerda: que los gradientes al definirse en la propieda Image son fondos!
*/

.anim-bg-gradient:hover{
    background-position:100% 0 ; /*vete al final de los gradientes (recuerda el primer valor es X y el segundo es Y)*/
    
}
```
### Menú de Pestañas Tabs (Maquetación)

### Menú de Pestañas Tabs (animación)

Ya dijimos que es un antipatron maquetar con IDs pero cuando querremos este tipo de comportamientos que tengan que ver con la pseudo clase target como para sacar un menú de navegación movil,estos que tambien tenemos un menú de pestañas pues aqui si es util utilizar los ids en base al id es que podemos sacar este tipo de efectos y sin la necesidad de JS

```css
    /*Cuando un input esté en su estado checked realmente a quien yo quiero afectar es a la etiqueta Label que tiene como hermana
    cuando lo seleccionamos el color se pasa al texto 
*/
.tabs-menu input[type="radio"]:checked + label{
    color: #fff;
}

.tab-bg-hover{
    position: absolute;
    width: calc(100% / 4 - 0.5rem);
    height: 2rem;
    border-radius: 0.5rem;
    background-image: linear-gradient(90deg, #a00, #d00);
    transition: transform 300ms ease-in-out; /*vamos a trasladarnos en X*/
}

#tab-1:checked ~ .tab-bg-hover{ /*cuando este chekeada, [~ selector de hermanos en general] */
    transform: translateX(0);
}
#tab-2:checked ~ .tab-bg-hover{
    transform: translateX(100%);
}
#tab-3:checked ~ .tab-bg-hover{
    transform: translateX(200%);
}
#tab-4:checked ~ .tab-bg-hover{
    transform: translateX(300%);
}
```

### Menú Off Canvas (marcado HTML)

¿Por que Off Canvas? por que se encuentra fuera del lienzo del documento.
para ocultar la barra de desplazamiento horizontal.

```css
    html{
    overflow-x: hidden;
}


```

vamos hacer un menú de amburguesa sin la necesidad de programar en JS entonces vamos hacer uso algunos elementos que tanto en la estructura como en la eleccion de etiquetas debemos respetar el siguiente orden.

para evitar programar el boton, el boton lo vamos a generar con input de tipo Check 

> los inputs de tipo Check o de tipo radio nos dan esta capacidad de aplicar al estado Checked entonces cuando esté checked vamos a sacar el menú cambas y cuando no esté cliqueado lo vamos a ocultar

**todo los nombres de clase hacen alucion a lo que hacen respectivamente** 

> tanto el input,  como la amburguesa, como el menú de navegacion tienen que ser hermanos si no son hermanos no nos va servir aqui vamos a usar el selector de hermano adyasente(+) selector de hermanos en general que es la (~) 

1. checkbox
2. label
3.  y al final la etiqueta nav

### Botón de Hamburguesa Animado

¿Como voy a lograr la X? La vamos a lograr dandole diferentes transformaciones a la clase before y after cuando el boton esté checkeado.

```CSS
    /*BOTON CANVAS*/

.off-canvas-btn{
    position: fixed;
    bottom: 1rem;
    right: 1rem;
    z-index: 999;
    width: 3rem;
    height: 3rem;
    cursor: pointer;
    opacity: 0.25; /*Engaño visual*/
}

.off-canvas-burger{
    position: fixed;
    bottom: 1rem;
    right: 1rem;
    z-index: 998;
    width: 3rem;
    height: 0.6rem; /* 3/5 */
    background-color: #d00;
    border-radius: 0.3rem;
    transform: rotate(0deg) translate(0,-1.2rem);
    transform-origin: top left;
    transition: transform 500ms ease, background-color 500ms ease;
}

.off-canvas-burger::before,
.off-canvas-burger::after{
    content: "";
    display: block;
    width: 100%;
    height: 0.6rem;
    background-color: #d00;
    border-radius: 0.3rem;
    transition: transform 0.5s ease;
}

.off-canvas-burger::before{
    transform: rotate(0deg) translate(0, -0.9rem);
    /* background-color: blue ; */
}

.off-canvas-burger::after{
    transform: rotate(0deg) translate(0, 0.3rem);
    /* background-color: green; */
}

.off-canvas-btn:checked + .off-canvas-burger{
    background-color: transparent;
}

/*rotacion de el elemento*/
.off-canvas-btn:checked + .off-canvas-burger::before{
    transform: rotate(45deg) translate(0,0);
}


.off-canvas-btn:checked + .off-canvas-burger::after{
    transform: rotate(-45deg) translate(0.4rem, -0.5rem);
}
```

### Menú Off Canvas (maquetación y animación)

Un menú Off Canvas es un elemento un menú que está colocado en alguna parte y sale de la derecha o sale de arriba o de la izquieda o de abajo.

vamos a maquetar nuestro menú para que ocupe toda la pantalla(opcional)

Hay quien les gusta poner el menú dentro de una Ul Li LINK (es complicarse un poco) 

Hay un truco para poder estirar un elemento a pantalla completa con posicionamiento Fijo(fixed) ya sabes que cuando tu le das posicionamiento fijo a un elemento perde sus propiedades de ancho y alto, pierde la disposicion del documento html.

> Recuerda: ``Top y Left`` tiene mayor preferencia que ``Bottom y right``

> Recuerda: la clave de todo esto es que el input se activa con la propiedad checked del checkbox si yo quisiera poner un boton entonces ahi ya se pierde esta pseudoclase checked y entonces tendria que usar javaScript para andar quitando una clase que sea la que anime el elemento en css tienen que ser hermanos directos tanto el input y label

```css
    /*Maquetando nuestro menú off canvas*/

.off-canvas-menu{
    position: fixed;
    /*Con esto estiramos el contenedor*/
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 997; /**/

    display: flex;
    justify-content: center;
    align-items: center;

    background-color: #0008; /*el 8 reprecenta el 80 por ciento de opacidad*/
    transition: transform 500ms ease-in-out ;/*¿Como lo animo: pues con una linda y hermosa transicion?*/
    transform: translate(0, -100%);
    transform: translate(0, 100%);/*para que el menú salga de abajo*/
    transform: translate(100%, 0%);/*para que salga de la derecha*/
    transform: translate(-100%, 0%);/*para que salga de la izquierda*/
    
}

.off-canvas-btn:checked ~ .off-canvas-menu{
    transform: translate(0,0);
}

/*Estilos al contenedor*/
.off-canvas-menu-container{
    width: 100%;
    height: 100vh;

    display: flex;
    flex-direction: column;
    justify-content: center;
    /* background-color: slateblue; */
}

/*estilo a los enlaces*/
.off-canvas-link{
    border-bottom: thin solid #d00;
    padding: 2rem;
    font-size: 1.5rem;
    text-align: center;
    text-decoration: none;
    color: #fff;
    transition: background-color 300ms ease;
}

.off-canvas-link:first-child{
    border-top: thin solid #d00;
}

.off-canvas-link:hover{
    background-color: #d005;
}
```
### Ventana Modal

Necesitamos un enlace que abra la ventana, así como para el menú utilizamos la pseudoclase checked de los inputs acá vamos a utilizar la pseudoclase Target esto lo tienen todo los elementos que tengan atributo ID eje: cuando el temario tiene el target en la url, se ilumina de color verde. como este Id del temario tiene el temario-css mediante la pseudoclase target es que le di ese color verde entonces es algo así que vamos a utilizar para la ventana modal

> Recuerda: 3rem = 48px si tu revisas cualquier guia de estilos de interacciones en moviles mas o menos un dedo promedio el toque a una pantalla de lo que representaria el area de un dedo es mas menos 40px

La clave de hacer funcionar sin javaScript. La ventana modal la voy animar de la opacidad: 0;

> Recuerda! cuando un elemento es interactivo y nosotros le quitamos la opacidad el elemento sigue existiendo [los enlaces son interactivos] entonces sigue habiendo interaccion con los enlaces lo puedes ver cuando el cursor:pointer; se activa

Cuando tu tienes una ventana modal así aparte de quitar la opacidad debes quitar una propiedad que se llama pointer-events:none; esta propiedad le da interactividad a los elementos de CSS 


al hacer click en "Abrir enlace" el target de la url está en ese id="modal-1"

> Recuerda la X es un enlace no un boton y al precionarlo nos hace referencia a un id "close" cerrar el hash cambia y hace que el modal se cierre


```css
    /*Ventana Modal*/

.modal{
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 997;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #0008;
    opacity: 0;
    pointer-events: none; /*Con esto los enlaces ya no son interactivos*/
    transition: opacity 500ms ease-in-out;
}

    /*Para abrir el modal*/

.modal:target{
    opacity: 1;
    pointer-events: auto;
}


.modal-container{
    position: relative; /*la X lo voy a posicionar absolutamente respecto del contenedor por eso le doy el posicionamiento relativo*/
    border: thick double #d00;
    border-radius: 1rem;
    padding: 2rem;
    width: 70%;
    height: 70vh;
    display: flex;
    flex-direction: column;
    text-align: left;
    overflow: hidden; /*En caso de que haya desbordamiento se oculta*/
    background-color: #fff;
}

/*boton cerrar*/

.modal-close{
    position: absolute;
    top: 1rem;
    right: 1rem;
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
    font-size: 2rem;
    font-weight: bold;
    text-align: center;/*lo centro en horizontal*/
    line-height: 3rem;/*lo alineo verticalmente*/
    text-decoration: none;
    color: #fff;
    background-color: #d00;
    transition: background-color 300ms linear, transform 300ms ease-in-out;
}

.modal-close:hover{
    background-color: #a00;
    transform: scale(1.2);
}
```
### Intro Películas Star Wars

```css
    @keyframes introStarWars {
    0%{
        transform: perspective(100vh) rotateX(15deg) translateY(100%);
    }
    
    100%{
        transform: perspective(100vh) rotateX(25deg) translateY(-200%);
    }
}

.star-wars{
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    height: 100vh;
    overflow: hidden; /*cuando desbode las letra lo oculta*/
    color: #ffb13a;
    background-image: url("../assets/starss.gif");
}


.star-wars-container{
    margin-left: auto;
    margin-right: auto;
    width: 80%;
    text-align: justify; /*el texto está justificado*/
    letter-spacing: 0.1rem;
    animation: introStarWars 20s linear infinite;
}


.star-wars h2,
.star-wars h3{
    font-size: 3rem;
    font-size: 5vw;
    text-align: center;
}

.star-wars p{
    font-size: 2rem;
    font-size: 3vw;
    line-height: 4rem;
}
```

SIGUIENTE CURSO: Responsive y Arquitectura CSS (5/5)

Responsive: es la capacidad que deben tener nuestros sitios web para que se adapten al ancho de cualquier pantalla
Arquitectura-css: tiene que ver con buenas prácticas con el uso de herramientas adicionales que puedan mejorar nuestro flujo de trabajo.

## RESPONSIVE DESIGN Y ARQUITECTURA CSS 5/5.

 [link para leer](https://jonmircha.com/responsive)

**Responsive Design** es el paradigma actual.

Cuando comienzes abordar un proyecto para la web, para cualquier interfaz sea para un sitio web informativo  de un blog, de una aplicación  el Responsive Design es el paradigma con el cual tu debez comenzar a desarrollar y diseñar y a planificar tu sitio o aplicacíon la interfaz que vayas a desarrollar

**Arquitectura CSS** es el conjunto de buenas prácticas.

Si nuestro proyecto comienza a crecer exponencialmente hace que nuestro codigo no se vuelva un desastre y el codigo CSS pueda escalar de una forma eficiente vamos a ver: Metodologias, frameworks procesadores que nos van a ayudar mucho en este proceso de mantener lo mas legible estandarizado y coherente nuestro código CSS, Te recomiendo ir al curso de FLEXBOX (es un sistema de maquetacion que nos ofrece CSS para moldear las interfaces de nuestros sitios web) y por el otro lado GRIDCSS es el módulo que lo complementa.

> __FLEXBOX:__ Está mas pensado a alinear elementos de nuestros componentes internos imagina una card (imagen, texto, la descripcion y el boton).

> __GRIDCSS:__ Nos va permitir defir un sistema de retícula es decír filas y columnas donde podamos decir: aca va la cabecera  aca ba el pie de página,  aca va el contenido lateral

### Descarga de archivos para trabajar


### Introducción al Responsive Design

EEthan Marcotte en 2010 lo que hizo con su artículo y su libro fue sentar las bases.

3 principios del Responsive Design.

1. Grids Flexibles. (la reticula en la cual nuestros sitios se adaptaban tenia que fluir y debia adaptarse al dispositivo que lo consumiera)

2. Imagenes Flexibles. (aunque fisicamente tu imagen sea mas grande, se tiene que adaptar  a la pantalla del dispositivo para evitar el Scroll horizontal) para cualquier elemento multimedia [Audios, videos. Iframes,post de alguna red social, un mapa de google un video de youtube todos esos elementos tendrian que ser flexibles ]

3. Media Queries. la pregunta al nevegador: ¿Estas en modo horizontal? ¿Estas en modo vertical? ¿estas a un tamaño minimo de 600px? mediante esas preguntas podemos definir estilos.


Resposive Design no solo es adaptar el contenido al tamaño de la pantall tambien es considerar:

...También es considerar:

* Conexión de Red ( Wifi, 2G, 3G, 4G, 5G, etc ).
* Hardware y Software de los dispositivos ( S.O., Versiones, Memoria, Procesador, Sensores, etc ).
* Interacciones ( con teclado y ratón, táctiles, por voz ).
* Accesibilidad web ( soporte a discapacidades ).

Cuando ya estes desarrollando aplicaciones mas funcionales que tengan que tener programación frontend y programacion backend en tonces los puntos anteriores van a ser vitales para que tu aplicacion funcione correctamente en cualquier ecenario

### Contenedores flexibles

es todo elemento en nuestra interfaz web, cualquier etiqueta html, cualquier sistema de columnas y tienen que ser flexibles y responsivos

> ¿Como puedes volver un contenedor flexible? antes la mayoria de las unidades de medidas eran pixeles y porcentajes, teniamos la resolucion de pantalla 1024 x 768 el diseño se entregaba en un photoshop que estaba maquetado a 1024 el diseño web se hacia pixel-perfect, pero aparecieron los dispositivos mobiles, en lugar de pensar en pixeles ya se tenia que pensar en proporciones.

```css
    /*Todo los elementos que empiezen en su nombre de clase
con la palabra Box y algo más aplica estos estilos*/

[class^="box"]{
    margin: 3rem auto; /*y... automático a los lados*/ 
    background-color: orangered;
}

/*como no se visualiza vamos a darle una anchura y una altura fija*/
.box{
width: 300px;
height: 300px;
}

/*si yo hago mas pequeña la pantalla,  por debajo de 300px pues crea 
un scroll horizontal. pero no haci en version para mobil
*/

/*¿Que seria una caja flexible?*/
/*es aquella donde las dimenciones de ancho y alto las vamos a definir (no
con unidades absolutas) sino con unidades relativas*/

.box-flexible{
    width: 50%; /*hace referencia al contenedor padre, en este caso el Article*/
    height: 20vh; /*si voy a dar dar altura en porcentajes el contenedor padre tiene que 
    tener perfectamente definida el tamaño de la altura expresado en una unidad de medida absoluta, por que sino los
    porcentajes no van a servir*/
}
```


Hay otra manera de controlar está flexibilidad y para ello vamos a utilizar 4 propiedades de CSS que tienen que ver con el ancho y alto pero para cuando tengamos que definir  maximos o minimos tamaños, podriamos utilizar pixeles que son unidades absolutas

### Propiedades max-width, min-width, max-height y min-height

```css
    /*en lugar de definir una anchura  y una altura base podriamos definir puntos máximos
 y puntos mínimos*/
.box-flexible-2{
    max-width: 960px;
    min-width: 280px;
    max-height: 480px; /*la altura siempre va depender del contenido*/
    min-height: 280px;
}
```


Vean como ya existe el desbordamiento por que llegó a su máxima altura

![desbordamiento](/assets-responsive/desbordamiento.JPG)

> _CUIDADO: en utilizar maximos y minimos y despues definir una anchura y una altura base por que ahi dependiendo de la unidad de medida que utilizemos podemos tener ciertos problemas_

### Tamaños Fijos VS Tamaños Maximos y Minimos


```css
    .box-flexible-3{
    max-width: 960px;
    min-width: 280px;
    max-height: 480px;
    min-height: 280px;
    width: 300px; /*tiene major jerarquia sobre maximo y minimos*/
    height: 300px; /*tiene major jerarquia sobre maximo y minimos*/
}

/*que  pasa si lo hago en unidades relativas*/

.box-flexible-4{
    max-width: 960px;
    min-width: 280px;
    max-height: 480px;
    min-height: 280px;
    width: 50%; /*tiene major jerarquia sobre maximo y minimos*/
    height: 20vh; /*tiene major jerarquia sobre maximo y minimos*/
}
```

> Cuando tu tienes contenedores flexibles y haz definido maximos y minimos, pero que pasa cuando aparte defines anchura (width) y altura(height) si estas propiedades lo defines en unidades absolutas como los pixeles pues esa fluides que nos da los máximos y minimos no las vamos a tener por que ``widht y height`` tienen mayor jerarquia sobre max y min, 

> Pero ojo que pasa cuando tiene maximos y minimos pero haz definido la anchura y la altura con unidades relativas, ve que va tener mayor jerarquia `width y height`  pero cuando ya llega a un minimo o un máximo digamos que si obedecen  

> Cuando no se tiene un conocimiento de los prefijos y de la jerarquia que tiene sobre los prefijos las propiedades iniciales que son `width y height` empesamos a tener ciertas frustraciones

cualquier elemento multimedia debe ser capaz de fluir al tamaño de su contenedor no solo las imágenes sino cualquier elemento multimedia (cualquier cosa que no sea texto)

### Multimedia Flexible


la etiqueta map ya no se usa. 

```css
     img, audio, video, iframe, canvas, svg, picture {
    max-width:100%;
    height: auto;
  }
     
```

### Atributo srcset y sizes

estos atributos nos van a permitir mejorar el rendimiento al colocar la imagen más adecuada, el navegador es quien decide colocar la imágen mas adecuada debpende de lo que definamos en el atributo SRCSET podemos definir las imagenes ya sea por: aspect ratio(resolucion de pantalla o por el ancho de la pantalla)

> una forma de probar es aumentando el zoom de 100% -> 150% -> 200%

> El atributo SRCSET nos permite cambiar diferentes imágenes por tamaño real pues esto va optimizar el rendimiento. por que no va ser lo mismo consultar desde el mobil y el escritorio, ya que podemos poner una imagen con menos resolución para el mobil

> El atributo Size va definiendo un tamaño especifico que mi imagen pueda ocupar.

```html
    <!-- 1.5x = 150%  de 600px en adelante pole esto... (la W significa ancho)-->
      <img src="img-responsive/html5-3d-600.png"
      srcset="img-responsive/html5-3d-600.png 1x, img-responsive/html5-3d-900.png 1.5x, img-responsive/html5-3d-1200.png 2.0x" alt="HTML-5">
      
      <img src="img-responsive/html5-3d-600.png"
      srcset="img-responsive/html5-3d-600.png 600w, img-responsive/html5-3d-900.png 900w, img-responsive/html5-3d-1200.png 1200w" alt="HTML-5">
      <!-- cuando la maxima anchura sea 768px  quiero que la imagen se veaa 600px -->
      <img src="img-responsive/html5-3d-600.png"
      srcset="img-responsive/html5-3d-600.png 600w, img-responsive/html5-3d-900.png 900w, img-responsive/html5-3d-1200.png 1200w" 
      sizes="(max-width: 480px)300px, (max-width: 600px)480px, (max-width: 768px)600px,
      (max-width: 1024px)900px, (min-width: 1200px)1200px"
      alt="HTML-5">
```

> pongan atencion a los sitios hechos con wordpress, por que desde hace varios años algunas de sus plantillas que están creadas con las buenas prácticas de wordpress lo que hace internamente wordpress es cambiar la imagen mas adecuada mediante estos atributos  `srcset y size` 

Si ustedes han trabajado con wordpress saben que cuando ustedes suben a la bibliteca de imagenes una imagen no es que nada mas se suba la imagen wordpress internamente genera varios tamaños de la misma imagen y¿por que crea esos tamaños? pues dependiendo desde que dispositivo estes accediendo al sitio wordpres utiliza estos atributos

### Etiqueta picture

algunos sitios hacen esto cuando tienen una version mimificada del logotipo, eje: hay sitios que en la version mobil solamente se ve el logo y que cuando estamos en la version descktop se ve el logo y aparte el nombre de la empresa que forma parte del logo

> las mediaquerys son como condicionales, preguntas que le hacemos al navegador ¿cuando la maxima anchura de la pantalla  sean 600px? si es de 600px para abajo, que la imagen se vea a 480 entonces esa es una media query


> este es el principal objetivo de la etiqueta picture, cambiar imágenes

> **webp** es un nuevo tipo de formato de imagen propuesto por google que trata de ser una mejor solucion de imagen para los jpg y para los gifs animados con un mayor peso

> ¿como saber el tipo de imagen? pues al inspeccionar el código ve a la pestaña de network


### Videos Responsivos 

> ¿Como hacemos un elemento multimedia responsivo? `max-width: 100%, height:auto` 

```css
    img,
video{
    max-width: 100%;
    height: auto;
}


/*esta es una tecnica vieja*/
.responsive-media{
    position: relative;
    max-width: 100%;
    height: 0;
    /*
        Formato widescreen 16:9
        16 ------> 100%
        9 -------> 56.25%
    */
    padding-bottom: 56.25%;
}

.responsive-media > *{
    position: absolute; /*su elemento padre es un position:relative, se posiciona respecto de
    su contenedor padre*/
    width: 100%;
    height: 100%;
}

/*la nueva forma de hacer responsivo*/

.aspect-ratio-16-9{
    aspect-ratio: 16 / 9;
    aspect-ratio: 4 / 3;
    aspect-ratio: 16 / 9; /*es como definir el ancho y alto en proporcion
    */
}


/*es una forma mas apropiada de aplicar responsabilidad 
a nuestros videos y documentos multimedia
*/
.aspect-ratio-16-9{
background-color: rebeccapurple;
aspect-ratio: 16 / 9;
aspect-ratio: 1 / 1;
aspect-ratio: 16 / 9;
}
```

### Iframes responsivos

> al darle máxima altura del 100% y altura automática

quisá lo que nos convenga utilizar las 2 tecnicas (tecnica vieja o usar el aspect-radio: 16:9)

gracias al booton-pading mágico se conserva rectangular

cuando llega al tamaño real del iframe de Youtube pues deja de hacer esta responsividad.

quisa un mapa lo queremos a un aspect-ratio: 1:1

```css
    /*es una forma mas apropiada de aplicar responsividad 
a nuestros videos y documentos multimedia
*/
.aspect-ratio-16-9{
background-color: rebeccapurple;
aspect-ratio: 16 / 9;
aspect-ratio: 1 / 1;
aspect-ratio: 16 / 9;
}

.aspect-ratio-1-1{
    aspect-ratio: 1/1;
}
```

### Media Queries Versión 2.1

medios de consultas son preguntas que le hacemos al navegador y dependiendo de estas preguntas pues el navegador va a aplicar ciertos estilos eje: la orientaion del dispositivo sea horizontal cuando el aspect-ratio sea el doble cuando el tamaño de pantalla la minima anchura a 300px cuando la maxima anchura sea a 500px cuando el usuario prefiera la reduccion de animaciones o cuando prefiera efectos animados o cuando el usuario prefiera el modo dark

> las media querys se definian desde la etiquet link

```html
    <link rel="stylesheet" media="print" href="print.css" >
```
esta hoja de estilos va haplicar cuando el usuario mande a imprimir el atributo ``media`` debe ir despues del atributo `rel`

> _Ctrl + p_ cuando mandes a imprimir tienes que asegurarte de haber scrolleado toda la página para que tome los estilos

```css
    /*primero debemos especificar el tamaño del papel*/
@page{
    size: A4;
}

body{
    font-size: 12pt; /*el software que utilizamos para redactar 
    es word y ese software trabaja con puntos, entonces como estos 
    estilos van a aplicar solamente para cuando yo mande a imprimir
    pues se me hace correcto pues usar las mismas unidades de medida
    que utilizaria un procesador de texto*/
    font-family: serif;
    background-color: #000;
    color: #fff;
}
```

debes scrollear todo el contenido para que la previsualizacion del comando imprimir lo detecte

### Media queries version 3

Esta es la foma más utilizada

> prefers-reduced-motion busquen en la documentacion de mozilla development network

> Recomendacion: _Cuando empiezen un sitio web, si ya comenzaron con la tecnica de Descktop first, no paren (la media query) y acaben con esa tecnica es decir no mesclen min-width y max-width_


```css
    /*media query para bajar animación*/



@media screen and (prefers-reduced-motion: reduce){

    /*REDUCE en mis configuraciones no tengo el valor de REDUCE */
    html{
        scroll-behavior: auto;
        scroll-behavior: smooth;
    }
}



@media screen and (prefers-reduced-motion: no-preference){

    /*REDUCE en mis configuraciones no tengo el valor de REDUCE */
    html{
        scroll-behavior: auto;
        scroll-behavior: smooth;
    }
}


/*como mi sistema operativo lo tengo en modo dark
esta media query toma eso como referencia y aplica los 
estilos

cuado al sistema operativo le das a entender que prefieres el 
modo dark(oscuro) esté configura las aplicaciones en modo oscuro por defecto

*/
@media screen and (prefers-color-scheme:dark){
    html{
        background-color: black;
        color: cyan;
    }
}


@media screen and (prefers-color-scheme:light){
    html{
        background-color: white;
        color: darkblue;
    }
}


/*Como mi sistema operativo tiene seleccionado el modo oscuro
pues obiamente estas preferencias de color  anque estan definidas despues del
DARK pues simplemente no están obedeciendo por que predomina
el */
@media screen and (prefers-color-scheme:no-preference){
    html{
        background-color: white;
        color: darkred;
    }

}

/*¿Como reestablesco los colores?*/
@media screen and (prefers-color-scheme:dark){
    html{
        background-color: white;
        color: black;
    }
}


/*Media querys que afectan el tamaño de la pantalla*/
/*generalmente las media querys con la que vamos a trabajar  en min width aplica
para cuando nostros estamos haciendo un diseño pensando primero en el mobil*/

/* En MOBILE FIRST se usa min-width que significa lo mínimo, del valor que des
 hacia arriba*/
@media screen and (min-width:480px){
    html{
        background-color: lightpink;
    }
}

/* En DESKTOP FIRST se usa max-width que significa lo máximo, del valor que des
 hacia abajo*/

 /*predomina esta media query por cascada*/
 @media screen and (max-width:1024px){
    html{
        background-color: lightgreen;
    }
}

/*Regresamos a los colores principales*/
@media screen and (min-width:1200px){
    html{
        background-color: white;
    }
}
```


Siguiente: ¿Cuando necesito ir aplicar una media query?

### Breakpoints

El breakpoint es el punto de interrupcion es decir es esa medida en la cual decido aplicarle estilos css

Analizen los sitios que ustedes visiten se van a dar cuenta que la mayoria no utiliza los 1920px, porque imaginense en un blog estar leyendo un parrafo de blog a 1920px seria muy cansado, por lo general el contenedor de los textos esto tambien tiene que ver con la usabilidad y la ergonomia los tamaños que definio Ettan marckote siguen siendo validos, vaver ocaciones donde querramos aplicar herro-image el 100% de la pantalla

el contendido de varias paginas web se centra no son al 100%

hay sitios que usan el 100% de la pantalla por que les comviene, eje: paginas de documentacion como bootstrap Vue.js

Actualmente los contenedores por muy grandes que sean llegan a ser de 1400 a 1440px


> **En la medida de lo posible combierte tus pixeles en  EMS**

¿Por que?

> los pixeles son unidades absolutas y tiene que ver con la resolucion de la pantalla entonces si tu dejas tus media  querys en pixeles corres riesgo de que dispositivos de gama alta o dispositivos que tengan mayor densidad de pixeles fisica en sus pantallas pues por ahi esos pixeles, como tu dejaste tus mediaquerys expresada en pixeles pues esos pixeles no se visualizen correctamente por la dencidad adicional que tengan en la pantalla de estos dispositivos de alta gama, 

> los EMS son unidades de medida en css QUE SE ADAPTAN al tamaño de la tipografia del contenedor entonces se a utilizado la unidad de medida EM por que esta se puedea adaptar en pantallas que tengan mayor densidad de pixeles. Cuando tu cargas un sitio en una pantalla que tiene mejor calidad(mejor densidad de pixeles)  al utilizar ems en lugar de pixeles pues todo se va volver relativo al contenedor en el que esté.

> estas recomendaciones lo dan profecionales del diseño web

eje: 800/16=50

### Viewport

una de sus 4 propiedades puedes definirle hasta que medida un usuario pede darle zoom a tu página

> antes que tu ego profecional está ¿para quienen estas diseñando? incluso sobre tu cliente, usuarios finales con problemas visuales.

> hay paginas que bloquean el click derecho ¿Como te sentirias? mal por que la experiencia agradable no la tiene siempre trata de pensar que lo mas importante no es tu ego profecional. sino ponerte en los zatapos del usuario final

yo uso el viwport tal cual nos da el atajo del EMET.

### Grid Responsiva Artesanal con Flexbox

¿Por qué los frameworks como Bootstrap, fundation usan una grid de 12 columnas?

> https://960.gs/ este era el abuelito de bootstrap estaba maquetado a 960px

> nos daba una grid de 12 y 16 columnas por que son números muy divisibles

en esta seccion aprenderemos como hacer tu propia grid sin frameworks y flexbox css

> nos guste o no, bootstrap es el framework mas utilizado hoy en día

> si les parece muchas mediaQuerys simplemente reduscanlas a sus necesidades

```css
    


/*
    es muy utilizado el sistema de 12 columnas
    por que tiene muchas diviciones que podriamos tener de elementos 
    que ocupen el mismo espacio a 12 columnas

    12 / 1= 12  elmento al 100%
    12 / 2= 6  elmento al 50%
    12 / 3= 4
    12 / 4= 3
    12 / 6=  2
    12 / 12= 1

    La clave es que la sumatoria de todo los elementos que quieras que esten
    en una misma fila de contenido pues tiene que dar como resultado 12, por que
    si te pasas el elemento pasa a la fila de abajo


    5 + 7 = 12
    2 + 5 + 5 = 12
    4 + 2 + 3 + 3 = 12

    12 -------> 100%
    ?col -----> ???%

    GRID SYSTEM ARTESANAL CON FLEXBOX A 12 COLUMNAS

    Tamaños (Mediaqueries)
  xs    -   extrasmall      - 0                 -  479px        -480res
  sm    -   small           - 480px (30em)      -  767px        -800res
  md    -   medium          - 768px (48em)      -  991px        -1024res
  lg    -   large           - 992px (62em)      -  1199px       -1280res
  xl    -   extralarge      -+1200px (75em)                     ->1281res

*/

html{
    box-sizing: border-box; /*si tu das espaciados y bordes ya estén incluidos dentro del modelo de caja*/
    font-size: 16px;   
}

*,
*::after, 
*::before{
    box-sizing: inherit;
}

.row{
    display: flex; /*flexbox es unidimencional*/
    flex-wrap: wrap;
}

/*si quieres ver el acomodo de las filas y columnas*/
.row > [class^="col"] { /*aplica estilos a los elementos que emepiezen con la palabra COL*/
 border: thin solid gray;
 padding: 1rem;
}

/*cuando estes maquetando  no necesitarias poner esta grid*/

/*defino sistema de columnas con cierto ancho*/

/*grid responsiva mobile first
 Los estilos antes de las media querys estan pensadas para el mobil
*/
.col-1{
width: 8.333333333333333%;
}

.col-2{
    width: 16.6666667%;
}

.col-3{
    width: 25%;
}

.col-4{
    width: 33.33333333%;
}

.col-5{
    width: 41.66666667%;
}

.col-6{
    width: 50%;
}

.col-7{
    width:58.33333333%;
}

.col-8{
    width: 66.66666667%;
}

.col-9{
    width:75%;
}

.col-10{
    width: 83.33333333%;
}

.col-11{
    width: 91.66666667%;
}

.col-12{
    width: 100%;
}

/*lo siguiente a determinar es nuestro grid sistem establecer
el tamaño de las media querys*/

/*Aca abajo debemos crear nuestras media queris, como vamos a hacer una grid mobileFirst
    las media querys tienen que ir de la menor a la mayor
*/

@media screen and (min-width: 30em){ /*hay una separacion entre AND's*/
        .col-sm-1{
            width: 8.333333333333333%;
        }
        
        .col-sm-2{
            width: 16.6666667%;
        }
        
        .col-sm-3{
            width: 25%;
        }
        
        .col-sm-4{
            width: 33.33333333%;
        }
        
        .col-sm-5{
            width: 41.66666667%;
        }
        
        .col-sm-6{
            width: 50%;
        }
        
        .col-sm-7{
            width:58.33333333%;
        }
        
        .col-sm-8{
            width: 66.66666667%;
        }
        
        .col-sm-9{
            width:75%;
        }
        
        .col-sm-10{
            width: 83.33333333%;
        }
        
        .col-sm-11{
            width: 91.66666667%;
        }
        
        .col-sm-12{
            width: 100%;
        }
  }

@media screen and (min-width: 48em) {
    .col-md-1 {
      width: 8.333333333333333%;
    }
  
    .col-md-2 {
      width: 16.66666666666667%;
    }
  
    .col-md-3 {
      width: 25%;
    }
  
    .col-md-4 {
      width: 33.33333333333333%;
    }
  
    .col-md-5 {
      width: 41.66666666666667%;
    }
  
    .col-md-6 {
      width: 50%;
    }
  
    .col-md-7 {
      width: 58.33333333333333%;
    }
  
    .col-md-8 {
      width: 66.66666666666667%;
    }
  
    .col-md-9 {
      width: 75%;
    }
  
    .col-md-10 {
      width: 83.33333333333333%;
    }
  
    .col-md-11 {
      width: 91.66666666666667%;
    }
  
    .col-md-12 {
      width: 100%;
    }
  }
  
@media screen and (min-width: 62em) {
    .col-lg-1 {
      width: 8.333333333333333%;
    }
  
    .col-lg-2 {
      width: 16.66666666666667%;
    }
  
    .col-lg-3 {
      width: 25%;
    }
  
    .col-lg-4 {
      width: 33.33333333333333%;
    }
  
    .col-lg-5 {
      width: 41.66666666666667%;
    }
  
    .col-lg-6 {
      width: 50%;
    }
  
    .col-lg-7 {
      width: 58.33333333333333%;
    }
  
    .col-lg-8 {
      width: 66.66666666666667%;
    }
  
    .col-lg-9 {
      width: 75%;
    }
  
    .col-lg-10 {
      width: 83.33333333333333%;
    }
  
    .col-lg-11 {
      width: 91.66666666666667%;
    }
  
    .col-lg-12 {
      width: 100%;
    }
  }
  
@media screen and (min-width: 75em) {
    .col-xl-1 {
      width: 8.333333333333333%;
    }
  
    .col-xl-2 {
      width: 16.66666666666667%;
    }
  
    .col-xl-3 {
      width: 25%;
    }
  
    .col-xl-4 {
      width: 33.33333333333333%;
    }
  
    .col-xl-5 {
      width: 41.66666666666667%;
    }
  
    .col-xl-6 {
      width: 50%;
    }
  
    .col-xl-7 {
      width: 58.33333333333333%;
    }
  
    .col-xl-8 {
      width: 66.66666666666667%;
    }
  
    .col-xl-9 {
      width: 75%;
    }
  
    .col-xl-10 {
      width: 83.33333333333333%;
    }
  
    .col-xl-11 {
      width: 91.66666666666667%;
    }
  
    .col-xl-12 {
      width: 100%;
    }
  }
```

### Feature Queries

las media querys son consultas de medios

las `Feature Queries` son consultas de las caracteristicas son reglas css que le van a preguntar al navegador si soportan ciertar caracterirsticas

¿Para que nos sirve preguntarle al navegador si soporta ciertas caracterirsticas? cuando sale algo nuevo que no está bien soportado en todo los navegadores, una buena practica es dar cierta retrocompatibilidad

las `Feature Queries` nos permitia preguntarle al navegador y cuando el navegador no soportaba la media query entonces tu podrias aplicar otra estrategia de css para poder simular ese comportamiento

> Cuando css y html saquen una nueva caracteristica en lugar de validar con librerias como modernizer y empesar a descargar mas cosas a tu aplicacion, ve que puedes hacerlo de manera muy simple con las reglas @suport, asi te evitas estar agregando librerias adicionales

> `¿Como te puedes entrar de los cambios?` https://caniuse.com/ 


```css

    /*Feature queries*/

@supports (grid-template-columns: subgrid){
    html{
        background-color: black;
        color: greenyellow;    
    }
}

/*Las media querys y las Feacture Queries nos permiten trabajar 
    con los operadores lógicos(and, or, not)
*/

@supports not (grid-template-columns: subgrid){
    html{
        background-color: darkgoldenrod;
        color: white;    
    }
}

/*Antes se utilizaba librerias como Modernicer librerias de javascript
para dar esta retrocompatibilidad a ciertar propiedades de CSS*/

/*Las 2 condiciones debes ser verdaderas*/

@supports (display: grid) and (grid-template-columns: subgrid){
    html{
        background-color: darkslateblue;
        color: lightseagreen;
    }
}


/*Condicional OR, por lo menos una debe ser verdadero*/
@supports (display: grid) or (grid-template-columns: subgrid){
    html{
        background-color: white;
        color: black;
    }
}
```

### Container Queries


Es otra opcion más
Asi como las Media queries nos permiten hacer cambios dependiendo del tamaño de la pantalla. y asi como las feature queries nos permiten aplicar ciertas reglas css dependiendo del soporte de algunos atributos y propiedades los ``Container queries`` nos va permitir redimencionar un contenido en particular

> COMPONENETE: los framework reactivos orientado a componenetes como anguar, vue.js, reakt  ya tenemos el concepto de programacion orientada a componenetes(¿paradigme new?) 

> Esto de los _Container Queries_  en lugar de que un elemento de tu interfaz dependa del tamaño de la pantalla dependa mas bien de sus necesidades

Imagina una targeta necesita estar en vertical hasta que el tamaño de su imagen sea de 300px y depues de ahi quisas esa imagen cambia a aun formato horizontal para mostrar su contenido pero que no va depender como tal del tamaño de la resolucion o de las caracteristicas del dispositivo, sino que va depender de sus propias necesidades

> para activar la bandera : ``chrome://flags/ ``pegalo en el navegador y buca en la caja de busquedas: **container queries.**  todo esto para experimentar, acualmete ya está soportado 2024


> los Container Queries trabajan sobre las necesidades de las propiedades de CSS  pero de cada componente


> solucion: https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_containment/Container_queries pdata, no queria ponerse en linea los elementos.

```css
    .card{
    border: thin solid #000;
    margin-left: auto; /*para que se centre*/
    margin-right: auto;
    max-width: 800px;
    /*container: layout style; /*acvivamos las caracteristicas de conteiner queries*/
     container-type: inline-size;
    container-name: sidebar;
    /* contain: layout; */
    /* contain: size; */
    /* contain: inline-size; */
     /* contain: layout; */
    /* contain: style; */
}

.card-image{
    max-width: 100%;
    height: auto;
    object-fit: cover;
    object-position: 0 50%; /*para que empieze en el eje horizontal,  y al mitad en el eje vertical*/

}

.card-content{
    padding: 1rem;
}

/*lo que yo quiero es que a cierto tamaño del componenete se vuelva en horizontal*/

/* que la parte de texto vaya en una sola fila con la imagen de la card*/

/*para activar lo de container queries al componente padre .card  hay que 
    activarle la propiedad contain: layout...
*/

/*chrome://flags/ */

@container (min-width: 600px){ /*cuando la targeta tenga de 600px en adelante*/
    .card-container{
        display: flex;
    }
}

@container (min-width: 600px) {
    .card-container {
        display: flex;
        /* Otros estilos que desees aplicar */
    }
}


/* .card {
    /* Especifica valores válidos para la propiedad "contain" */
   /* contain: layout style;
  } */
  
  @container sidebar (min-width: 600px) {
    .card-container {
      display: flex;
    }
    .card-container > *{
        width: 50%;
        flex-basis: 50%;
    }
  }
```

> cuando algo es nuevo, mucha paciencia

### SEO

OPTIMIZACIN EN MOTORES DE BUSQUEDA (search engine Optimization)

Recuerda que hay ciertas practicas a nivel de codigo de html que podemos aplicar para que de forma orgánica nuestros sitios, sobre todo si son sitios noticiosos o que generes contenido del dia a dia se pueda ir posicionando respecto de la temática de la que es tu sitio.

> hacerte conciente que el que tu hagas un sitio una interfaz o una aplicacion web, pues estás ayudando a nivel de código al posicionamiento orgánico en los motores de busqueda

> no te opseciones con sacar calificacion verdes o llegar al 100 a partir de 70pts ya es un buen puntaje

mas que responsive desigin y pensar en adaptar el contenido al tamaño de la pantalla, tendriamos que pensar en diferentes estrategias de diseño multidispositivo y por  ahi te ablaba del responsive design del adaptive design, responsive design + server site componenets, responsive responsive design y del fluid design 

https://pagespeed.web.dev/?utm_source=psi&utm_medium=redirect

### Desktop First VS Mobile First

hay 2 estrategias para hacer diseño responsivo

> Desktop first (usas max-width y de mayor a menor)

> Mobile First

siempre va ser mas facil ir agregando elementos  que irlos quitando y adaptando lo que quede

> no puedes omitir el responsive design si o si tus interfaces o sitios tienen que ser responsivas

> Te recomiendo siempre empesar por MOBILE FIRST

> muchos frameworks empiezan por MOBILE FIRST(es un paradigma de que todos  nuestros sitios e interfases tienen que adaptarse a cualquier dispositivo)  pues nos combiene empesar por lo mas pequeño, siempre va ser mas facil ir adaptando como a nivel de diseño como a nivel de programacion entonces hoy en dia MOBILE FIRST es la tecnica con la que deberias empesar todo tus proyectos

![descktop-first](/assets/desktop-first.webp)

![mobile-first](/assets/mobile-first.webp)

### Adaptive Design

todas en su conjunto son lo mismo es ofrecernos herramientas para que nuestro diseño sea optimo  adaptable en cuestion de tamaño en cualquier dispositivo

No solo es pensar en adaptar el contenido al tamaño de la pantalla Tambien es considerar:

* conexion de red

* hardware, software

* Interacciones (teclado, raton, tactiles por voz)

* Accesibilidad web (soporte a discapacidades)

no tengo instalado fb ni twiter por mi paz mental.

si quiero entrar a fb voy a un navegador del celular y entro desde ahi, me da como resultado una version simplificada de facebook incluso el dominio cambió, dice m.facebook.com, cuando nosotros abrimos facebook en la computadora del escritorio pues ve como la interfaz va a variar no son lo mismo

lo que nos propone Aaron Gustafson es tener diferentes fronts y dependiendo del tipo de dispositivo (pc-descktop,  mobil o tableta) pues aprovechando estos dominios como m.facebook.com o mobile.facebook, etc podamos redirigir al usuario al frontend que mas se adecue a las caracterirsticas del dispositivo del que nos está consumiendo y eso de detectar el dispositivo ve al video 92 de javascript

El adptive Design en sitios web normalitos informativos, blogs hechas con wordpress, gadsby,  o con estas herramientas tipo cms te voy a ser sincero, el Adaptive Design no te combiene, al adaptive design te va comvenir en aplicaciones interactivas que ciertas aplicaciones o módulos dependiendo del dispositivo en el que se encuentre tu usuario puedan estar funcionando o no como lo son las redes sociales

### Responsive Design + Server Side Components (RESS)

dependiendo de las capacidades y caracteristicas de cada dispositivo hablando de hardware y software es que tendriamos que pensar en las adaptaciones para las interfaces y de ser necesrio mandar varios fronts

> adptive design: habla de redirigir al subdominio mas adecuado donde la interfaz ya esté adaptada para ese dispositivo

> RESS: dependiendo de la tecnologia que ocupemos en el lado del backend(servidor) nosotros si tenemos por ejemplo algun sistema con laravel laravel tiene un sistema de plantilla llamada blade, y el blade es como el html  pero dentro de larabel entonces quizas ya a lado del servidor dependiendo del dispositivo que consumas estar mandando ese frontend pero un front dinámico sin la necesidad de tener subdominios no no sé si fb lo hace  desde el frontend o desde el backend entonces todos estos ejemplos twiter, facebook, youtube

> todas van oriendadas a lo mismo a tratar de darle una mejor experiencia al usuario, a la hora de consumir e interactuar un usuario y una interfaz sea un sitio o una aplicacion

en la página de reforma.com no hay responsive design pero cuando detecta un USERAGENT adecuado con JAVASCRIP la interfaz cambia esa estrategia que tiene es eperiodico

> Adaptive design:  toda las adaptaciones lo hace con js

> RESS: lo hace desde las tecnologias del lado del servidor laravel(BLADE), puede volverse mas amplio dependiendo del lenguaje de programacion del lado del servidor, los sistemas de plantilla o el framework que utilises

> _la diferencia entre al adaptive y el Ress es la perspectiva de la programacion que modifica las interfaces mientras que en adptive desing es el frontend en el ress es el backend_

### Responsible Responsive Design

es hacer un responsive design "Responsable" esto del responsive design es estas buenas prácticas de css son buenas pero va ver momentos donde nosotros a parte de adaptar el contenido tengamos que meter programacion JS  para adaptar el contenido al dispositivo que lo esté consumiendo


Responsible Responsive Design es una evolucion del responsive design de Ettan markote 

Scott jels no propone diferentes fronts sino aplicar esa programacion a un mismo front que se va adaptando dependiendo del tamaño de la pantalla.

Scott Jehl se ha especializado mucho en el performance (mejora de las interfaces a partir del web permormace) video 90 de js 

si con programacion JS detectamos el tamaño de la pantalla para dispositivos mobiles en lugar de embeber directamente el codigo html que nos formaria el mapa o el vido de youbube ponemos un link hacia el mapa o hacia el video entonces ahi el usuario tiene la desicion si lo consulta en ese momento o si lo hace posteriormente entonces ahi ya estamos aciendo que ese ahoro de las cosas que tiene que descargarel sitio para formar el video de Youtube o el mapa de google pues ya se lo estamos ahorando en cuestion de datos al usaurio entonces con programamcion js hacemos esta deteccion. Y si es tamaño de computadoras de escritorio ahi si embebemos el iframe del video y el iframe del mapa es un ejercicio que te permite entender

`display none ` para que se oculte es una mala practica mejor es adaptar el contenido  dependiendo del dispositivo en el que nos encontremos

### Fluid Design.

se habla del 2020 
es una tecnica es un poco ya harta 
sin la necesidad de usar o usar en la menor medida mediaquerys

mi sitio web lo trabajo con un static site generator llamada `Sergey` que trabaja con puros html y documentos makdown es muy minimalista si haz trabajado con herramientas como next o como view press o como gadsby es algo así pero con con puro html plano "MENOS ES MAS" "mas que mas menos es mejor"


para muchas de las soluciones quenos propone Trys  hay que utilizar funciones y caracteristicas y unidades de medida de css que hasta cierto punto son relativamente nuevas es decir que no tiene no mas de 5 años soportandose en los navegadores, todas estas caracteristicas ya las hemos visto en los cursos de unidades y estilos css

la filosofia de Trys es muy buena

funcion clamp()

### Grid Fluida

```css
      /*Grid Fluida*/

  .fluid-grid{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    /*¿Por que no estoy especificando filas por que las filas se van a generar dinamicamente?*/
    }
.fluid-item{
    border: thin solid gray;
    padding: 1rem;
    }
```

### Textos Fluidos

hay dos estrategias

> La primera seria tener en consideracion varios tamaños de texto que yo pueda ir fluyendo

vamos a está  pagina: https://utopia.fyi/type/calculator/  y copiamos el código 

* nos declara 8 variables

* tendrian que modificar el tamaño del view port

```css
    /* @link https://utopia.fyi/type/calculator?c=320,18,1.2,1240,20,1.25,5,2,&s=0.75|0.5|0.25,1.5|2|3|4|6,s-l&g=s,l,xl,12 */

:root {
  --step--2: clamp(0.7813rem, 0.7747rem + 0.0326vi, 0.8rem);
  --step--1: clamp(0.9375rem, 0.9158rem + 0.1087vi, 1rem);
  --step-0: clamp(1.125rem, 1.0815rem + 0.2174vi, 1.25rem);
  --step-1: clamp(1.35rem, 1.2761rem + 0.3696vi, 1.5625rem);
  --step-2: clamp(1.62rem, 1.5041rem + 0.5793vi, 1.9531rem);
  --step-3: clamp(1.944rem, 1.771rem + 0.8651vi, 2.4414rem);
  --step-4: clamp(2.3328rem, 2.0827rem + 1.2504vi, 3.0518rem);
  --step-5: clamp(2.7994rem, 2.4462rem + 1.7658vi, 3.8147rem);
}

.step--2 {
    font-size: var(--step--2);
}

.step--1 {
    font-size: var(--step--1);
}

/* podria ser para h6*/
.step-0 {
    font-size: var(--step-0);
}
/* podria ser para h5*/
.step-1 {
    font-size: var(--step-1);
}
.step-2 {
    font-size: var(--step-2);
}
.step-3 {
    font-size: var(--step-3);
}
.step-4 {
    font-size: var(--step-4);
}
/* podria ser para h1*/
.step-5 {
    font-size: var(--step-5);
}
```

* Cuando conocí el sitio de https://www.trysmudford.com/ dije: esto es buen responsive elegante, minimalista estético 


de hecho si se acercan a 1200 que tiene de tamaño el contenedor quiero que vena que al final ya no cambia mas el texto ¿por que pasa esto? recuerda que el contenedor tiene una maxima anchura definida de 1200px entonces nosotros aumentamos el valor a 1200px con esto podemos crear una nueva variable(si, necesitan más tamaños).


![texto-fluido](/assets/texto-fluido.JPG)

* estos textos son responsivos, y la página jonmircha sigue estos principios de los textos fluidos que nos propuso Trysmudford 

* esta tecnica de los textos fluidos no solo aplica para el ``Font-size`` tambien aplica a valores de espaciado interno `margin y paddings` podrias aplicar estos valores guardados en las variables para que esas distancias tambien vayan siendo fluidas y no estáticas


**Hack para no generar varias clases** es de Ettan marcotte

```css
    body{
/*
    14 = tamaño de letra mas pequeño
    18 = tamaño de letra mas grande
    1400 = tamaño de viewport más grande
    300 = tamaño de viewport más pequeño (al tamaño de pantalla que tu texto ya va dejar de fluir)  
*/
font-size: calc(14px + (18 - 14) * ((100vw - 300px)/(1400 - 300)));
/* font-size: calc(12px + (24-12)*((100vw - 300px)/(1600 - 200))); */
}
```

> **tu eliges que te combiene,  si ir generando tus clases de tamaños e irselar agregando.step-2 a cada uno de tus elementos textuales o contenedores o que de buenas a primeras definas en el BODY los tamaños maximos y mínimos tanto de tamaños de letra como tamaño de viewport y veas ahi como las etiquetas van fluyendo dependiendo de tipo de etiqueta no va ser lo mismo un h1 que un parrafo**

>  ! "bastante cool"

> así es como podemos hacer textos fluidos y dejar de sufrir  con estar generando media querys para ir aumentando el tamaño de la letra de nuestros sitios.

Siguiente: cajas de elementos eje: una targeta que vaya fluyendo su tamaño dependiendo de la responsividad que vayamos teniendo del tamaño de la pantalla pero sin la necesidad de aplicar media querys sino con estás tecnicas del fluid design


### Contenedores Fluidos (cajas)

```css
    .box-fluid{
    width: 300px;
    height: 300px;
}
```

mira que la caja es estática y no fluida(responsiva) si le hubieramos puesto porcentajes seria responsiva

¿Como podria volver un contenedor en ancho y alto fluido? 

Pues nos vamos ayudar de la funcion Clamp(valor minimo, valor ideal,  el valor maximo) que es muy util en las tematicas de Fluid

* Esto se modifica solo en anchura pero para que haga efecto en altura lo redusco el viewpor en altura

* El tamaño va depender de lo que ese contenedor tenga [párrafo, targeta con sus elementos, su img, su titulo, su enlace, su descripcion, capas es un carrusel con sus imágenes]


```css
    /* .box-fluid{
    width: 300px;
    height: 300px;
} */

.box-fluid{
    width: clamp(400px, 60vw, 600px);
    height: clamp(200px, 30vh, 300px);
}
```

Vean que con estos 3 principios aprender a hacer grid responsiva, aprender a trabajar espaciados y tamaños de letra fluidos,  y aprender a trabajar los tamaños de cajas de manera fluida, practicamente estos son los 3 principios básicos del fluid design propuestos por trys mutford

### INTRODUCCION A LA ARQUITECTURA CSS

Te voy a enseñar las directrices para ordenar tu codigo CSS para que sea escalable y no se vuelva un caos a la hora de implementar nuevas cosas

* **Escribir CSS es facil, escalarlo y mantenerlo no tanto**

para mentener nuestro codigo organizado necesitamos un plan:

* **La arquitectura CSS** Que es el arte y tecnica de siseñar, proyectar y construir edificios y espacios públicos

* **Tecnicas que nos ayudan  a organizar y mantener nuestro código ordenado, óptimo y escalable** por que no sabes cuando un proyecto que tu hayas iniciado muy sencillo derepente tenga exito y derepente tenga que escalar exponencialmente, si tu desde un unicio comienzas trabajando con buenas prácticas teniendo una arquitectura de CSS  un "PLAN" no tienes que tener un problema de que tu código se vuelva un caos

**Una buena arquitectura de css debe ser:**

1. Predecible (frameworks como bootstrap o tawlin llamados "utilities first" nos ofrecen muchas clases utilitarias de estas que afectan a un valor en particular en css) esperar que haga lo que dice que hace y lo haga

2. Reutilizable (que se pueda usar en distintas secciones sin estar afectando a otros elementos)

3. Estable (deberias poderlo modificar sin afectar otras reglas)

4. Escalable (tu codigo debe ser facil de mantener) la hoja de estilos de cada uno de sus proyectos es como si fuera un diccionario en el cual ustedes van a ir definiendo clases, yo les sugiero que vayan definiendo clases untilitarias{tipos de clases que solo hacen una sola cosa en particular} el html se vuelve muy textoso segun puristas, pero está bien, por que finalmente eso se espera de una ariquitectura de css, de hecho lo que puedes ir haciendo sobre todo si no te gusta trabajar con frameworks como bootstrap fundation tailwind y te gusta crear tu propio codigo css no pierda tu tiempo, si tu empiezas creando una arquitectura css escalable reutilizable... imaginate que en tu primer proyecto generaste 100 clases utilitarias como esas clases utilitarias pueden ser reutilizables en otro proyecto cuando tu crees un segundo proyecto pues que crees esas 100 clases te las puedes copiar al siguiente proyecto y utilizar las que te sirva seguramente vas a crear más entonces para el 3re proyecto quizas ya tienes 120  con forme tu vayas generando proyectos vas a ir haciedote de una base de clases utilitarias que tu haz creado y con el tiempo se puede volver un mini framework propio que tengas para porder maquetar proyectos

**Debemos pensar siempre: en diseñar SISTEMAS, no PÁGINAS**

Si tu sueles diseñar tus páginas pensando solamente pensando en las necesidades del proyecto entonces dejame decirte que estas haciendo "malas practicas" en el sentido de que inviertes mucho tiempo cada vez que empiezas un proyecto por que cuando empiezas un proyecto empiezas como a maquetar las caracteristicas que el cliente o la propuesta visual que te hayan dado:

ejemplo de malos selectores:

.cabecera. , .contenido-principal, targeta-principal

.menú-principal.

y empiezas a definir todo los estilos, estás pensando solo en el diseño que en ese momento tienes que bien podira ser la interfaz de un curiculum personal, de una empresa que vende productos, de una empresa que ofrece servicios, de una persona influencer entonces lo que tienes que entender es que **"NO diseñes desde lo particular diseña de lo general"** obiamente que cada proyecto tiene sus particularidades pero vas a partir de una base genérica donde sabemos que todo los sitios tiene menú de navegacion que toda las interfaces tienen cabecera que toda las interfaces se pueden acomodar en sistemas de columnas que dependiendo del tamaño de la pantalla puede ser que vayas a una columana a 2 columnas a 3 columanas.

Desde ahora trata de tener una vision más genérica. por que vas a poder usar frameworks como bootstrap taiwlin por que ya te ofrecen una base preexistente y probada 

Si eres muy purista y te gusta maquetar  tu codigo CSS propio pues sé inteligente y en  el primer proyecto trata de ir creando esa base de un pequeño miniframework que tu tengas y conforme vayas pasando de un proyecto a otro ese framework lo vayas enriqueciendo y vaya siendo escalable y reutilizable...

> cada vez que abordes un nuevo proyecto de maquetacion no pienses en ese proyecto en particular piensa en diseñar sistemas

> independientemente del proyecto que estés trabajando en turno pues todo los proyectos a nivel de maquetacion tienen los mismos elementos: "layout,  manejan módulos,componentes, estádos, hover, focus, disable, podemos manejar temas tema oscuro, tema claro, ciertas areas de maquetacion: (cabecera, menú, contenido lateral, contenido principal, columnas)"

por que si estás pensando en páginas y proyectos particulares estas perdiendo mucho tiempo a la hora de maquetar


**COMPONENTES**

es un patron visual que se repite, que puede ser abstracto, es independiente, tiene parte de html, css y posible js

de las estrategias de maquetacion multidispositivo, te hablaba de que con el devenir de las tecnologias como react angular vue.js se dio todo esto de la programacion orientada a los componentes, los web-components es un estandar de JS  no está bien estandarizado estamos a nada de hacer componentes web con puro vanilla JS 

bootstrap y tawlin nos frecen una gama de componentes dentro de su documentacion: targetas, carruceles, acordeones, botones, tamaños de textos.

**DIVIDE Y VENCERAS**

"don't Repeat Yourself"

como un componente es un patros visual repetitivo: de un home de un blog, cada targetita representa la entrada hacia un artículo de un blog 

- cumple una sola funcion:  por que si ya comienza a cumplir mas de una entonces es ahi donde literalmente todo se vuelve un relajo, que solo haga una cosa pero que la haga muy bien.

- Son independientes: 

- Son autocontenidos: no permiten que elementos externos afecten su estructura interna, y sus componenetes internos no afectan  los elementos de afuera

- Son reutilizables

> la ventaja de empezar a diseñar pensando desde lo general y poco a poco irte hacia  las partes específicas de cada proyecto

el bloque seria la cabezera un elemento seria el logotipo, el formulario de autenticacion

**HERRAMIENTAS CSS PARA CREAR SISTEMAS**

1. Metodologias
2. Frameworks
3. Procesadores
4. Guias de estilos


### Metodologias CSS

Son buenas prácticas, es una manera de la organizacion del código y nombrar el código

la mayoria empesaron como articulos y terminaron siendo libros

son propuestas que otros colegas profecionales han planteado han tenido buena aceptacion. cada una de ellas al final  todas tratan de tener un codigo css mas legible, mas organizado y entendible escalable

- **BEM bloque**  (es muy verboso) yo lo que hago es un nombre de clase al componente principal y apartir de ahi con la ayuda del selector desendiente espacio en blanco empiezo a a plicar los estilos, "TOMA LO QUE TE SIRVA" no me gusta.

- **SMACSS modulos** una regla de estado podria ser: habilitado, desabilitado, con el foco de la página, theme Rules (modo oscuro, modo claro)

![desmenusado](/assets/desmenusado.JPG)

- **OOCSS objeto** piensa que todo en css es un objeto que es el mismo concepto de componente

- **ITCSS** si trabajas en equipos de desarrollo  ya tendran cierta metodologia a la que tendras que adaptarte y puede que sea una metodologia que ellos fueron creando

- **AMCSS** tienes que mandar a llamar una libreria JS usa data-attribute

- **SUITCSS lo llama componente** {bloque, componente, elemento} es lo mismo no? usa clases "utilitarias" 

- **atomic design** es una de las metodologias que mas me ha gustado  tiene un stared en php y ademas ya tiene un estarter en NODE por que puedes instalar via node NPM  https://demo.patternlab.io/ 

![atomic](/assets/atomic-web-design.JPG)

Yo ninguna de estas metodologias las sigo al pie de la letra sino que trato de tomar lo mejor de cada una

**van hacia lo mismo dividir y mejorar el código mas organizado, con nombres alucivos a lo que aplica**

### Frameworks CSS 

Son **marcos de trabajo** (traducido al español) que nos ofrecen componentes y utilidades de UI. "no vamos a empesar desde 0" generalmente ya nos ofrecen sus hojas de estilos y su archivo de programacion js. 

- **960Grid System** mantenido por twiter

- **Skeleton** kit de inicio reticula a 12 columnas

- **PureCss** librerias o kit de inicio

- **INK** la mayoria de estos frameworks  tanto en codigo css y como en código SASS. tiene la metodologia como de smaks, yo no soy fan de modificar con SASS estos frameworks por que cuando se actualizan esos cambios que tu ya pusiste ya no van a tener efecto. yo prefiero trabajar con lo que me dá el framework a nivel de CSS y despues yo ir modificando con código css puro las caracteristicas que yo considere que pueda modificar de un framework

- **MUI** Está basado como materialcss en el leguaje visual de google si tu trabajas con angular con react con vue.js puedes implementarlo de una manera muy amigable a tu stack de trabajo, estos frameworks ya se pueden adaptar a un stack de flujo de trabajo frontend.

- **Semantic UI** bootstrap y fundation aunque son los mas populares todavia siguen usando div div div...  para todo elementos = Componentes

- **Bulma** es un framework CSS moderno usa solo css

- **UIkit** se ha vuelto muy popular entre programadores de REACKT,  no tiene nombres genéricos, la mayoria de sus clases empieza con `UK` está escrito con 2 preprocesadores, less y Sass no te recomiento tocar las tripas de uikit

- **Materialize** 2004 solo tiene 2 versiones dejó de usar jquery. es para proyectos muy pequeños, por que no lo actualizaron hace años

- **foundation** las primeras grids fueron hechas con floats el codigo html para email marketing es muy diferente al que tenemos para navegadores el html para los clientes de correo no ha avanzado usa mucho la metodologia SMACSS le falta a nivel de componenetes.

- **Tailwind** es facil de implementar en cualquier flujo de trabajo independientementes si estas trabajando con la libreria Reack, angular quizá con alguna otra tecnologia laravel, en las vistas que te genera laravel, php, .net cada vez que escriban su código CSS haganlo lo mas semántico posible. para muchos puristas esto es mala práctica, yo no lo veo de esa manera, si tu tienes un exelente dominio de css te vas adaptar facilmente, estos frameworks se llaman utilities first por que su funcionamiento se están basando en clases utilitarias(aquella clase que solo aplica un valor en particular). lo puedes instalar via npm, tiene una configuracion muy parecida a webpack(un flujo de trabajo) tailwind tiene su propia CLI su propia interfaz de linea de comando, no te recomienda usar Tailwind via CDN. cuando tengas mas experiencia en JS, en ejecutar entornos de programacion con webpack o utilizando (framework)angular o (libreria)reack no te preucupes despues vas a poder instalar el framework de Tailwind _Tailwind se volvió muy popular por que está muy orientado a los flujos de trabajo que los front developers trabajamos con este tipo de herramientas (reack, angular, vue, webpack)_ está mas orientado a este tipo de flujo de trabajo que al tipico manda a llamar la hoja de estilos.

> vue.js está orientado a componenetes.

> next.js es un framework de react para hacer react a lado del servidor


- **Bootstrapt** fue creada por gente de twiter, sigue siendo mantenido, es muy popular por que muchas plantillas de wordpress, si tu te vas a sitios donde puedas comprarte plantillas html plantillas de wordpress plantillas de drupal plantillas de jumla, de estos CMSs la mayoria de esas personas que se dedican hacer plantillas para estos cmss pues han usado mucho bootstrapt se ha mantenido a lo largo de más de una década, en la version 4 bootstrap usaba jquery hoy en dia ya dejó las dependencias de jquery, ya trae su propia libreria de iconos, lo puedo descargar en fomato SVG para llamarlo dentro de SRC de una imágen, lo puedes usar como Icon-fonts hay que llamar la tipografia de los iconos de bootstrap, lo mejor es que lo puedes copiar nativamente la etiqueta SVG y pegarla en tu codigo html, ademas de que tienen iconos de las tipicas redes sociales: fb ig, youtube ... para usar bootstrap simplemente hay que mandar a llamar la hoja de estilos y el archivo de JS, adicionalmente utilizan una libreria popper para algunos efectos que tiene que ver con tooltips o elmentos superpuestos, te da la opcion de llamarlo, Trae un flujo para que tu puedas instalarlo y configurarlo a tu gusto tanto con: Webpack y Parcel que son herramientas de automatizacion, entonces ve como podrias importar bootstrap desde incorporarlo a un flujo de trabajo que tengas con webpack, actualmente el código fuente de bootstrap está escrito en SASS entonces podrias meterte a las tripas y cambiar la configuracíon, y están separados en capas, si tu revisas las hojas de estilos de bootstrap ya trae un buen de custop propertis variables css ya definidas, en la opcion de Sass está dividido en capas, si tu quisieras para un proyecto tu color primario fuera un verde pues cambias el código en el SASS compilas y listo tendrias funcionando de manera personalizada la hoja de bootstrap o podrias modificar con simplemente con puro código css, una de las ventajas es que la grid de bootstrap funciona con flexbox, tiene una gran cantidad de componentes(formularios) en la parte de Helpers(clasees auxiliares) fixed-top, fixed-bottom, Sticky-top, Bootstrap y Tailwind premian a las personas que saben css a fondo con las utilidades(Components) y helpers por que eje: eso del 

>> Helpers: Stiky position que es un tema avanzado no lo va saber un novato que nada más sabe copiar y pegar el código html de los componentes de bootstrap modificar el texto domi, la imagen https://getbootstrap.com/docs/5.3/helpers/position/ ahora ve la parte de las...

>> utilidades: tiene utilidades de flexbox "en todo los tamaños", pero si tu no sabes flexbox dificilmente le vas a sacar provecho a estas clases utilitarias que ya nos ofrece bootstrap, ve que están mapeadas toda las propiedades a lado derecho como en un indicé.

>> entonces si tu haces una interfaz de usuario con bootstrap y necesitas aplicar flexbox pues ya nada mas es cuestion de que te aprendas los nombres y no es la gran cosa: `align-items-sm-center`(align_items-tamaño_de_la_mediaquery-valor) 

>> `https://getbootstrap.com/docs/5.3/utilities/spacing/` este es el espaciado el valor auto no lo podemos aplicar para el padding.

>> cuando hablamos de margin y padding hablamos del modelo de cajas 

Por eso cre que bootstrap es y seguirá siendo el rey de los framewoks en Css por que no solo nos da el codigo html de los componentes ya preestablecidos como: una barra de navegacion, o una targeta o un carrusel, porque tambien maneja buenas prácticas a nivel de accesibilidad(para personas con discapacidades diferentes). 

Una de las cosas que adolece es que la mayoria de los componentes usa mucho la div como los demas frameworks que yá está cambiando. por ejemplo la barra de navegacon nav ya es más semantico, las mediaquerys sigue trabajando con pixeles. 🤔🤔🤔 

### Concluciones de frameworks

tu tienes que comparar: quieres agilidad y velocidad a la hora de desarrollar interfaces o quiers clavarte en tu ego y decir yo todo lo voy hacer artesanalmente, talvez aya proyectos donde si valga la pena y hasta sea formativo para tí  hacer todo el código CSS eje: piensa en tu sitio personal, pero cuando ya estoy trabajando en proyectos de clientes donde sé que tal herramienta tal libreria tal framework me van agilizar el tiempo de desarrollo pues adelante utiliza estas herramientas pero ***"ANTES DE USAR ESTOS FRAMEWORKS CONOSCAN LAS BASES DEL LENGUAJE"*** es decir conoscan las bases de html y de CSS hasta cierto punto es incuerente utilizar este tipo de herramientas pues cuando no tenemos los fundamentos base.
El framework que uses va depender en el proyecto que tu estes desarrollando, entonces dependiendo de las necesidades y caracteristicas de los proyectos que afrontes entonces decide utilizar uno u otro, no necesitas casarte con un framework, trata de ir identificando dependiendo de las necesidades. Mi intencion es que aprendas a dicernir que dependiendo de las necesidades del proyecto será el framework con el que decidas trabajar y para sacar el provecho a estos frameworks tienes que si o si **dominar los fundamentos de css y los modelos de maquetacion(flexbox y grid)**

### ¿Como elegir un Framework CSS?

depende de las necesidades del proyecto, puedes usar materialcss para formularios, o para un proyecto que no necesita responsividad usa botstrap, php, react, api.

Y de igual manera,  si trabajas para una empresa para un equipo de desarrollo pues seguramente te tendras que adaptar al stack de tecnologias y herramientas que en ese equipo esten trabajando.

### Procesadores CSS

- `Preprocesadores`

> Son herramientas que toman un lenguaje y lo transforman en CSS, son metalenguajes

> nos permiten tener mejor organizado el código css

> si tu revisas la parte de Sass de Bootstrap hay un archivo para cada uno de los componentes y cuando ya compilamos este código del preprocesador eje: sass al final nos queda una hoja de estilos mimificada, _todo esto lo puedes ver en el github de bootstrap_ Nesting es una de las cosas que solo los preprocesadores me permitian tener, pero W3E ya lo incluyó a css y actualmente ya está soportada por el 99% de los navegadores.

> nos permite la creacion de funciones(Mixins) 

> todos estos Preprocesadores nos permiten dividir en archivos https://github.com/twbs/bootstrap/blob/main/scss/bootstrap.scss 

> Si estas desarrollando un framework un preprocesador te va permitir una mejor estructura una mejor organizacion un archivo por cada uno de los componentes. y al final cuando el preprocesador compila, nos va generar una sola hoja de estilos que es la que vemos en el CDN que nos comparten cada uno de los frameworks
> la mayoria son paquetes de Node.js y tenemos que instalarlas via npm

> Estas herramientas hace que yo pueda generar código dinámico. sin repetir codigo css

> todo lo que te permite escribir estos preprocesadores al final tu lo puedes escribir con código puro por eso no soy fan de estas herramientas.    

> lee la documentacíon, y domina los conceptos de CSS

* Sass. es una gema(paquete de Ruby) descargas el lenguaje de programacion de Ruby y luego via terminal instalar Sass, tanbien hay un clon para npm de Node.js su sintaxis scss es mas parecida a css

* Less.

* Stylus. usa un lenguaje muy declarativo como phyton, es un meta lenguaje que los navegadores no entienden y cuando compila genera css que si entiende el navegador

- `Post procesadores`

> Son herramientas que procesas en css y lo optimizan y automatizan.

> un ejemplo es la mimificacion de la hoja de estilos

> autoprefixer fue el que inicio todo esto del post procesamiento https://autoprefixer.github.io/ 

> es un paso adicional que no te va optimizar muchas cosas

* `Post CSS` una herramienta que transforma css con JS.

* `CSS Next` muchas de las caracteristicas ya se soportan en css

* `CSS in JS` esto se está popularizando mucho ya que es la forma en la que muchos frameworks como vue.js, react estan escribiendo css dentro de JS.

>> si tu haces sitios web normalitos con html, css y js no vas a tener la necesidad de hacer esto pero si eres mas un frontend developer y usas los frameworks como vue.js, angular, react, esta va ser una forma de crear los estilos de tus aplicacines

>> para el manejo de estas herramientas necesitas conocimientos de javaScript de la manipulacion de la terminal.

### Herramientas de Automatizacion.

Es para utilizar estos Preprocesadores  y post procesadores

**Build Tools**

* `Node.js` Es un entorno de programacion de Js nos permite ejecutar JS en el lado del servidor y tambien nos sirve para la gestion de dependencias en el front como Sass less... 

* `Grunt` me permite crear una rutina para escuchar el archivo que estoy compilando y despues me genere un codigo sass

* `Gulp`

* `Webpack` es una herramienta del ecosistema de la libreria javaScript llamada React, Webpack es el software que se necesita para configurar y leventar un entorno de programacion en react, prodria compilar toda la programacion de mi aplicacion javaScript en un solo archivo JS sirve tanto para Sass, .png...
>> te permite levantar un servidor de pruebas, te permite optimizar imágenes, 

> para todas estas herramientas necesitas el uso de la terminal "no te agovies" va llegar su tiempo para cuando tu decidas aprender este tipo de cosas lo importante es aprender las bases de las 3 tecnologias: **HTML, CSS, JAVASCRIPT** enfocate 🎯 en aprender las bases 

**Online Tools**

> no te estreses, el codigo lo pasan a autoprefixer, despues lo mimifican (buenas practicas?)

* **``CODEPEN.IO``** es un sitio donde puedes generar pequeños proyectos que tengan html, css y javaScript. es como un editor en linea y aparte puede compartir tu código. https://codepen.io/ 

* `JS Bin`

* `Autoprefixer CSS` https://autoprefixer.github.io/

* `CSS Minifier` https://www.toptal.com/developers/cssminifier 


### Guias de Estilos

Colección  de elementos y reglas pre establecidas que aseguran la consistencia y coherencia de nuestro código.

> en empresas mas grandes hay gente que se dedica a definir los lineamientos de las tecnologias que van a emplear

- lenguajes de programacion

- frameworks

- generacion de funciones, lineamientos para generar/definir: selectores, marcado de html, formato a las imágenes.

Las gias de estilo aplica a todo los lenguajes y a toda las tecnologias

> !recuerda _el objetivo de la arquitectura css es tener un codigo ordenado que pueda ser escalable,  que sea predecible, reutilizable_

las guias son recomendaciones de profecionales más experimentados: 

* [***Code Guide*** ](https://codeguide.co/) estandar te dá buenas prácticas para escribir código html,css .

* ***W3C Design System***

* ***Website Style Guide*** es como un repositorio de otras páginas

* ***Airbnb CSS / Sass Styleguide***

* [***Idiomatic CSS***](https://github.com/necolas/idiomatic-css)cuando tienes varios selectores no los definas en una sola linea  para tener mayor legibilidad, no mesclar sistemas de colores 

* ***CSS Guidelines*** es una guia

La intencion de estas guias es colaborar con la comunidad y darnos una serie de lineamientos independientemente del lenguaje que estes trabajando siempre va existir _mark Otto_

### ¿Que erramientas uso?

si vas empesando preucupate por dominar las bases de html, css, js

Hoy en dia hay muchos frameworks, librerias

quisa el mejor camino es empesar por el frontend dominar html para el contenido,  dominar css para la presentacion, js para la parte de la programacion. conforme vayas ganando experiencia te vas a dar cuenta que es lo que mas te gusta front(interaccion, programacion) o te gusta mas lo abstracto backend, base de datos,  administracion de servidores, redes,yo creo que un buen punto es empesar por el frontend por que independientemente tu te especialices en db, en entornos de produccion, en administracion de nubes siempre va servir mucho que tu sepas frontend el que tengas nociones de html, css javascript por que finalmente lo que los usuarios de las aplicaciones lo que el usuario ve es lo que los navegadores le permite interpretar pues en ese sentido trata de dominar ***html, css, javaScript***  con forme vayas avanzando ve implementando tecnologias como frameworks, traten de crear proyectos personales,  proyectos de familiares que les permitan empesar a poner en practica todos estos conocimientos y en esos pequeños proyectos personales que les van a servir para crecer y ganar experiencia traten de implementar diferentes tipos de tecnologias un proyecto haganlo con css artesanal,  ya que dominen css artesanal pasense algunos frameworks como Bootstrap, y con un poco más de conocimiento con la terminal con estos entornos de programacion como Node.js herramientas como WebPack pues empiezen a integrar estas herramientas como procesadores y post procesadores leanse dede un **inicio** alguna de estas guias de estilos, tambien lean alguna de las **metodologias que vimos**  para la organizacion del código css y poco a poco conforme vayan conociendo estas tecnologias traten de irla implementando pero __No se casen con ninguna__  por que puede ser que en un futuro esa tecnologia o herramienta ya no exista. pero lo que nunca he visto caer son las tecnologias base : "html, css y javaScript" Centrense en dominar estas bases, tambien va depender mucho  de hacia donde los lleve su via profecional, si deciden integrarse como miembros de un equipo de desarrollo de una empresa, de una consultoria pues seguramente se tendran que adaptar a las herramientas que usen. vas a conocer personas que hasta cierto punto van a fungir como mentores que te puedan ir orientando en cualquier duda que tu vayas a tener, si te pasas a otros mundos como las bases de datos el lenguaje de programacion a lado del servidor te vas a dar cuenta que en todos lados mas o menos se sigue los mismos principios siempre va ver librerias, frameworks, herramientas guias de estilos para mejorar nuestro flujo de trabajo en todo momento 

siguiente: te voy a enseñar una arquitectura que he creado para mis proyectos presonales, medianamente complejos que uso a nivel de Css y que me ha dado resultado no significa que sea la tuya

### Arquitectura Minimalista

* agarro una sola hoja de estilos y genero estos 5 comentarios

* los comentarios con más asteriscos me permite detectar donde se encuentran las seciones


```css
    /* ********** Custom Properties ********** */
/* ********** Reset ********** */
/* ********** Components ********** */
/* ********** Utilities ********** */
/* ********** Site Styles ********** */
```

1. defino las variables css que voy a usar y las defino en el selecor Root.

2. reseteo no utilizo las hojas de estilo como __reset o normalize__ lo que reseteo es el box-zising y apartir de ahi aplicar una serie de estilos muy particulares a algunas etiquetas que esos estilos los voy a querer a lo largo de las etiquetas

3. componentes. los defino eje: cabezera, menú de navegacion, una targeta, 

4. tengo una zona de utilidades muy al estilo de Bootstrap una regla que modifica un atributo o una propiedad de css 

5. ya ya tengo una seccion donde tengo los estilos particulares de cada proyecto

Esto contribuye al concepto de : _Debemos diseñar Sistemas, no Páginas_  por que yo puedo construir una base de ciertas variables que pueda utilizar de un proyecto a otro y tenerlas definidas en mi seccion de Custom propertis lo unico que de un proyecto vaya desechando es los estilos particulares de cada sitio o proyecto de tal manera eso me permite hacer como mi propio framework, que no me hace iniciar todo de 0 esto de la arquitectura lo he hablado en mi taller de maquetacion

cuando desarrollo proyectos pequeños, esta arquitectura de css minimalista quiza sea una opcion a toda esta boragine de informacion (metodologias, guias de estilo, y herramientas) como para que tu puedas comenzar  con tus proyectos bajo estas directrices.

### ¿Que sigue?

te suguiero seguir con el curso de figma, toma el curso de maquetacion, javascript