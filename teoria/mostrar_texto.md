# Mostrar texto

Ya hemos introducido en la aplicación "Hola Mundo" como mostrar texto en pantalla con la función `printf()`, avancemos un poco más sobre ella.

## Función `printf()`

Como ya hemos visto podemos mostrar texto con la función `printf()` que se encuentra en la librería `stdio.h` que añadiremos con la directiva `include`.

```c
#include <stdio.h>

int main()
{
    printf("Hola Mundo");
    return 0;
}
```

Al ejecutar la aplicación, veremos en pantalla:

```
Hola Mundo
```

De esta manera, podemos llamar todas las veces que queramos la función `printf()` para mostrar más texto. Por ejemplo:

```c
printf("Hola Mundo");
printf("¿Cómo estas?");
printf("Bien, gracias");
```

Tendremos:

```
Hola Mundo¿Cómo estas?Bien, gracias
```

Este ejemplo ha mostrado como funciona `printf()`, cuando se imprime en pantalla una cadena de texto, el cursor se coloca después del último caracter. Si queremos que cada frase se coloque en la siguiente línea, tendremos que indicarle a `printf()` que imprima el caracter especial de salto de línea `\n`. Ejemplo:

```c
printf("Hola Mundo\n");
printf("¿Cómo estas?\n");
printf("Bien, gracias");
```

Ahora el resultado será:

```
Hola Mundo
¿Cómo estas?
Bien, gracias
```

Una sola función de `printf()` también permite usar varias cadenas de texto contenidas entre comillas `"`. Si reicieramos el ejemplo anterior con una sola función, tendríamos:

```c
printf(
    "Hola Mundo\n"
    "¿Cómo estas?\n"
    "Bien, gracias"
);
```

## Caracteres especiales

Al igual que el salto de línea `\n` existe una serie de caracteres especiales especiales que no pueden ser usados en `printf()` de la misma manera que si estuviesemos trabajando con un editor de texto. Estos son:

| C. especial | Salida         | Definición |
|:-----------:|----------------|------------|
| `\n`        | Salto de línea | Salto de línea |
| `\t`        | 4 espacios     | Tabulador |
| `\b`        | Elimina último caracter | Retroceso |
| `\\`        | `\`            | Corchete derecho |
| `\'`        | `'`            | Comilla simple |
| `\"`        | `"`            | Comillas dobles |

Por ejemplo, si quisieramos ver en pantalla:

```
Esto es muy "extraño".
```

Tendríamos que escribir con `printf()`:

```c
printf("Esto es muy \"extraño\".");
```

> **NOTA:** Existen más caracteres especiales pero los trataremos más adelante ya que no presentan utilidad para `printf()`.


## Ejercicios

