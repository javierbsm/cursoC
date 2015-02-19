# Funciones de ficheros

En los apartados anteriores ya hemos tratado las funciones básicas para abrir y cerrar archivos y comprobar su final:

- `FILE *` para declarar un puntero de fichero (no es una función, recordatorio).
- `fopen()`: abre el fichero en el modo indicado.
- `fclose()`: cierra el fichero.
- `feof()`: devuelve `1` al encontrar el final del archivo (caracter `EOF`).

También hemos visto como escribir cadenas de texto con:

- `fgets()`: lee una cadena de texto de un fichero.
- `fprintf()`: escribe una cadena de texto con datos en fichero.

Es un buen comienzo, pero en la práctica vas a necesitar un mayor repertorio de funciones para leer y escribir datos en archivos de la manera que te interese. Ahora trataremos todas las funciones más comunes ,incluidas en `stdio.h`, para la lectura y escritura en ficheros.

## Leer y escribir caracteres con `getc()` y `putc()`

La función `getc()` lee un caracter de fichero y desplaza el puntero a la siguiente posición. Igualmente, `putc()` escribe un caracter en fichero y desplaza el puntero a la siguiente posición.

Veamos un ejemplo de uso para realizar copias de archivos de texto.

````c
FILE *origen  = fopen ("origen.txt",  "r");
FILE *destino = fopen ("destino.txt", "w");
char letra    = getc(origen); // Declara variable y lee caracter de origen

while (!feof(origen)) {
    putc(destino); // Escribe caracter en destino
    getc(origen);  // Lee siguiente caracter en origen
}
````

## Leer y escribir cadenas de texto con `fgets()` y `fputs()`

La funciones `fgets()` y `fputs()` funcionan de manera similar a las utilizadas para caracteres pero trabajando con cadenas de texto.

Vamos a reproducir el mismo ejemplo anterior, pero copiando el archivo a través de cadenas de texto.

````c
FILE *origen  = fopen ("origen.txt",  "r");
FILE *destino = fopen ("destino.txt", "w");
int const longTexto = 100;
char texto[longTexto]; // Declara string que almacena lo leido

fgets(texto, longTexto, origen); // Lee primer string de origen
while (!feof(origen)) {
    fputs(texto, destino); // Escribe string en destino
    fgets(texto, longTexto, origen);  // Lee siguiente string de origen
}
````

>A primera vista pueden parecer similares, pero ten en cuenta que `getc` recoge caracter y con ello la aplicación puede establecer distintos flujos de trabajo en función del caracter recogido. Mientras que `fgets()` opera con strings y, por ejemplo, puedes hacer comparaciones con `strcmp()`.

## Leer y escribir datos con `fscanf()` y `fprintf()`

La funciones `fscanf()` y `fprintf()` permiten la lectura y escritura de datos, de manera análoga a sus omónimos `scanf()` y `printf()`, para ficheros. Los usaremos cuando los ficheros vayan a trabajar con distintos tipos de datos.

Ejemplo, el archivo `origen.txt` almacena el nombre, apellido, edad y altura de una persona y queremos crear un párrafo redactado a partir de esos datos en el archivo `destino.txt`:

````c
/* 
origen.txt contiene:
Marcos Rodríguez 28 1.75
*/
FILE *origen  = fopen ("origen.txt",  "r");
FILE *destino = fopen ("destino.txt", "w");
char nombre[20];
char apellido[40];
int edad;
float altura;

fscanf(origen, "%s %s %i %f", nombre, apellido, &edad, &altura);
fprintf(
    destino,
    "El cliente %s %s tiene %i años y mide %.2f metros.\n",
    nombre, apellido, edad, altura
); // Salida: El cliente Marcos Rodríguez tiene 28 años y mide 1.75 metros.
````

## Leer y escribir elementos con `fread()` y `fwrite()`

Estas funciones las utilizaremos cuando vayamos a leer, con `fread()`, o escribir, con `fwrite()`, en un fichero un número indeterminado de datos del mismo, por ejemplo números enteros.

La sintaxi de estas funciones es:

```c
fread(*punt, eltsize, n, fi);
fwrite(*punt, eltsize, n, fi);
```

Donde:

- `*punt` es el puntero a la variable o array que va almacenar los datos.
- `eltsize` es el tamaño, en bytes, de los datos a almacenar. Típicamente se obtiene de `sizeof()`.
- `n` es el número de elementos que va a copiar.
- `fi` es el fichero, o mejor dicho el puntero declarado al fichero.

Ejemplo:

```c
// PROXIMAMENTE
```

## Buscar con `fseek()` y `ftell()`

```c
// PROXIMAMENTE
```

## Resumen

| Función                           | Descripción   |
|:----------------------------------|:--------------|
| `FILE *punt`                      | Declara puntero de fichero              |
| `fopen("fi", "modo");`            | Abre fichero en modo indicado           |
| `fclose(fi);`                     | Cierra fichero                          |
| `ferror(fi);`                     | Devuelve `1` si hay error               |
| `feof(fi);`                       | Devuelve `1` en caracter `EOF`          |
| `getc(fi);`                       | Lee caracter de fichero                 |
| `putc(char, fi);`                 | Escribe caracter en fichero             |
| `fgets(string, max, fi);`         | Lee string `max` caracteres de fichero  |
| `fputs(string, fi);`              | Escribe string en fichero               |
| `fscanf(fi, "form", arg1, ...);`  | Lee de fichero                          |
| `fprintf(fi, "form", arg1, ...);` | Escribe en fichero                      |
| `fread(*punt, eltsize, n, fi);`   | Lee y guarda `n` elementos en `*punt`   |
| `fwrite(*punt, eltsize, n, fi);`  | Escribe `n` elementos de `*punt` a `fi` |
| `fseek()` |  |
| `ftell()` |  |

