# Variables

En una aplicación se pueden manipular o procesar datos. Estos datos se almacenan en **variables** para poderse trabajar con ellos.

Una **variable** es un espacio de almacenamiento, al que se le ha asignado un nombre (o identificador), y que almacena un **tipo de dato** con un **valor**.

## Identificadores de variables

Los **identificadores** de variables (lo nombres) siguen las siguientes normas:

- Sólo permiten minúsculas `a-z`, mayúsculas `A-Z`, dígitos `0-9` y guiones bajos `_`. No se permiten espacios en blanco ni otros símbolos.
- **NO** pueden empezar por un dígito.
- **NO** pueden identificarse como una palabra reservada (ej `int`, `double`, `if`, `else`, ...)
- Son sensibles a las mayúsculas, la variable `rosa` no es la misma que `Rosa`.

Por **convenio**, una variable es identificada por un sustantivo (ej: `cosa`) o varias palabras seguidas con la primera en minúscula y las consecutivas con la primera letra en mayúculas (ej: `numeroCosasRecogidas`).


## Declaración de variables

Vamos a declarar una variable llamada `unidades` que va a almacenar un número entero (`int`eger en inglés), y se le asigna el valor 10. Se haría de esta manera:

```c
int unidades;
unidades = 10;
```

Como se puede observar, se ha declarado la variable indicando primero el tipo `int` (integer, entero en inglés), el nombre `unidades` y cerramos la sentencia `;`. Con esta expresión hemos reservado un espacio en memoria para almacenar una variable de tipo entero.

En resumen, la declaración de variable es:

```
tipo_dato nombreVariable;
```

En la segunda sentencia del ejemplo hemos asignado el valor `10` a la variable *unidades* con la expresión `unidades = 10;`. De tal manera podemos deducir que la asignación de un valor a una variable es:

```
nombreVariable = valor;
```

Dado que estas sentencias se utilizan mucho, hay versiones abreviadas:

```c
// Declarar la variable y asignar valor en la misma sentencia
int var1 = 10;

// Declarar más de una variable en un sentencia
int var2, var3, var 4;

// Declarar y asignar valores en más de una variable
int var5 = 3, var6 = 23, var7 = 23;
```

## Mostrar el dato de una variable

Ya sabemos declarar una variable y asignarle el valor. Vamos a mostrarlo en pantalla, para ello utilizaremos la función `printf()`. Veamoslo a  través de un programita:

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int unidades;     // Declaramos variable
    unidades = 10;    // Asignamos valor a la variable

    printf("Tienes %i elementos.", unidades);
    system("PAUSE");
    return 0;
}
```

Al ejecutar esta aplicación veremos en pantalla:

```
Tienes 10 elementos.
```

Analicemos la función `printf()`.

```c
printf("Tienes %i elementos.", unidades);
```

Como se puede observar, usamos el **código de conversión** `%i` para referirnos al dato de la variables `unidades`, donde `i` hace referencia a que el dato va a ser un entero (integer). Fíjate que como argumento (tras la coma) escribimos `unidades`, que es el identificador de la variable que queremos mostrar en el sitio reservado `%i` en la frase que se va a mostrar con el `printf()`.

De la misma manera, podemos mostrar múltiples variables en una sola sentencia:

```c
int var1 = 10, var2 = 5, var3 = 19;

printf("Las variables son: %i, %i y %i.", var1, var2, var3);
```

El resultado sería:

```
Las variables son: 10, 5 y 19.
```

## Reasignación de variable

Como su nombre indica, una variable permite variar el valor del dato que tiene almacenado. Basta con añadir una sentencia asignando otro valor a la misma variable.

Lo vemos a través de un ejemplo.

```c
int x;
x = 10;
printf("La variable X es igual a %i.\n", x);
// La variable X es igual 10.

x = 25;
printf("Ahora la variable X es igual a %i.\n", x);
// Ahora la variable X es igual a 25.
```

## Tipos de datos

Los **datos** que se pueden almacenar en una variable tan sólo pueden ser:

- Caracteres `char`, reserva `1` byte en memoria.
- Números enteros `int`, reserva `4` bytes en memoria.
- Números reales `float` o `double`, reserva `4` y `8` bytes en memoria, respectivamente.

Aparte, tenemos **modificadores** de datos que alteran la cantidad que puede almacenar el tipo de dato, estos son:

- `short` asigna la mitad de bytes al dato.
- `long` asigna el doble de bytes al dato.
- `long long` asigna el cuadruple de bytes al dato.
- `unsigned` quita el signo del tipo de dato para que pueda almacenar valores mayores (hasta el doble) en el mismo espacio a costa de no poder guardar valores negativos.
- `signed` fuerza a añadir el signo al tipo de dato, normalmente se añade sólo si detecta que usamos un número negativo.

Estos modificadores se aplican como la siguiente manera:

```c
// modificador tipo_dato variable;
long int numero_entero_largo;

// modificador variable;
// si no se indica, el compilador usará un entero (int)
unsigned numero_entero_sin_signo;
```

La siguiente tabla muestra los tipos de datos más comunes, y que usaremos en este curso, junto con **código de conversión** que utiliza, el espacio que ocupa en memoria y el rango de números que puede almacenar.

| Tipo | Declaración | Conversión | Bytes | Mínimo | Máximo |
|------|-------------|------------|------:|-------:|-------:|
| Entero | `int`    | `%i` ó `%d` |  4 | -2.147.483.647 | 2.147.483.647 |
| Entero sin signo   | `unsigned` | `%u`        | 4 | 0       | 4.294.967.295 |
| Real de 7 dígitos  | `float`    | `%f` ó `%e` | 4 | 3.4e38  | 3.4e38 |
| Real de 14 dígitos | `double`   | `%f` ó `%e` | 8 | 1.7e308 | 1.7e308 |
| Caracter ASCII     | `char`     | `%c`        | 1 | -128    | 127 |

## Asignar caracter a una variable

Tiene una particularidad especial, en la asignación el caracter asignado tiene que estar entre comillas simples `''`.

Veamos un ejemplo:

```c
int   entero = 10;
float real = 32.436;
char  letra = 'd';

printf("Tenemos un entero %i, un real %f y un caracter %c.\n", entero, real, letra);
// Tenemos un entero 10, un real 32.436 y un caracter d.
```
