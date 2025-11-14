---
title: "Práctica 2"
date: 2025-01-01
draft: false
---

# Universidad Autónoma de Baja California  
## Facultad de Ingeniería, Arquitectura y Diseño (FIAD)  
### Ingeniería en Software


**Docente:** Carlos gallegos

**Estudiante:** Brian De Jesús Gastélum Fierro  
**Matrícula:** 373408

**Fecha de entrega:** 16/10/2025  

---


### `biblioteca.py`
Contiene la **lógica central del sistema de biblioteca**, incluyendo las clases:
- `Book`, `DigitalBook`, `Member`, y `Library`, que representan los objetos principales.
- Implementa operaciones como agregar libros, registrar miembros, prestar y devolver libros.
- Define la función `main()` que ejecuta el programa en consola y maneja el menú interactivo.

### `biblioteca_web.py`
Implementa la **versión web del sistema** usando el framework **Flask**, proporcionando una API REST:
- Rutas como `/books`, `/members`, `/issue_book`, `/return_book`, `/save` y `/load`.
- Utiliza `render_template()` para desplegar la interfaz en `index.html`.
- Permite la conexión entre el backend en Python y el frontend con HTML, CSS y JavaScript.

### `memory_management.py`
Simula la **administración de memoria** con la clase `MemoryManagement`:
- Registra asignaciones y liberaciones de memoria con los métodos `increment_heap_allocations()` y `increment_heap_deallocations()`.
- Se integra con las clases de `biblioteca.py` para reflejar el consumo de memoria al crear o eliminar objetos.

---

#  Identificación de Elementos Fundamentales de los Lenguajes 

## 1. Nombres
En el sistema de biblioteca, los **nombres** identifican variables, funciones, clases y objetos.  
Ejemplos:  
- `Book`, `Member`, `Library`, `DigitalBook` — nombres de clases.  
- `book_id`, `title`, `author`, `genre`, `quantity` — variables de instancia.  
- `add_book()`, `find_book_by_id()` — métodos que definen comportamientos.  

## 2. Marcos de Activación 
Cada vez que se ejecuta una función o método se crea un **marco de activación** en la pila, que guarda:  
- Variables locales (por ejemplo, `book` o `member_id` en `add_book()`).  
- Dirección de retorno.  
- Resultados temporales.  

Ejemplo: la llamada `library.add_book(book)` genera su propio marco de ejecución independiente.

## 3. Bloques de Alcance 
El **alcance** determina dónde se pueden usar las variables:  
- Variables de instancia (`self.books`) → alcance del objeto.  
- Variables dentro de métodos → alcance local.  
- Constantes de clase (`Genre.FICTION`) → alcance de clase.

## 4. Administración de Memoria
El archivo `memory_management.py` controla la **simulación del manejo de memoria**:  
```python
self.heap_allocations += size
self.heap_deallocations += size
```
Los constructores (`__init__`) y destructores (`__del__`) de las clases aumentan o liberan memoria con:
```python
memory_management.increment_heap_allocations(1)
memory_management.increment_heap_deallocations(1)
```
Esto simula la gestión de memoria dinámica (heap).

## 5. Expresiones
Las **expresiones** combinan valores, operadores y funciones:  
- `book.quantity -= 1` → resta un libro del inventario.  
- `int(data['id'])` → conversión de tipo.  
- `book.to_dict()` → retorna un diccionario del objeto.

## 6. Comandos (Sentencias)
Las **sentencias** ejecutan acciones o controlan el flujo:  
```python
if book and member and book.quantity > 0:
    book.quantity -= 1
    member.issued_books.append(book_id)
```
Aquí hay comandos de control (`if`), asignación (`-=`) y métodos (`append`).

## 7. Control de Secuencia
El código usa los tres tipos principales:

### a) Selección  
```python
if is_digital:
    book = DigitalBook(...)
else:
    book = Book(...)
```

### b) Iteración  
```python
for book in self.books:
    print(book.title)
```

### c) Recursión  
No hay recursión explícita, pero el diseño podría extenderse para búsqueda recursiva o conteo.

## 8. Subprogramas
Son las **funciones y métodos** del sistema:  
- En `biblioteca.py`: `add_book()`, `issue_book()`, `display_books()`, etc.  
- En `biblioteca_web.py`: rutas como `get_books()` y `add_member()` (decoradas con `@app.route`).  
- En `memory_management.py`: `display_memory_usage()`.  

Cada uno cumple un propósito modular y puede recibir argumentos y devolver valores.

## 9. Tipos de Datos
Se manejan distintos tipos:  
- **Primitivos:** `int`, `str`, `bool`.  
- **Compuestos:** `list`, `dict`.  
- **Personalizados:** `Book`, `Member`, `Library`, `DigitalBook`.  
Ejemplo:  
```python
json.dump([book.to_dict() for book in self.books], file)
```  
Convierte objetos a estructuras JSON.

---

## conclusión
La aplicación integra todos los elementos  de los lenguajes de programación, mostrandonos:  
- **nombres** y **tipos de datos**.  
- **Subprogramas**  estructurados.  
- Simulación de **administración de memoria**.  
- **Bloques de alcance** definidos y control  

