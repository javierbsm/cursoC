# Funciones de caracteres y strings

Ahora trataremos una serie de funciones que nos ayudan mucho para trabajar con caracteres y strings.

Existen de muchos tipos, pero para este curso nos centraremos sólo en las más básicas.

>**REPASO**:
>
>Un **caracter** es un símbolo almacenado en una varialble que almacena un dato de tipo `char`.
>
>Un **string** es un array que almacena una cadena de caracteres.

## Funciones de tipo y conversión de caracteres

Estas funciones están incluidas en la librería `ctype.h`, hay de varios tipos:

### Comprobación de tipo de caracter

| Función      | Caracter      | Descripción                           |
|:--------------|:--------------|:---------------------------------------|
| `isalpha(c)`  | `[a-zA-Z]`    | letra                                  |
| `isdigit(c)`  | `[0-9]`       | número                                |
| `isalnum(c)`  | `[a-zA-Z0-9]` | número o letra                        |
| `iscdigit(c)` | `[0-9a-fA-F]` | caracter hexadecimal                   |
| `isspace(c)`  | `[ \t\n]`     | espacio, tabulación o salto de línea |
| `iscntrl(c)`  |               | caracter control                       |
| `ispunct(c)`  |               | caracter de puntuación                |
| `isprint(c)`  |               | caracter imprimible                    |
| `isgraph(c)`  |               | caracter gráfico                      |
| `isupper(c)`  | `[A-Z]`       | letra mayúscula                       |
| `islower(c)`  | `[a-z]`       | letra minúscula                       |

### Modificación de caracter

| Función     | Descripción                       |
|:-------------|:-----------------------------------|
| `toupper(c)` | devuelve el caracter en mayúscula |
| `tolower(c)` | devuelve el caracter en minúscula |

Ejemplo, una aplicación que comprueba si el caracter aportado es una letra o un número y, si es letra, comprueba si está en mayúscula o no.

````c
#include <stdio.h>
#include <ctype.h>

void comprobar(char caracter) {
    if (isalpha(caracter)) {
        printf("\"%c\" es una letra", caracter);
        if (isupper(caracter)) {
            printf(" y es mayúscula");
        } else {
            printf(" y es minúscula");
        }
        printf(".\n");
    } else {
        printf("\"%c\" no es una letra.\n", caracter);
    }
}

int main() {
    char letra = 'a';
    char numero = '8';

    comprobar(letra);  // "a" es letra y es minúscula.
    comprobar(numero); // "8" no es una letra
    letra = toupper(letra);
    comprobar(letra);  // "A" es letra y es mayúscula.
}
````

## Funciones de manipulación de strings

Trataremos varias funciones nuevas para trabajar con cadenas de texto:

| Función            | Descripción                                       |
|:--------------------|:---------------------------------------------------|
| `strlen()`          | Devuelve el número de caracteres sin contar `\0`. |
| `strcpy(dest, src)` | Sobreescribe el contenido de `src` en `dest`.      |
| `strcat(dest, src)` | Añade el contenido de la cadena `src` en `dest`.  |
| `sprintf()`         | Copia un string a un array igual que `printf()`    |
| `strcmp(s1, s2)`    | Comprueba si `s1` y `s2` son distintos.            |

````c
// EJEMPLO DE FUNCIONES PARA MANIPULAR STRINGS
````
