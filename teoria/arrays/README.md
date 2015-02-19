# Arrays

Un **ARRAY** (también llamados matrices o vectores) es una lista de variables del mismo tipo que tienen el mismo nombre y se diferencian en el índice.

## Declaración y asignación en arrays

La declaración de arrays se realiza indicando el **tipo de dato** que va almacenar los elementos del array, asignarle un **identificador** e indicar el **número de elementos** que va a contener.

````c
tipo_dato identificador_array[numero_elementos];
````

Para asignar un valor a algún elemento del array, tendremos que invocarlo con su **identificador** e indicar el **número del elemento**.

````c
identificador_array[numero_elemento] = dato;
````

> **RECUERDA:** en informática se empieza contando desde `0`. De esta manera la variable que está en la primer posición del array `notas[i]` es `notas[0]` y la última es `notas[i - 1]`.

Ejemplo. Tenemos un curso con 5 alumnos y almacenamos las notas obtenidas en un array:

````c
int notas[5];   // Declarado array de enteros con 5 elementos

// Asignamos el valor a los elementos del array
notas[0] = 6;   // Nota del primer alumno
notas[1] = 8;   // Nota del segundo alumno
notas[2] = 9;
notas[3] = 5;
notas[4] = 3;   // Nota del quinto y último alumno
````

Una manera abreviada de hacer lo anterior sería:

````c
ìnt notas[] = {6, 8, 9, 5, 3};
````

En este caso, no es necesario que indiques la longitud del array ya que lo detecta automáticamente.

## Introducir datos en un array

Se realiza de la misma manera que hacemos con las variables. 

Una vez el usuario escribe por teclado el valor, este se introduce en una posición específica del array con la función `scanf()`.

Ejemplo:

````c
float temperaturas[24];

printf("Indique la temperatura de las 00:00 : ");
scanf("$f", &temperaturas[0]);
printf("La temperatura de las 00:00 es: %f", temperaturas[0]);
````

## Número de elementos del array

Al declarar un array, la aplicación reserva un espacio determinado en memoria que dependerá de la longitud del array. Por ejemplo, si declaramos un array de 10 datos `double` ocupará un espacio de:

````text
10 elementos * 8 bytes/elemento = 80 bytes
````

Salvo que trabajemos con asignación dinámica de memoria, lo haremos más adelante, este espacio tiene que será una cantidad fija que se reservará en el momento de la declaración del array.

Por esta razón, no podemos utilizar una variable para indicar el número de elementos del array:

````c
int numeroElementos;

elementos[numeroElementos];
````

Si lo intentamos, el compilador devolverá un error y no dejará compilar.

Pero sí podemos hacerlo con una constante declarada con `#define` o con el modificador `const`.

Ejemplo:

````c
const int ALUMNOS = 5;

notas[ALUMNOS];
````

## Longitud del array

Con frecuencia, es útil determinar el número de elementos que contiene un array sin estar utilizando las constantes, la manera más sencilla es utilizando la función `syzeof()`:

````c
char array[] = {'a', 'b', 'c'};
int count;

count = syzeof(array)/syzeof(array[0]);
printf("array de %i elementos.", count); // Salida: array de 3 elementos
````

Lo que se ha hecho es recoger el espacio que ocupa en memoria el array con la expresión `sizeof(array)` (que serán los 3 `char`) y dividirlo por el espacio que ocupa la variable en primera posición (otro `char`). El resultado será un entero con el número de elementos del array.

## Bucles y arrays

El uso de bucles con arrays es continuo ya que puedes procesar todos los elementos de un array con un número.

Ejemplo, muestra las notas de los alumnos que hay en el aula:

````c
int i;
float notas[] = {2, 2.5, 3.6, 4.5, 5, 5, 5, 6, 7, 7.8, 9, 9.3};

count = sizeof(notas)/syzeof(notas[0]);

printf("Las notas obtenidas son: ");
for (i = 0; i < count; ++i) {
    printf("%f ", notas[i]);
}
````

