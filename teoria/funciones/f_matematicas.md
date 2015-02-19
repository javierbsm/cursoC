# Funciones matemáticas

Ahora trataremos varias de las funciones matemáticas más habituales como son las funciones trigonométricas, exponenciales, logaritmicas, etc. y la generación de números aleatorios muy usados para ejercicios de probabilidad.

## Funciones en `math.h`

La librería de cabecera `math.h` dispone de las siguientes expresiones matemáticas:

|   Función    | Descripción                   |
|:-------------:|:-------------------------------|
|   `sin(x)`    | seno de X                      |
|   `cos(x)`    | coseno de X                    |
|   `tan(x)`    | tangente de X                  |
|   `asin(x)`   | arcoseno de X                  |
|   `acos(x)`   | arcocoseno de X                |
|   `atan(x)`   | arcotangente de X              |
| `atan2(y, x)` | arcotangente de Y/X            |
|   `sinh(x)`   | seno hiperbólico de X         |
|   `cosh(x)`   | coseno hiperbólico de X       |
|   `tanh(x)`   | tangente hiperbólica de X     |
|  `pow(x, y)`  | potencia de X elevado a Y      |
|   `sqrt(x)`   | raíz cuadrada de X            |
|   `ceil(x)`   | entero mínimo no inferior a X |
|  `floor(x)`   | entero máximo no mayor a X    |
|   `fabs(x)`   | valor absoluto de X            |
| `fmod(x, y)`  | resto de la división X/Y      |
|   `exp(x)`    | número E elevado a X          |
|   `log(x)`    | logaritmo en base E de X       |
|  `log10(x)`   | logaritmo en base 10 de X      |

>**NOTA**: Las funciones angulares se expresan en radianes.

## Números aleatorios

La generación de números aleatorios es de gran utilidad para la estadística, la  probabilidad, simular el lanzamiento de dados, etc.

La función que se utiliza para obtener números aleatorios es `rand()`, incluida en `stdlib.h`, que devuelve un número aleatorio entre `[0, RAND_MAX)`. La constante RAND_MAX está incluida en `stdlib.h` y cuyo valor es al menos `32767`.

Si prefieres generar un número aleatorio contenido en un rango más reducido, sea `[0, n)`, entonces usarías la expresión `rand() % n;`.

Ejemplo:

````c
#include <stdio.h>
#include <stdlib.h>

int main() {
    printf("La constante RAND_MAX es igual a %i.\n", RAND_MAX);
    printf("Aleatorio entre 0 a %i: %i.\n", RAND_MAX, rand());
    printf("Aleatorio entre 0 a 100: %i.\n", rand() % 100);

    printf("Diez nº aleatorios: ");
    for (int i = 0; i < 10; i++) {
        printf("%i ", rand() % 100);
    }
    printf("\n");
    return 0;
}
````

Un inconveniente de `rand()` es que la elección de números aleatorios se realiza en el momento de compilación, por lo que cada vez que ejecutes la aplicación siempre devolverá los mismos valores. Para reinicializar el generador de números cada vez que se invoque disponemos de la función `srand()`, incluida también en `stdlib.h`, que tradicionalmente se realiza con el tiempo obtenido mediante la función `time(0)`, incluida en `time.h`.

Ejemplo:

````c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    printf("Números aleatorios: ");
    srand(time(0));
    for (size_t i = 0; i < 10; i++) {
        printf("%i ", rand() % 100);
    }
    printf("\n");
    return 0;
}
````
