# Trabajo con ficheros

En el capítulo anterior usábamos la redirección para controlar hacia donde se dirige la entrada y la salida de datos, de esta manera podíamos crear ficheros. Pero este es un sistema poco flexible para manejar ficheros, ahora vamos a crear y modificar ficheros usando las funciones estándar del C.

El flujo de trabajo habitual para manejar ficheros es:

1. Acceder al fichero
2. Comprobar si el fichero está abierto
3. Leer y escribir en el fichero
4. Cerrar el fichero

>**IMPORTANTE**: recordar que los ficheros no son únicamente los archivos que guardamos en el disco duro, en C todos los dispositivos del ordenador se tratan como ficheros: la impresora, el teclado, la pantalla, ...

## Acceder al fichero

Para poder acceder a un fichero en la aplicación se empieza declarando un puntero de tipo `FILE` con la siguiente sintaxis:

````c
FILE *nombrePuntero;
````

Este puntero es una estructura que recogerá información sobre el archivo que vaya a abrir (nombre archivo, dirección en memoria, buffer, etc.). Ahora toca abrir el fichero usando la función `fopen()` con la siguiente sintaxis:

````c
nombrePuntero = fopen("nombreArchivo.ext", "modoAcceso");
````

Donde `nombreArchivo.ext` es el fichero a acceder o crear y `modoAcceso` es un parámetro que especifica el modo en el que se accede al fichero. Estos pueden ser:

- `r`: abre fichero existente para lectura.
- `w`: crea un fichero, o lo sobre-escribe si ya existiese, para escritura.
- `a`: abre un fichero, o lo crea si no existiese, para datos al final del mismo.

A estos parámetros se le pueden añadir modificadores:

- `b`: abre el fichero en modo binario.
- `t`: abre el fichero en modo texto.
- `+`: abre el fichero en modo escritura y lectura.

Ejemplos de apertura de ficheros:

````c
include <stdio.h>

int main() {
    // Acceso sólo lectura a "origen.txt"
    FILE *ficheroLectura;
    ficheroLectura = fopen("origen.txt", "r"); 

    // Acceso escritura a "destino1.txt"
    FILE *ficheroEscritura;
    ficheroEscritura = fopen("destino1.txt", "w"); 

     // Acceso añadir en modo binario
    FILE *ficheroAnadir;
    ficheroAnadir = fopen("destino2.txt", "ab");
}
````

## Comprobar si el fichero está abierto

Una vez se ha accedido el fichero, es importante comprobar si realmente se ha podido acceder a él. Por ejemplo, es posible que quisieramos abrir en lectura un archivo que no exista.

Es fácil de comprobar ya que el puntero `FILE *` tendrá un valor `0` mientras no haya abierto ningún archivo.

Ejemplo:

````c
#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *fichero;
    fichero = fopen("origen.txt", "r");
    
    if (fichero != 0) { // Si no existe fichero
        fprintf(stderr, "No existe el fichero.\n"); // Muestra mensaje de error
        exit(1);  // Sale de la aplicación
    } 
    
    // Continua aplicación
    return 0;
}
````

## Leer y escribir en el fichero

Ya hemos abierto un fichero y hemos comprobado que está abierto, ahora es el momento de trabajar con él.

Por ejemplo, vamos a leer una frase de `origen.txt` con la función `fgets()` y copiarla a `fprintf()` que ya las hemos utilizado anteriormente:

````c
FILE *origen, *destino;
origen  = fopen("origen.txt",  "r");
destino = fopen("destino.txt", "w");

char frase[100];
fgets(frase, 100, origen); // Copiamos la frase de origen.txt al array
fprintf(destino, "%s", frase); // Copiamos la frase del array a destino.txt
````

>**NOTA**: Este ha sido un ejemplo, para seguir el flujo de trabajo de un fichero, ya profundizaremos en el siguiente apartado en las funciones de lectura y escritura de ficheros.

## Final de fichero `\EOF`

En cualquier documento se colocan los caracteres en serie con letras, números, símbolos y caracteres especiales tipo `\n` que indica salto de línea, `\t` tabulación, etc. El caracter especial `\EOF` (**End Of File**) indica a la aplicación el final del fichero.

A su manera, podemos decir que un fichero es como un similar a un string en el que se finaliza cuando llega al caracter especial `\EOF` en vez de `\0`. ,Y al igual que con el string, cuando se lee un caracter el puntero pasa a la posición del siguiente caracter hasta llegar a `\EOF`.

Para comprobar fácilmente cuando el fichero llega al caracter `\EOF`, disponemos de la función `feof(fichero)`  que devuelve `1` cuando lo encuentra. Sabiendo esto podemos crear un bucle que recorra todo el contenido de un fichero de múltiples líneas.

Ejemplo, sección de aplicación que muestra en pantalla todo el contenido de un fichero:

````c
char frase[100];
FILE *origen, *destino;
origen = fopen("origen.txt", "r");

do {
    printf("%s", frase);
    fgets(frase, 100, origen);
} while (feof(origen) == 0);
````

## Cerrar el fichero

Una vez realizadas las operaciones deseadas sobre el fichero, hay que cerrarlo. Es importante no olvidarse de hacerlo ya que el fichero podría corromperse.

El cierre de ficheros se realiza con la función `fclose(fichero)`. Si no hay problema, devuelve un `0`. En caso contrario (si el disco duro esta lleno, por ejemplo) devuelve un `1`.

````c
FILE *fichero;
fichero = fopen("origen.txt", "r");

// Comprobación de apertura
// Lectura y escritura de fichero

if (fclose(fichero) != 0) {
    fprintf(stderr, "Problemas al cerrar el archivo.\n");
}
````

## Resumen

Para resumir este apartado, vamos a escribir una aplicación que muestre el archivo `quijote.txt`, que contiene el primer párrafo de la novela de Cervantes, siguiendo los pasos indicados:

Aplicación:

````c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // 1. Acceso al fichero
    FILE *fichero;
    fichero = fopen("quijote.txt", "r");
    
    // 2. Comprobación de que está abierto
    if (!fichero) {
        fprintf(stderr, "No existe el fichero.\n");
        exit(1);
    }
    
    // 3. Trabajamos con el fichero
    char linea[100];
    fgets(linea, 100, origen);
    while (!feof(origen)) {
        printf("%s", linea);
        fgets(linea, 100, origen);
    };
    
    // 4. Cerramos el fichero
    if (fclose(fichero) != 0) {
        fprintf(stderr, "Problemas al cerrar el archivo.\n");
    }

    return 0;
}
````
