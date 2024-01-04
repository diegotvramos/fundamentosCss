

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

´´´html
    <ul>
                <li><a href="" target="_blank">Inicio</a></li>
                <li><a href="" target="_blank">Cursos</a></li>
                <li><a href="" target="_blank">Blog</a></li>
                <li><a href="" target="_blank">Cv</a></li>
                <li><a href="" target="_blank">Ahora</a></li>
                <li><a href="" target="_blank">Notas</a></li>
    </ul>
´´´

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

