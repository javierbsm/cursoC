# Función `main()`

Es la función más importante de todas ya que es la que se ejecuta al iniciar la aplicación. Tal es asi, que si en ella no invocamos otras funciones que se hayan declarado previamente, no se ejecutarán nunca.

La función `main()` también acepta parámetros que serán datos que se pasarán a la aplicación en el momento de ejecución por consola. 

Pero sólo acepta dos parámetros, uno que indica el número de parámetros recibidos y otro que es un array con la lista de parámetros. Estos son el entero `argc` (**arg**ument **c**ount) y el array de constantes `argv` (**arg**ument **v**alues).

>Se puede nombrar de manera distinta los argumentos de `main()`, pero esta es la costumbre.

Veamos un ejemplo:

````c
#include <stdio.h>

// Aplicación "suma" que muestra en pantalla la suma  
// de los números enteros pasados a la aplicación.

int main(int argc, char const *argv[]) {
    int suma;

    printf("%i + %i es igual a %i.\n", argv[0], argv[1], argv[0] + argv[1]);

    return 0;
}
````

Si ejecutásemos la aplicación pasandole dos números, tendríamos:

````bash
$ ./suma 4 9
4 + 9 es igual a 13.
$ 
````

>Este es un ejemplo de ejecución en Linux, si lo hicieras en Windows, no sería necesario utilizar el `./` para ejecutar la aplicación.