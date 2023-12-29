



# FUNDAMENTOS CSS
## INTRODUCCION A CSS

CSS es un lenguaje de definicion de estilos, es la presentacion de los documentos html.
css no es un leguaje de programacion, pero tiene caracteristicas propias de lenguaje de programacion.
debemos empesar a despertar cierta logica para porder crear ciertos efectos visuales, llamado tambien arte digital atraves de css.

## SINTAXIS BASICA.

Una regla de CSS consta de 2 partes
1 _*selector*_- es el elemento html al que nosotros podemos aplicarle el bloque de declaracion de estilos, y un selector podria ser cualquier etiqueta html, ele selector mas basico son las etiquetas.
2 _*Bloque de declaraciones*_
    //Es cada uno de los atributos que vamos a modificar.
    {
        atributo: valor.
        atributo-de-mas-dos-palabras: otro-valor
    }

## COMENTARIOS EN CSS.

/**/este seria un comentarios en css

## FORMAS DE INVOCACION.

Hay 3 formas de invocarlos.
* internamente dentrod el documento Html.
* en linea (en la propida etiqueta).
* mediante una hoja externa (que es lo ideal)
Es una mala practica importar en CSS son bloqueantes a la hora de que el navegador lee esta instruccion.
no es mala practica para preprocesadores como SAS