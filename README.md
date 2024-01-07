

# _FUNDAMENTOS CSS_

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
## Modelo de Caja

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
  2. Derecha (right)
  3. Abajo (bottom)
  4. Izquierda (left)
