# Redirección

En cualquier dispositivo informático, cuando se escribe por teclado, los datos escritos pasan por una entrada estandarizada (**stdin**, standard input), donde las aplicaciones recogen estos datos para trabajar con ellos. 

De la misma manera, los datos incluidos en una aplicación que se quieren mostrar en pantalla tienen que pasar a una sección en memoria de salida estandarizada de datos (**stdout**, standard output) que, normalmente, apuntará a la pantalla.

También existe otra salida de datos estandarizada para mostrar los mensajes de error (**stderr**, standard error) que normalmente suele apuntar a la pantalla.

A este flujo que se produce con los datos se le llama **redireccionamiento**. 

| Redirección       | Flujo |
|-------------------|-------|
| Entrada de datos  | `teclado --> stdin --> aplicación` |
| Salida de datos   | `aplicación --> stdout --> pantalla` |
| Salida de errores | `aplicación --> stderr --> pantalla` |

## Redirección de entrada

Las entradas y salidas estandarizadas `stdin`, `stdout` y `stderr` pueden trabajarse como si fuesen "archivos" en memoria.

La redirección de entrada ya la hemos tratado en el apartado de strings con la función `fgets()` para recoger el texto desde `stdin` y guardalo en el string. O lo que es lo mismo, la redirección de entrada a un string:

````c
#include <stdio.h>

int main() {
    char frase[100];
    printf("Escribe una frase: ");
    fgets(frase, 100, stdin);  // Recoge frase escrita por el usuario
    printf("Has escrito:\n%s", frase);  // La muestra en pantalla
    return 0;
}
````

La función `fgets()` se utiliza para copiar cadenas de texto desde un archivo a un string siguiente esta sintaxis:

````c
fgets(stringDestino, nCaracteresRecoger, archivoOrigen);
````

## Redirección de salida

Podemos realizarla con la función `freopen` que permite redireccionar un archivo a otro de la siguiente manera:

````c
freopen("ficheroDestino", "modoEscritura", "ficheroOrigen");
````

Los modos de escritura son:

- `w`: crea archivo o sobre-escribe si existiese.
- `a`: crea archivo o añade al mismo si existiese.

Si, por ejemplo, quisieramos redirigir la salida a fichero en vez de a pantalla, podríamos hacer:

````c
#include <stdio.h>

int main() {
    freeopen("fichero.txt", "w", stdout);
    printf("Hola Mundo");
    return 0;
}
````

Si compilas y ejecutas esta aplicación verás que no se muestra nada en pantalla pero que aparecerá en el mismo directorio `fichero.txt` con el texto:

````text
Hola Mundo
````

## Redirección para mensajes de error

Para facilitar la depuración de aplicaciones, disponemos de una salida estandarizada para mensajes de error **stderr**. 

La salida utilizada por defecto es **stdout** por lo que hay que indicar que el mensaje se redireccione a `stderr`. Lo podemos hacer fácilmente con la función `fprintf()` que redirecciona lo escrito como si fuera con `printf()` a un fichero con la siguiente sintaxis:

````c
fprintf(fichero, "cadenaTexto", arg1, arg2, ...);
````

Veamos un ejemplo de una aplicación que recoge todo el texto de escribamos y lo copia a un fichero hasta que escribamos la frase `salir` y presionemos `RETURN`:

````c
#include <stdio.h>
#include <string.h>

int main() {
    char texto[100];
    printf("Escribe algo:\n");
    fgets(texto, 100, stdin);  // Redireccion lo escrito al string
    freopen("resultado.txt", "wb", stdout);  // Redirecciona stdout a fichero
    do {
        printf("%s", texto);  // Este texto saldrá al fichero y no a pantalla
        fgets(texto, 100, stdin);
        // Sigue escribiendo hasta que el usuario no escribe "salir"
    } while (strcmp(texto, "salir\n") != 0);
    // Cuando el usuario acabe, mostramos texto de despedida
    fprintf(stderr, "Ha tecleado SALIR.\n");
    return 0;
}
````

Fíjate que el texto de despedida está redireccionado a `stderr` por lo que se verá en pantalla. En caso de no haberlo hecho así, este hubiera salido a través de `stdout` y hubiera acabado en `resultado.txt` sin verlo en pantalla.