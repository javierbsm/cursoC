# Ejercicios

## Lista de ejercicios

<!-- MarkdownTOC -->

- [Mostrar texto](#mostrar-texto)
    - [Mostrar parrafo en pantalla](#mostrar-parrafo-en-pantalla)
    - [Mostrar caracteres especiales](#mostrar-caracteres-especiales)

<!-- /MarkdownTOC -->

## Mostrar texto

### Mostrar parrafo en pantalla

Escribe una aplicación que muestre el siguiente párrafo en pantalla:

````text
En un lugar de la Mancha, de cuyo nombre no quiero
acordarme, no ha mucho tiempo que vivía un hidalgo de los de
lanza en astillero, adarga antigua, rocín flaco y galgo
corredor. Una olla de algo más vaca que carnero, salpicón
las más noches, duelos y quebrantos los sábados, lentejas
los viernes, algún palomino de añadidura los domingos,
consumían las tres partes de su hacienda.
````

Solución:

````c
#include <stdio.h>
#include <stdlib.h>

int main() {
    printf(
        "En un lugar de la Mancha, de cuyo nombre no quiero\n"
        "acordarme, no ha mucho tiempo que vivía un hidalgo de los de\n"
        "lanza en astillero, adarga antigua, rocín flaco y galgo\n"
        "corredor. Una olla de algo más vaca que carnero, salpicón\n"
        "las más noches, duelos y quebrantos los sábados, lentejas\n"
        "los viernes, algún palomino de añadidura los domingos,\n"
        "consumían las tres partes de su hacienda.\n"
    );

    system("PAUSE");
    return 0;
}
````

### Mostrar caracteres especiales

Escribe una aplicación que muestre el siguiente dibujo en pantalla:

````text
          '__'
          (oo)
  +========\/
 / || %%% ||
*  ||-----||
   ""     ""
````

Solución:

````c
#include <stdio.h>
#include <stdlib.h>

int main() {
    printf(

    );

    system("PAUSE");
    return 0;
}
````
