# 📚 Libft - 42 School

> *Mi primera biblioteca propia, que contiene los bloques de construcción para futuros proyectos en C en 42 School.*

## 💡 Sobre el Proyecto

**Libft** (Biblioteca de funciones) es el primer proyecto del tronco común ("common core") de 42 School. El objetivo es recrear funciones estándar de la biblioteca de C (de `<string.h>`, `<ctype.h>`, `<stdlib.h>`) junto con funciones de utilidad adicionales que se utilizarán a lo largo del resto del plan de estudios. 

Al reescribir estas funciones desde cero, este proyecto proporciona una comprensión profunda de la asignación de memoria, la aritmética de punteros, las estructuras de datos y el funcionamiento interno de las funciones estándar de C que normalmente se dan por sentadas.

---

## 🧠 Análisis Profundo: Conceptos Fundamentales Explorados

### 1. Gestión de Memoria y Punteros
En C, la memoria no se gestiona automáticamente. Libft obliga a tener un enfoque riguroso respecto a la asignación de memoria y la seguridad:
*   **Asignación Dinámica (`malloc`, `free`):** Funciones como `ft_split`, `ft_strjoin` y `ft_itoa` requieren una asignación de memoria dinámica y precisa. Aprendes a asignar exactamente lo que se necesita (incluyendo el terminador nulo `\0`) y a liberarlo adecuadamente para evitar fugas de memoria.
*   **Manipulación de Memoria:** Funciones como `ft_memset`, `ft_memcpy`, `ft_memmove` y `ft_bzero` requieren una manipulación cruda de la memoria byte por byte utilizando punteros `unsigned char`, enseñando cómo se estructuran y acceden de manera segura los bloques contiguos de memoria sin desbordamientos de búfer.
*   **Memoria Superpuesta:** `ft_memmove` aborda específicamente el desafío de los bloques de memoria superpuestos, requiriendo lógica condicional para copiar de adelante hacia atrás o de atrás hacia adelante dependiendo de las direcciones de los punteros.

### 2. Implementación de Estructuras y Listas Enlazadas (Bonus)
La parte bonus del proyecto introduce las estructuras de datos dinámicas a través de la implementación de Listas Enlazadas Simples.
```c
typedef struct s_list
{
    void            *content;
    struct s_list   *next;
} t_list;
```

*   **Punteros Void (void \*):** La variable content es un puntero void, lo que significa que la lista enlazada es polimórfica y puede almacenar cualquier tipo de dato (cadenas, enteros, otras estructuras). Esto enseña el casting de tipos y la programación genérica en C.
*   **Enlace y Recorrido de Nodos:** Funciones como ft_lstadd_back y ft_lstmap enseñan cómo recorrer estructuras dinámicas, enlazar nodos de memoria separados y aplicar de forma segura punteros a funciones a lo largo de un conjunto de datos completo.

### 3. Operaciones a Nivel de Bits e Intercambio de Datos

Mientras que la biblioteca estándar trata en gran medida con caracteres y cadenas, las optimizaciones subyacentes a menudo requieren una comprensión a nivel de bits:
*   **Intercambio de Bits:** Intercambiar datos eficientemente es un concepto algorítmico fundamental. Mientras que los intercambios estándar usan una variable temporal, los intercambios XOR a nivel de bits `(a ^= b; b ^= a; a ^= b;)` se pueden implementar en funciones de utilidad personalizadas para intercambiar valores a nivel de registro sin asignar memoria extra.
*   **Desplazamiento y Enmascaramiento de Bits:** La comprensión de los valores ASCII para ft_toupper o ft_tolower se puede optimizar mediante operaciones a nivel de bits (por ejemplo, invertir el sexto bit para cambiar entre letras mayúsculas y minúsculas).

---

## 🛠️ Resumen de Funciones
### Parte 1 - Funciones de Libc

Re-implementaciones de funciones estándar de la biblioteca de C:
*   **Memoria:** `ft_memset`, `ft_bzero`, `ft_memcpy`, `ft_memmove`, `ft_memchr`, `ft_memcmp`, `ft_calloc`.
*   **Cadenas/Caracteres:** `ft_strlen`, `ft_strlcpy`, `ft_strlcat`, `ft_strchr`, `ft_strrchr`, `ft_strncmp`, `ft_strnstr`, `ft_strdup`.
*   **Verificación de tipos:** `ft_isalpha`, `ft_isdigit`, `ft_isalnum`, `ft_isascii`, `ft_isprint`.
*   **Transformación:** `ft_toupper`, `ft_tolower`, `ft_atoi`.

### Parte 2 - Funciones Adicionales

Funciones que no forman parte de la libc estándar pero que son extremadamente útiles para futuros proyectos:
*   **Manipulación de Cadenas:** `ft_substr`, `ft_strjoin`, `ft_strtrim`, `ft_split`, `ft_strmapi`, `ft_striteri`.
*   **Conversión:** `ft_itoa`.
*   **Descriptores de Archivo (E/S):** `ft_putchar_fd`, `ft_putstr_fd`, `ft_putendl_fd`, `ft_putnbr_fd`.

### Parte Bonus - Listas Enlazadas
Funciones para manipular la estructura t_list:

`ft_lstnew`, `ft_lstadd_front`, `ft_lstsize`, `ft_lstlast`, `ft_lstadd_back`, `ft_lstdelone`, `ft_lstclear`, `ft_lstiter`, `ft_lstmap`.

---

## 🚀 Compilación y Uso
Este proyecto incluye un Makefile que compila los archivos fuente en una biblioteca estática (libft.a).
### Instrucciones
1. Clona el repositorio:
```Bash
git clone [https://github.com/your-username/libft.git](https://github.com/your-username/libft.git)
cd libft
```

2. Compila la biblioteca:
```Bash
make
```

Esto generará el archivo `libft.a`.

3. Compila con las funciones bonus (Listas Enlazadas):
```Bash
make bonus
```

4. Limpia los archivos objeto:
```Bash
make clean
```

5. Limpia todos los archivos generados (objetos y biblioteca):
```Bash
make fclean
```
---

## Usándolo en tus proyectos

Para usar libft en tus futuros proyectos de C, incluye el archivo de cabecera en tus archivos C:
```C
#include "libft.h"
```

Y compila tu proyecto con la biblioteca:
```Bash
gcc -Wall -Wextra -Werror your_file.c -L. -lft
```