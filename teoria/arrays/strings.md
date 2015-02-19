# Strings

Un string es una cadena de caracteres que forman una palabra o frase.

Con lo que ya sabemos de array y bucles, ya podríamos crear una cadena de caracteres en un array y mostrarla con un bucle:

````c
char saludo[] = {'B', 'i', 'e', 'n', 'v', 'e', 'n', 'i', 'd', 'o'};
count = syzeof(saludo)/syzeof(saludo[0]);

for (i = 0; i < count; ++i) {
    printf("%c", saludo[i]);
}
````

Salida:

````text
Bienvenido
````

Como esta acción se realiza continuamente, disponemos de los **strings** que son arrays con un caracter especial `\0` que indican su final.

## Declarar y mostrar strings

Se declaran igual que los arrays normales pero sin necesidad de separar los caracteres:

````c
char saludo[] = "Bienvenido";
// Equivale a:
char saludo[] = {'B', 'i', 'e', 'n', 'v', 'e', 'n', 'i', 'd', 'o', '\0'};
````

Para mostrarlos en pantalla se utiliza el símbolo de conversión `%s` de la misma manera que trabajamos con variables.

````c
char saludo[] = "Bienvenido";

printf("%s usuario", saludo);
````

Salida:

````text
Bienvenido usuario
````

## Introducir palabra en string

Se realiza de la misma manera que hacemos con las variables.

````c
char word[20]; // Almacena una palabra de hasta 20 caracteres

printf("Escriba una palabra: ");
scanf("%s", word);
printf("Palabra escrita: %s", word)
````

>**ATENCIÓN:** fíjate que en la función `scanf()` no se utiliza el símbolo `&` para introducir el dato. Cuando trabajemos punteros entenderás por qué.

Y también se pueden añadir varias palabras a distintos strings:

````c
char word1[20];
char word2[20];
char word3[20];

printf("Escriba tres palabras: ");
scanf("%s %s %s", word1, word2, word3);
printf("Palabras escritas: %s, %s, %s", word1, word2, word3);
````

## Introducir frase en string

La cosa varía un poco si queremos añadir frases ya que `scanf()` usa los espacios para separar los datos que se van a insertar en cada variable, string o array.

Podemos solucionarlo utilizando la función `fgets()` que permite recoger los caracteres escritos en un fichero e insertarlos en un string. Si ese fichero es `stdin`, que es el "fichero" en memoria que recoge lo introducido en teclado, podemos recoger lo que escribe el usuario y añadirlo al string.

La sintaxis del la función `fgets()`:

````c
fgets(nombreString, numeroCaracteres, fichero);
````

Ejemplo de uso para que el usuario introduzca una frase en un string:

````c
int longitudFrase = 100;
char frase[longitudFrase];

fgets(frase, longitudFrase, stdin);
````

>Trataremos con más detalle `fgets()` y `stdin` en el capítulo de ficheros. De momento, se introduce porque es muy útil para esta situación.

Si consultas manuales antiguos de C verás que se utilizaba la función `gets(nombreString)`, esta función se está retirando desde la **C11** y si intentas compilar aplicaciones que las utilizan te mostrará un `warning`.

La razón se debe a que un string tiene un tamaño específico, por ejemplo `char frase[100];` puede almacenar hasta 100 caracteres. Con `gets()` un usuario podría introducir miles de caracteres donde sólo se almacenarían los 100 primeros en `frase[]` pero los demás se almacenan aleatoriamente en la memoria pudiendo producir errores graves.

Esta situación la resolvemos con `fgets()` ya que en ella indicamos el número de caracteres que vamos a recoger de la última frase escrita por el usuario `fgets(frase, longitudFrase, stdin);`.