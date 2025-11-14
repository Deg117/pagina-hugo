---
title: "Práctica 1"
date: 2025-01-01
draft: false
---

             Universidad Autónoma De Baja California

                             Paradigmas 

                             Grupo-941

                             Practica 0

                             26/09/2025
                     
                             Alumno:

                Gastelum fierro Brian de Jesus

                        Profesor. 

                    Carlos Gallegos
                    Introduccion :
Para esta practica se espera que el alumno identifique los elementos fundamentales de los lenguajes de programación como los on nombre,marcos de activación, bloques de alcance, administración de memoria,expresiones, comandos, control de secuencia como lo es ; selección, iteración y recursión, subprogramas, y tipos de datos.

Instrucciones:
Identificar estos conceptos en la aplicación propuesta para esta práctica.

Elaborar un pdf para el reporte a entregar lo echo 

- Variables:
 -Globales: static_var (estática, segmento de datos), bss_var (BSS, no inicializada).
 -Locales (stack): library, members, bookCount, memberCount, choice (en main), new_book,current, bookFound, memberFound, etc.
- Campos de estructuras: id, title, author, publication_year, genre, quantity, next,id, name, issued_count, issued_books, next (en member_t).
- Funciones:
 genreToString, addBook, ndBookById, displayBooksRecursive, displayBooks, addMember,issueBook, returnBook, freeLibrary, freeMembers,saveLibraryToFile, loadLibraryFromFile,saveMembersToFile, loadMembersFromFile, displayMembers, searchMember, main.
- Tipos de nidos:
 genre_t (enumeración).
 book_t, member_t (estructuras).
- Constantes:
 Enumeradores: FICTION, NON_FICTION, SCIENCE, HISTORY, FANTASY, BIOGRAPHY, OTHER.
 Cadenas literales: "Error al asignar memoria", "library.txt".

- Marcos de activación
 Los marcos de activación (o registros de activación) son áreas en el stack que almacenan información
 sobre una llamada a función, incluyendo parámetros, variables locales y el valor de retorno. En este
- código:
 Ejemplos de marcos de activación:
 En addBook: parámetros (library, count), variables locales (new_book, genre).
- main: variables locales (library, members, bookCount, memberCount, choice).
 Cada llamada a función hace un marco de activación en el stack, que se libera al retornar.
 Comportamiento:
 Las variables locales como new_book en addBook o current en ndBookById se almacenan.
Los parámetros (library, count) se pasan por valor o puntero, almacenados en el marco de activación de la función.
- Bloques de alcance
 Alcance global:
 Variables: static_var (estática, alcance de archivo), bss_var (global, no inicializada).
 De niciones: genre_t, book_t, member_t.
 Alcance de función:
 Variables locales en funciones como new_book en addBook, current en ndBookById.
 Alcance de bloque:
 Dentro de bucles o condicionales, como i en el bucle for de issueBook:

 for (int i = 0; i < memberFound->issued_count; i++) 
 
 Aquí, i solo existe dentro del bucle.
 Alcance estático:
 static_var tiene alcance de archivo, pero su vida útil es durante toda la ejecución del
 programa.
- Administración de memoria
 El código utiliza varios esquemas de memoria:
 Segmento de datos:
 static_var (inicializada, estática).
Cadenas literales como "Ficcion".
 Segmento BSS:
 bss_var (global no inicializada).
 Stack:
- Variables locales automáticas: library, members, bookCount, choice, etc.
- Parámetros de funciones: library, count en addBook.
 Heap:
 Asignación dinámica con malloc y realloc:
 En addBook: new_book = (book_t *)malloc(sizeof(book_t)).
 En issueBook: realloc para issued_books.
 Liberación con free:
 En freeLibrary: free(current) para cada nodo de la lista book_t.
 En freeMembers: free(current->issued_books) y free(current).
- Seguimiento de memoria:
 Funciones como incrementHeapAllocations y incrementHeapDeallocations (de nidas en
 memory_management.h) rastrean asignaciones y liberaciones.
- Gestión explícita:
 El código veri ca errores de asignación (if (!new_book)).
 Usa listas enlazadas (next) para gestionar estructuras dinámicas (book_t, member_t).
- Expresiones
 Las expresiones son combinaciones de operandos y operadores que producen un valor. Ejemplos:
 Aritméticas:
 (*count)++ en addBook.
 bookFound->quantity en issueBook.
 Lógicas:
 if (bookFound && memberFound) en issueBook.
 while (current) en ndBookById.
 Asignación:
 new_book->id = scanf("%d", &new_book->id) (lectura).
 new_book->next = *library en addBook.
 Llamadas a funciones:
 genreToString(library->genre) en displayBooksRecursive.
 malloc(sizeof(book_t)) en addBook.
 Comparaciones:
 if (current->id == bookID) en ndBookById.
 strcmp(genre_str, "Ficcion") == 0 en loadLibraryFromFile.
