# Hola Mundo

Empezamos el curso creando nuestra primera aplicación en **C**. pero antes de nada tendremos que instalar un editor de texto y un compilador para poder escribir nuestra aplicación.

## Editores de texto y compilador

Si estás empezando desde cero, te indico una serie de recomedaciones en función del sistema operativo en el que trabajes. Son editores de texto avanzados que están genial para aplicaciones sencillas y que además te instalan el compilador para **C**.

| Sistema operativo | Aplicación |
|:-----------------:|:----------:|
| Windows | [WxDev-C++](http://wxdsgn.sourceforge.net/) |
| MacOS   | [Xcode](https://developer.apple.com/xcode/) |
| Linux   | [Geany](http://www.geany.org/) |
| Android | [CppDroid](https://play.google.com/store/apps/details?id=name.antonsmirnov.android.cppdroid&hl=es) |
| iOS     | [CppCode](https://itunes.apple.com/app/cppcode-offline-c-c++-ide/id936694712) |

>Si ya estás acostumbrado a programar, te basta con instalar un compilador de **C**, [MinGW](http://www.mingw.org/) para Windows o los paquetes `gcc` y `g++` en Linux y MacOs, así puedes utilizar tu editor de texto o IDE favorito.

## Nuestra primera aplicación en C

Ya tenemos instalado será una aplicación muy sencilla que tan solo mostrará **"Hola Mundo"** en pantalla. 

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
