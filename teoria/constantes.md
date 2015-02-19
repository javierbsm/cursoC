# Constantes

Las constantes son aquellos datos que no se pueden cambiar a lo largo de la aplicación.

Estas se pueden declarar a través de las directivas del preprocesador con `#define` o mediante el modificador de datos `const`.

## Directiva `define`

La directiva `#deine` permite declarar constantes con un identificador y el valor que se le asigna. Ejemplo:

```c
#include <stdio.h>
#include <stdlib.h>

//directiva  nombre_constante  valor
#define      PI                3.1416
#define      E                 2.7183

int main()
{
    printf("El valor de PI es %f.\n", PI);
    printf("El valor de E es %f.\n", E);

    system("PAUSE");
    return 0;
}
```

> Por convenio, las constantes se identifican con mayúsculas.

## Modificador `const`

El modificador de tipos de datos `const` permite forzar a que una variable se convierta en una variable de solo lectura (una constante) desde el momento en el que se aplica en una designación. Ejemplo:

````c
#include <stdio.h>
#include <stdlib.h>

int main() 
{
    float const PI = 3.1416;
    printf("El número PI es $f", PI);
    // El número PI es 3.1416

    system("PAUSE");
    return 0;
}
````

Si reasignásemos el valor de una constante tras haberla declarado, tendríamos un error de compilación. Ejemplo:

````c
float const PI = 3.1416;
PI = 32;
````

Al intentar compilar la aplicación no podríamos y obtendremos este error:

````text
error: assignment of read-only variable 'PI'
PI = 32;
````