- Comandos
 Los comandos son instrucciones en el programa. Ejemplos:
 Asignaciones:
 new_book->quantity = scanf("%d", &new_book->quantity) en addBook.
 memberFound->issued_books = realloc(...) en issueBook.
 Entrada/salida:
 printf("Ingresa ID del libro: ") en addBook.
 fscanf( le, "%d\n", &new_book->id) en loadLibraryFromFile.
 Control de ujo:
 if, switch, while, for (ver control de secuencia).
 return NULL en ndBookById.
 Llamadas a funciones:
 incrementHeapAllocations(new_book, sizeof(book_t)) en addBook.
 fclose( le) en saveLibraryToFile.
 El control de secuencia incluye selección, iteración y recursión:
 Selección:
 if-else:
 if (!new_book) { 
   printf("Error al asignar memoria...\n"); 
} 
    return; 
En addBook, veri ca si la asignación de memoria falló.
 switch:
 switch (genre) { 
    case FICTION: return "Ficcion"; 
} 
En genreToString, selecciona una cadena según el valor de genre.
 Iteración:
 while:
 while (current) { 
    if (current->id == bookID) { 
        return current; 
    }
    current = current->next; 
} 
En ndBookById, recorre la lista de libros.
 for:
 for (int i = 0; i < memberFound->issued_count; i++) { 
    if (memberFound->issued_books[i] == bookID) { 
        ... 
    }
 } 
En returnBook, busca un libro en la lista de prestados.
 Recursión:
 En displayBooksRecursive:
 void displayBooksRecursive(book_t *library) { 
    if (!library) return; 
    printf(...); 
Page 6 of 15
} 
    displayBooksRecursive(library->next); 
Recorre la lista de libros recursivamente.
- Subprogramas
 Los subprogramas son funciones que encapsulan tareas especícas. En el código:
 Funciones:
 addBook: Agrega un libro a la lista.
 ndBookById: Busca un libro por ID.
 displayBooksRecursive: Muestra libros recursivamente.
 issueBook: Presta un libro a un miembro.
 freeLibrary: Libera memoria de la lista de libros.
 main: Punto de entrada, controla el ujo del programa.
 Características:
 Parámetros: Por valor (int bookID) o puntero (book_t library).
 Retorno: const char en genreToString, book_t en ndBookById, void en addBook.
 Modularidad: Cada función realiza una tarea especí ca, como agregar, prestar o liberar.
- Tipos de datos
 El código utiliza varios tipos de datos:
 Primitivos:
 int: id, publication_year, quantity, bookCount.
 char: Arreglos como title[100], author[100].
 FILE*: Para manejar archivos en saveLibraryToFile.
 De nidos por el usuario:
 Enumeración:
 typedef enum { FICTION, NON_FICTION, ... } genre_t; 
- Estructuras:
 typedef struct _book { 
    int id; 
    char title[100];  
    struct _book *next; 
} book_t; 
Representa un libro con un enlace al siguiente.
 typedef struct _member { 
    int id; 
    char name[100]; 
    struct _member *next; 
} member_t; 

                        memory_management.c
- Variables:
Globales: heap_allocations, heap_deallocations, stack_allocations, stack_deallocations (contadores para seguimiento de memoria).
 Global con puntero: heap_memory_records (puntero a una lista de registros de memoria).
 Locales: record (en addMemoryRecord), current (en removeMemoryRecord)
- Funciones:
 addMemoryRecord, removeMemoryRecord, displayMemoryUsage, incrementHeapAllocations,
 incrementHeapDeallocations, incrementStackAllocations, incrementStackDeallocations.
 Estructuras:
 MemoryRecord (de nida con typedef).
 Constantes:
 MEMORY_MANAGEMENT_DISPLAY (macro condicional para controlar la salida de depuración).
 Marcos de activación
 Los marcos de activación son áreas en el stack para las variables locales y parámetros de una función.
 Elementos únicos:
 En addMemoryRecord:
 Parámetros: pointer (tipo void*), size (tipo size_t).
 Variable local: record (tipo MemoryRecord*).
 El marco de activación almacena estas variables y se libera al retornar.
 En removeMemoryRecord:
 Parámetro: pointer (tipo void*).
 Variables locales: current (tipo MemoryRecord**), to_free (tipo MemoryRecord*).
 En displayMemoryUsage:
 Variable local: current (tipo MemoryRecord*).
- Bloques de alcance
 Los bloques de alcance determinan la visibilidad y vida útil de los nombres. Elementos únicos:
 Alcance global:
