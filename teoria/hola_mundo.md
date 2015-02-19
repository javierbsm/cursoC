# Hola Mundo

Empezamos el curso creando nuestra primera aplicación en C. Será una aplicación muy sencilla que tan solo mostrará **"Hola Mundo"** en pantalla.

Para ello crea un archivo llamado `hola_mundo.c`. Abrelo con el editor de texto y escribe el siguiente código:

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    printf("Hola Mundo");

    system("PAUSE");
    return 0;
}
```

**Enhorabuena**, ya has escrito tu primera aplicación en C. Guarda, compila y ejecuta la aplicación. Verás que te sale una ventana de consola que muestra:

```
Hola Mundo
```

Vamos por partes para ver lo que hemos hecho.

#### `#include <stdio.h>`

La directiva `include` se utiliza para añadir a la aplicación ficheros externos que usaremos en nuestro código. En este caso hemos añadido la librería `stdio.h` que contiene la función `printf()` que es las que usamos para mostrar el texto en pantalla.

#### `#include <stdlib.h>`

Mediante otro `include` añadimos la librería `stdlib.h` que contiene la función `system()` que la usaremos para ejecutar comandos del sistema.

#### `int main(){}`

De todo el fichero de código fuente, la función `main()` es la que contiene las sentencias que se van activar una vez se ejecute la aplicación.

Para declarar la función, primero le hemos indicado que, al ejecutarse la función, devuelva un dato que en este caso es un entero `int`, la elección más habitual.

#### `printf("Hola Mundo");`

La función `printf()` es la encargada de mostrar el texto en pantalla. En este caso muestra el texto entre comillas `Hola Mundo`.

> No olides añadir el `;` para indicar que acaba la sentencia.

#### `system("PAUSE");`

La función `system()` se utiliza para ejecutar comandos de sistema.

En este caso el comando `PAUSE` de **MS-DOS**, que pide que presiones una tecla para continuar. Usaremos este comando justo antes de que acabe la aplicación para evitar que se cierre automáticamente la ventana de consola al finalizar.

>**NOTA:** esta función sólo te será necesaria si estas ejecutando la aplicación directamente desde el entorno gráfico en Windows. En Linux, Mac o desde la consola de Windows no te hará falta.

#### `return 0;`

Como se ha indicado antes, el programa al finalizar devuelve un valor entero. En este caso hemos puesto que al finalizar correctamente el programa, devuelva el valor `0` usarndo la funcion `return`.
