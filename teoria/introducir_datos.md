# Introducir datos

Podemos pedirle al usuario de la aplicación en cualquier momento que inserte datos que pueden ser almacenados en variables. Por el momento trataremos la introducción de números y caracteres ya que es lo único que se puede almacenar en las variables.

## Recoger dato con `scanf()`

La función `scanf()` permite a la aplicación recoger el último valor introducido en teclado por el usuario.

Veamos como se utiliza a través de un ejemplo:

````c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int num1;

    printf("Introduzca un número: ");
    scanf("%i", &num1);
    printf("\nHa introducido el número %i.\n", num1);

    system("PAUSE");
    return 0;
}
````

Esta aplicación mostrará `Introduzca un número: ` y esperará a que el usuario teclee un dato y presione `ENTER`, una vez lo haga, `scanf("%i", &num1);` recogerá lo introducido por teclado, lo convierte a dato y lo asigna a la variable `num1`.

Por ejemplo, si ejecutaramos la aplicación, tendríamos:

````text
Introduzca un número: 10
Ha introducido el número 10.
````

Fíjate que hay que añadir el caracter `&` antes de la variable `num1`. Esto quiere decir que añadimos el dato a la posición que ocupa en memoria la variable `num1`.

> De momento quédate con que hay que hacer es, ya trataremos con más detalle la posición en memoria de las variables en el capítulo de punteros.

## Recoger varios datos con `scanf()`

La función `scanf()` también permite recoger varios datos en una sola sentencia. Los datos recogidos deberán estar separados por espacios y se introducen de la siguiente manera:

````c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int entero;
    float real;
    char letra;

    printf("Introduzca un entero, un real y una letra: ");
    scanf("%i %f %c", &entero, &real, &letra);
    printf("\nHa introducido: %i, %f, %c.\n", entero, real, letra);

    system("PAUSE");
    return 0;
}
````

Supongamos que el usuario ejecuta la aplicación e introduce `10 4.54 c`, veríamos:

````text
Introduzca un entero, un real y una letra: 10 4.54 c
Ha introducido: 10 4.540000 c
````

Fijate que tan sólo cambia la sentencia `scanf("%i %f %c", &entero, &real, &letra);` en la que indicamos que lo introducido por teclado tendrá que convertirse a un entero y asignarlo a la variable `entero`, lo mismo para el real y el caracter.
