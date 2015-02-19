# Arrays multidimensionales

La manera más sencilla para definir un array multidimensional es un array que almaneca arrays. 

## Declaración de array multidimensional

Vamos a verlo con un ejemplo. Declaramos un array de enteros que almacena 5 arrays y cada uno de ellos almacena 10 variables.

````c
int multiArray[3][5];
````

>**NOTA:** se pueden declarar arrays multidimensionales de cualquier número de dimensiones. Por ejemplo, uno de 4: `int array[3][4][5][6];`

## Asignación de valores

Para asignar valores a las distintas posiciones es igual que con los arrays simples, tan sólo tener en cuenta que hay que indicar en cual ponerlo.

````c
multiArray[0][0] = 10;     // Primer valor del primer array en array_lti
````

De la misma manera, para declarar y asignar muchos valores de manera abreviada:

````c
int multiArray[3][5] = {
    {10, 48, 15, 32, 32},
    {38, 54, 87, 45, 32},
    {32, 43, 65, 76, 87}
}
````

## Uso de bucles con arrays multidimensionales

Un ejemplo de un bucle `for` recorriendo este array multidimensional.

`````c
int i, j;

for (i = 0; i < 3; ++i) {
    for (j = 0; j < 5; ++j) {
        printf("%i ", multiArray[i][j]);
    }
    printf("\n");
}
````

Salida:

````text
 10  48  15  32  32
 38  54  87  45  32
 32  43  65  76  87
````

Fijate que se ha utilizado un bucle dentro de otro, uno que recorre la variable `i` y otro la `j`. Lo que hacemos es inicializar `i = 0` y para `multiArray[0][j]` recorremos y mostramos todos los valores del primer array con el bucle `for` con `j`.