# Expresiones

En **C**, y en cualquier lenguaje de programación, todo se indica a través de expresiones, trataremos las expresiones más habituales como los comentarios, sentencias, bloques, ...

> No te preocupe si no entiendes lo que está escrito en los ejemplos. Por ahora lo importantes es que diferencias los distintos tipos de expresiones. Ya iremos tratando el contenido a lo largo del curso.

## Comentarios

Los comentarios son usados en documentos para explicar el código o la lógica de la aplicación. Los comentarios no son expresiones de programación y son ignorados por el compilador, aun así son MUY IMPORTANTES para informar y explicar el código.

Hay dos tipos de comentarios:

- Comentarios multi-línea: se insertan con los símbolos `/*` indicando que todo lo que sigue es comentarios hasta `*/`.
- Comentario de línea: empieza con `//` hasta que finaliza la línea.

Ejemplo:

```c
#include <stdio.h>

/*
Esto es un comentarios multilinea
*/
int main()
{
    // Esto es un comentario de una línea
    printf("Hola Mundo");

    return 0
}
```

## Sentencias

La **sentencia** es la únidad de programación más pequeña. Esta desarrolla un pedazo de acción en la programación. Cada sentencia tiene que finalizar con un punto y coma `;` (igual que el punto en una frase coloquial).

Ejemplo:

```c
int numero1 = 2;
int numero2, numero3 = 99;
int producto;
producto = numero1 * numero2 * numero3;
printf("El producto cuesta %i", producto);
```

## Directivas

Un tipo especial de sentencia son las **directivas de preprocesador**. Las directivas permiten al compilador insertar código de archivos externos, asignar constantes, etc.

Se declaran al incluir el símbolo `#` al principio de la sentencias y no llevan `;` al final.

```c
#include <stdio.h>
// Hemos usado la directiva include para añadir la librería stdio.h

int main() {}
```

## Bloques

Un **bloque** es un conjunto de sentencias agrupadas entre llaves `{ sentencias }` de tal manera que ese conjunto es tratado como una unidad cuando se produzcan las condiciones que lo ejecuten.

El uso de bloques los veremos en las funciones, condicionales, bucles, etc. Por ejemplo:

```c
int x = 10;

if (x == 10)
{
    // se ejecuta si X = 10
    printf("La variable X es igual a 10");
} else {
    // se ejecuta si X no es 10
    printf("La variable X no es igual a 10");
}
```

## Funciones

Una **función** es un bloque al que se le ha asignado un título y que realiza algo. Cada vez que llamas a la función en el código, se ejecuta el contenido del bloque.

La función más importante es `main()` ya que es la que se ejecuta al iniciar la aplicación.

> De momento quédate con lo que significa una función, ya las trataremos adelante con más detalle.
