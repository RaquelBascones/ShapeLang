# Shapelang – Lenguaje de Figuras

Shapelang es un lenguaje visual no convencional basado en figuras geométricas que representan operaciones, números y estructuras de control.  
El proyecto combina arte y programación: las figuras se interpretan siguiendo un sistema de pila (stack) y se traducen a notación polaca inversa (RPN), que después se ejecuta de forma animada mediante una máquina virtual.

---

## Objetivo del proyecto

- Crear un lenguaje interpretado físico, donde las figuras geométricas actúan como tokens.  
- Desarrollar una máquina virtual con pila que procese operaciones, bucles y condiciones.  
- Mostrar la ejecución paso a paso (historial de pila y registro de operaciones).  
- Integrar el concepto de RPN (Reverse Polish Notation) para eliminar la necesidad de paréntesis.  
- Servir como herramienta educativa para enseñar lógica y programación de manera visual.

---

## Estructura del lenguaje (según la app)

### Dígitos (0–9)

Se representan como **figuras moradas** y se apilan directamente en la pila.

| Dígito | Figura en la interfaz |
|--------|------------------------|
| 0 | Círculo vacío (trazo morado) |
| 1 | Círculo con trazo morado más grueso |
| 2 | Barra horizontal morada |
| 3 | Triángulo morado |
| 4 | Rombo morado |
| 5 | Pentágono morado |
| 6 | Hexágono morado |
| 7 | Heptágono morado |
| 8 | Octágono morado |
| 9 | Eneágono morado |

> El color morado indica que son **valores numéricos**.

---

### Operadores aritméticos

Botones blancos con borde negro. Cada operador consume dos valores de la pila y apila el resultado.

| Operador | Botón | Descripción |
|-----------|--------|--------------|
| `+` | círculo con “+” | Suma |
| `-` | cuadrado con “−” | Resta |
| `*` | triángulo con “*” | Multiplicación |
| `/` | cuadrado con “/” | División (redondeo con `Math.round`) |
| `//` | rectángulo con “∥” | División entera (también redondeo) |
| `%` | pentágono con “%” | Módulo |
| `**` | hexágono con “^” | Potencia |

---

### Comparaciones

También son botones blancos con borde negro. Devuelven `1` (verdadero) o `0` (falso).

| Operador | Descripción |
|-----------|--------------|
| `>` | Mayor que |
| `<` | Menor que |
| `==` | Igualdad |
| `!=` | Distinto |

---

### Estructuras y control

| Token | Apariencia | Comportamiento |
|--------|-------------|----------------|
| `IF`, `ELIF`, `ELSE`, `DO`, `END` | Botones rectangulares blancos | Se **expanden antes** de ejecutar: se evalúa la condición y se inserta solo el bloque correcto. |
| `FOR` | Botón rectangular blanco | Repite el bloque N veces y añade un `POP` al final de cada vuelta (pop pospuesto). |
| `PRINT` | Hexágono morado | Muestra el tope de la pila **sin quitarlo** (post-operación). |
| `(`, `)` | Paréntesis negros | Solo afectan al orden (no modifican la pila). |

---

### Resumen operativo

- **Números:** `push n`  
- **Operadores:** consumen dos valores, apilan el resultado  
- **Comparaciones:** consumen dos valores, apilan `0` o `1`  
- **PRINT:** muestra el tope, no hace `pop`  
- **FOR:** expansión + `POP` final por iteración  
- **IF / ELIF / ELSE:** expansión del bloque válido  
- **Paréntesis:** afectan al orden, no a la pila

---

## Funcionamiento general

1. **Interpretación humana:** las figuras se traducen a símbolos numéricos o lógicos.  
2. **Conversión a RPN:** se genera la notación polaca inversa mediante un algoritmo tipo *shunting-yard*.  
3. **Expansión:** se resuelven los bloques (`IF`, `FOR`, `ELSE`, etc.) antes de ejecutar.  
4. **Ejecución animada:** la pila se actualiza paso a paso, mostrando los resultados y el historial visual.


---

## Estructuras de control

### FOR n DO … END

Repite un bloque n veces.  
Después de cada vuelta se ejecuta un `POP` automático para limpiar la pila.

### IF / ELIF / ELSE

Evalúa una condición y expande solo el bloque verdadero antes de la ejecución.  
Las condiciones devuelven `1` (verdadero) o `0` (falso).

---