Variables: heap_allocations, heap_deallocations, stack_allocations, stack_deallocations,
 heap_memory_records.
 Estas variables son accesibles en todo el programa y persisten durante toda la ejecución.
 Alcance de función:
 En addMemoryRecord: record solo es visible dentro de la función.
 En removeMemoryRecord: current y to_free son locales a la función.
 En displayMemoryUsage: current es local.
 Alcance condicional (por macro):
 Las funciones incrementHeapAllocations y incrementHeapDeallocations tienen bloques condicionales
 controlados por #if MEMORY_MANAGEMENT_DISPLAY, que afectan la visibilidad de las llamadas a printf
 dentro de esos bloques.
- Administración de memoria
 Este código se centra en la gestión de memoria, con elementos únicos:
 Segmento de datos:
 Variables globales inicializadas: heap_allocations, heap_deallocations, stack_allocations,
 stack_deallocations (inicializadas en 0).
 Heap:
 Asignación dinámica:
 En addMemoryRecord: record = (MemoryRecord *)malloc(sizeof(MemoryRecord)) asigna memoria para
 un nuevo registro.
 Liberación:
 En removeMemoryRecord: free(to_free) libera un nodo de la lista de registros.
 Lista enlazada para seguimiento:
 heap_memory_records es una lista enlazada que registra punteros y tamaños de memoria asignada en
 el heap.
 addMemoryRecord agrega un nodo a esta lista.
 removeMemoryRecord elimina un nodo especí co.
 Seguimiento de memoria
 Contadores globales (heap_allocations, heap_deallocations) rastrean el número de asignaciones y
 liberaciones en el heap.
 Contadores stack_allocations y stack_deallocations (aunque no se usan explícitamente en el código
 previo para asignaciones automáticas).
 Condicionalidad:
 La macro MEMORY_MANAGEMENT_DISPLAY controla si se muestran mensajes de depuración (printf)
 sobre asignaciones y liberaciones.
- Expresiones
 Expresiones únicas en este código:
 Asignación:
 record->pointer = pointer y record->size = size en addMemoryRecord.
 heap_memory_records = record en addMemoryRecord.
 Punteros y desreferenciación:
 (*current)->pointer == pointer en removeMemoryRecord (compara el puntero almacenado).
 current = &(*current)->next en removeMemoryRecord (avanza al siguiente nodo).
 Incrementos:
 heap_allocations++ en incrementHeapAllocations.
 heap_deallocations++ en incrementHeapDeallocations.
 Formato de cadenas:
 En displayMemoryUsage: printf("| 0x%-14p | %-27zu |\n", current->pointer, current->size) para
 mostrar punteros y tamaños.
- Comandos
 Comandos únicos (instrucciones ejecutables):
 Asignaciones:
 record->next = heap_memory_records en addMemoryRecord.
 current = (current)->next en removeMemoryRecord.
 Entrada/salida
 En displayMemoryUsage:
 printf("|   Asignaciones: %-28d |\n", heap_allocations); 
Muestra contadores de memoria.
 En incrementHeapAllocations:
 printf("Memoria asignada en el heap: Puntero=0x%p, Tamano=%zu bytes\n", p
 Liberación de memoria:
 free(to_free) en removeMemoryRecord.
- Control de secuencia
 Elementos únicos de control de secuencia:
 Selección:
 if:
 if ((*current)->pointer == pointer) { 
    MemoryRecord *to_free = *current; 
    *current = (*current)->next; 
    free(to_free); 
    return; 
} 
En removeMemoryRecord, veri ca si el puntero coincide para eliminar el registro.
 Iteración:
 while:
 while (*current) { 
    ... 
    current = &(*current)->next; 
} 
En removeMemoryRecord, recorre la lista para encontrar el puntero. 
cwhile (current) { 
    printf("| 0x%-14p | %-27zu |\n", current->pointer, current->size); 
    En displayMemoryUsage, muestra todos los registros de memoria.
 Recursión:
 No hay recursión explícita en este código (a diferencia del código anterior con
 displayBooksRecursive).
 Directivas de preprocesador:
 #if MEMORY_MANAGEMENT_DISPLAY controla condicionalmente la ejecución de printf en
 displayMemoryUsage, incrementHeapAllocations y incrementHeapDeallocations.
- Subprogramas
 Subprogramas (funciones) únicos en este código:
 addMemoryRecord(void pointer, size_t size):
 Crea un nuevo nodo MemoryRecord y lo agrega a la lista heap_memory_records.
 removeMemoryRecord(void pointer):
 Busca y elimina un nodo de la lista heap_memory_records basado en el puntero.
 displayMemoryUsage():
 Muestra estadísticas de memoria (contadores y detalles de heap).
 incrementHeapAllocations(void pointer, size_t size):
 Incrementa el contador de asignaciones y registra el puntero/tamaño.
 incrementHeapDeallocations(void pointer):
 Incrementa el contador de liberaciones, elimina el registro.
 incrementStackAllocations() y incrementStackDeallocations():
 Incrementan contadores para el stack (aunque no se usan en el código previo).

 [repositorio](https://github.com/Deg117/Portafolio)
