# Punteros

Ahora empezamos a tratar los punteros, para muchos estudiantes es una de las partes más difíciles de C al principio.

Creo que la manera más sencilla de entender punteros es mediante un simil con la realidad. Pensemos en un mapa, si queremos saber la situación de un elemento en el mapa lo indicaremos mediante coordenadas expresadas en latitud y longitud.

Ahora pasemos esta idea al ordenador, al declarar una variable se reserva un espacio en memoria en el que podremos insertar un dato. Si la memoria del ordenador fuese un espacio física, podríamos decir que el puntero es la coordenada que indica la posición de la variable y que se expresa en formato hexadecimal.

## Obtención y declaración de puntero

Para obtener el puntero de una variable ya declarada, basta con referirte a la variable con `&` y el símbolo de conversión `%p` para mostrarlo.

Ejemplo:

````c
#include <stdio.h>

int main () {
    int x = 10;
    printf("X = %i, puntero %p\n", x, &x);
    return 0;
}
````

La salida sería, por ejemplo `X = 10, puntero 0x7fff587803ac`, donde el puntero será un valor hexadecimal distinto cada vez que ejecutes la aplicación ya que cambia la posición de la variable.

Ahora vamos a declarar un puntero que viene a ser como una variable que guarda la coordenada hexadecimal de una variable ya declarada. La sintaxis para declarar un punteros es:

````c
tipoDato var = arg;
tipoDato *punt = &var;
````

A través de los punteros se puede acceder a los datos almacenados en ese espacio en memoria, que es el que se ha reservado para las variables, y también modificarlos.

Ejemplo:

````c
int a = 5;
int *punt1 = &a;

printf("Dato almacenado en puntero: %i\n", *punt1); // 5

*punt += 3;

printf("Variable A modificada: %i\n", a); // 8
````

## Uso de punteros

Ya sabemos que son los punteros, pero... ¿para qué se utilizan si todo esto se puede hacer normalmente con variables?

Los usos son muchos ya que los punteros permiten romper limitaciones del lenguaje más básico para funciones y arrays, así como la capacidad de acceder directamente a la pantalla, al teclado, a ficheros, etc.

>Uno de los usos ya lo habíamos tratado en la introducción de datos ya que a la función `scanf()` tenemos que pasarle el código de conversión de dato y la dirección de la variable en memoria. Ejemplo:
>
>````c
>ìnt num;
>
>printf("Introduzca un número: ");
>scanf("%i", &num);
>````

## Punteros en funciones

Por defecto, las funciones reciben una serie de datos como argumentos, estos se traspasan a variables locales en la función para que esta trabaje con ellos y devuelve **UN ÚNICO** valor.

Por lo tanto, las funciones no son capaces de modificar variables externas salvo que estas sean globales. Esta característica puede ser cambiada si se pasan a la función los punteros de las variables a modificar.

Ejemplo:

````c
#include <stdio.h>

int suma(int *a, int b) {
    int c;
    c = *a + b;  // 5 + 10 = 15
    *a = 0;      // num1 = 0
    return c;
}

int main() {
    int num1 = 5, num2 = 10;
    int resultado = suma(&num1, num2);
    printf("Resultado: %i, Num1 = %i\n", resultado, num1);
    return 0;
}
````

En este ejemplo hemos visto como la función `suma()` devuelve la suma de los datos aportados, donde uno de ellos `num1` es pasado como puntero. Dicho puntero se almacena en `*a` y tras la suma se iguala a 0 con lo que `num1` pasa a valer 0.

## Arrays en funciones

A una función no se le puede pasar un array como parámetro, sino que se le pasa un puntero que indica el punto de comienzo del array.

Ejemplo, una función que devuelve el sumatorio del array que es proporcionado como parámetro:

````c
#include <stdio.h>
#include <stdlib.h>

int sumatorio(int array[], int count) {
    int suma = 0;
    for (int i = 0; i < count; i++) {
        suma += array[i];
    }
    return suma;
}

int main() {
    int numeros[] = {4, 5, 7, 8, 3, 6, 6};
    int count = sizeof(numeros)/sizeof(numeros[0]);
    printf("%i\n", sumatorio(numeros, count));
    return 0;
}
````

Aunque la expresión `int sumatorio(int array[], int count)` haga parecer que estamos declarando `array[]` para almacenar los datos de `numeros[]`, en realidad `numeros` es un puntero que señala señala al resto del array y que puede ser recibido por la función de esta manera:

````c
int sumatorio(int *array, int count) {
    int suma = 0;
    for (int i = 0; i < count; i++) {
        suma += array[i];
    }
    return suma;
}
````

>De hecho, antiguamente sólo se podía pasar un array a una función expresándolo explícitamente como puntero.

Un inconveniente es que no puedes utilizar la función `sizeof()` para determinar la longitud del array ya que devolverá sólo el tamaño del puntero, que será siempre 8 bytes. Debido a esto, es necesario que pases la longitud como otro argumento.

Ejemplo:

````c
int sumatorio(int array[]) {
    count = syzeof(array);
    printf("%i bytes", count); // 8 bytes
}
````

La aplicación es capaz de trabajar con los arrays sólo a través de su puntero gracias a que los datos se almacenan de manera secuencial, uno tras otro en memoria. Este ejercicio muestra la posición en memoria de un array de caracteres.

````c
#include <stdio.h>
#include <stdlib.h>

void muestra(char array[], int count) {
    for (int i = 0; i < count; i++) {
        printf("Posición puntero nº %i: %p\n", i, &array[i]);
    }
}

int main() {
    char numeros[] = { 4, 5, 7, 8, 3, 6, 6};
    int count = sizeof(numeros)/sizeof(numeros[0]);
    muestra(numeros, count);
    return 0;
}
````

Donde la salida es:

````text
Posición puntero nº 0: 0x7fff9a325810
Posición puntero nº 1: 0x7fff9a325811
Posición puntero nº 2: 0x7fff9a325812
Posición puntero nº 3: 0x7fff9a325813
Posición puntero nº 4: 0x7fff9a325814
Posición puntero nº 5: 0x7fff9a325815
Posición puntero nº 6: 0x7fff9a325816
````

>Cada caracter esta a 1 byte despues del anterior ya que ocupa eso, si hubiese sido un array de enteros cada puntero hubiera estado 4 bytes adelante ya que el entero ocupa 4 bytes.
