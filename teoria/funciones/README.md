# Funciones

Una **función** es un bloque de código al que se le ha asignado un título y que realiza algo. Cada vez que llamas a la función en el código, se ejecuta el contenido del bloque.

## Declaración de función

La sintaxis para declarar una función es la siguiente:

````c
tipoDato nombreFuncion(arg1, arg2, ...) {
    declaración de las variables locales;
    
    cuerpo de la funcion;

    return dato;
}
````

Analicemos la sintaxis por partes:

- **Nombre de Funcion**: es el identificador que se utiliza para invocar la función cada vez que vaya a utilizarse. Para el nombre sólo pueden usarse letras, números y el símbolo `_` de la misma manera que con las variables.

- **Tipo de dato**: es el tipo de dato que se espera que devuelva la función. Estos serán los mismos que se utilizan para las variables (`int`, `char`, `float` y `double`).

- **Argumentos**: son variables, arrays o punteros que van a recibir los datos proporcionados a la función. Es necesario declarar las variables previamente como globales o en la misma sentencia para usarlas como variables locales.

- **Declaración de variables locales**.

- **Cuerpo de la función**: el código que va a ejecutar la función cada vez que se invoque.

- **return dato**: la sentecia `return` será la que indique el dato a devolver, tendrá que ser del tipo de dato indicado en la declaración de la función, pudiendo ser una constante o una variable.

Veamos un ejemplo de aplicación con una función muy simple que suma dos números reales:

````c
#include <stdio.h>
#include <stdlib.h>

// La función suma recoge dos viables de números reales
// y devuelve la suma de ambos.
float suma(float num1, float num2) {
    float sum;

    sum = num1 + num2;
    return sum;
}

int main() {
    float dato1, dato2, sumados;

    // Pedimos al usuario que introduzca los números a sumar
    printf("Introduzca dos números: ");
    scanf("%f %f", &dato1, &dato2);

    // Invocamos la función suma() pasando los datos introducidos
    // por el usuario y los mostramos en pantalla
    sumados = suma(dato1, dato2);
    printf("Suma de números: %f.\n", sumados);

    system("PAUSE");
    return 0;
}
````

>**NOTA**: tambíén podría invocarse la función en la misma expresión de `printf()` de la siguiente manera `
    printf("Suma de números: %f.\n", suma(dato1, dato2));`.

## Cuando declarar una función

Un función **TIENE** que ser declarada antes de poder invocarla, de todas maneras, no es necesario definir el bloque en el momento de la declaración. Veamos el ejemplo anterior definiendo la función posteriormente:

````c
#include <stdio.h>

float suma(float num1, float num2);     // Declaración de función

int main() {
    float dato1, dato2, sumados;
    printf("Introduzca dos números: ");
    scanf("%f %f", &dato1, &dato2);
    sumados = suma(dato1, dato2);
    printf("Suma de números: %f.\n", sumados);
    return 0;
}

float suma(float num1, float num2) {    // Definición de función
    float sum;
    sum = num1 + num2;
    return sum;
}
````

## Tipo de dato `void`

En funciones se puede utilizar el tipo de dato `void` para que que este no devuelva ningún tipo de dato. Esto puede ser interesante para funciones que no van a devolver datos sino que muestran texto en pantalla o trabajan por punteros.

Ejemplo: creamos la función `menu()` para mostrar el menú de la aplicación.

````c
#include <stdio.h>

int selector;

void menu();

int main() {
    menu();

    switch(selector) {
        // Bloque de código
    }

    system("PAUSE");
    return 0;
}

void menu() {
    do {
        printf(
            "¿Qué desea hacer?\n"
            "1. Introducir valor.\n"
            "2. Mostrar valores.\n"
            "3. Comparar valores.\n"
            "Elija opción: "
        );
        scanf("%i", selector);
    } while (selector != 1 || selector != 2 || selector != 3);
}
````

## Pasar arrays a funciones

También puedes pasar arrays a funciones. De todas maneras, es necesario que pases la longitud del array a la función no se puede calcular su longitud desde el interior de la función.

>En el apartado de punteros, explicaremos por qué no se puede calcular el tamaño del array con `sizeof()`.

Veamos un ejemplo:

````c
#include <stdio.h>

// Declaramos la función esperando recibir el array y su longitud
int sumatorio(int array[], int count);

int main() {
    // Declaramos array y guardamos en una variable su longitud
    int unidades[] = {4, 5, 6, 7, 3, 4, 2};
    int count = sizeof(unidades)/sizeof(unidades[0]);

    printf("Las unidades son: ");
    for (int i = 0; i < count; ++i) {
        printf("%i ", unidades[i]);
    }
    printf("\n");
    // Invocamos la función pasando el array y su longitud
    printf("El sumatorio de unidades es %i.\n", sumatorio(unidades, count))

    return 0;
}

// Recibidos el array y la longitud, se trabaja con el array normalmente
int sumatorio(int array[], int count) {
    int sum = 0;
    for (int i = 0; i < count; ++i) {
        sum += array[i];
    }
    return sum;
}
````

