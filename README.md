# Shapelang – Visual Language Based on Geometric Figures

Shapelang is an unconventional visual programming language based on geometric figures that represent operations, numbers, and control structures.  
The project combines art and programming: the figures are interpreted using a stack-based system and translated into Reverse Polish Notation (RPN), which is then executed step by step through a visual virtual machine.

---

## Table of Contents
1. [Project Objectives](#project-objectives)
2. [Language Structure](#language-structure-as-implemented-in-the-app)
   - [Digits (0–9)](#digits-09)
   - [Arithmetic Operators](#arithmetic-operators)
   - [Comparisons](#comparisons)
   - [Control and Logic Structures](#control-and-logic-structures)
   - [Operational Summary](#operational-summary)
3. [Control Structures](#control-structures)
4. [Repository Files](#repository-files)
5. [Local Execution](#local-execution)
6. [Academic Context](#academic-context)



## Project Objectives

- Create a physical interpreted language where geometric figures act as tokens.  
- Develop a stack-based virtual machine capable of processing operations, loops, and conditions.  
- Display step-by-step execution (stack history and operation log).  
- Integrate the RPN (Reverse Polish Notation) concept to eliminate the need for parentheses.  
- Serve as an educational tool to teach logic and programming in a more visual and intuitive way.

---

## Language Structure (as implemented in the app)

### Digits (0–9)

Digits are represented as **purple figures** and are directly pushed onto the stack.

| Digit | Figure in the interface |
|--------|--------------------------|
| 0 | Empty circle (purple outline) |
| 1 | Circle with thicker purple outline |
| 2 | Horizontal purple bar |
| 3 | Purple triangle |
| 4 | Purple diamond |
| 5 | Purple pentagon |
| 6 | Purple hexagon |
| 7 | Purple heptagon |
| 8 | Purple octagon |
| 9 | Purple enneagon |

> The purple color indicates **numeric values**.

---

### Arithmetic Operators

White buttons with black borders. Each operator consumes two values from the stack and pushes the resulting value.

| Operator | Button | Description |
|-----------|--------|-------------|
| `+` | Circle with “+” | Addition |
| `-` | Square with “−” | Subtraction |
| `*` | Triangle with “*” | Multiplication |
| `/` | Square with “/” | Division (rounded using `Math.round`) |
| `//` | Rectangle with “∥” | Integer division (also rounded) |
| `%` | Pentagon with “%” | Modulo |
| `**` | Hexagon with “^” | Power |

---

### Comparisons

Also represented by white buttons with black borders. These operators return `1` (true) or `0` (false).

| Operator | Description |
|-----------|-------------|
| `>` | Greater than |
| `<` | Less than |
| `==` | Equal to |
| `!=` | Not equal to |

---

### Control and Logic Structures

| Token | Appearance | Behavior |
|--------|-------------|-----------|
| `IF`, `ELIF`, `ELSE`, `DO`, `END` | White rectangular buttons | **Expanded before execution**: the condition is evaluated and only the correct block is inserted. |
| `FOR` | White rectangular button | Repeats the block N times and adds a `POP` at the end of each iteration (deferred pop). |
| `PRINT` | Purple hexagon | Displays the top of the stack **without removing it** (post-operation). |
| `(`, `)` | Black parentheses | Affect only operation order (do not modify the stack). |

---

### Operational Summary

- **Numbers:** `push n`  
- **Operators:** consume two values, push the result  
- **Comparisons:** consume two values, push `0` or `1`  
- **PRINT:** displays the top value, does not pop it  
- **FOR:** expansion + final `POP` per iteration  
- **IF / ELIF / ELSE:** expands only the valid block  
- **Parentheses:** affect order but not stack contents

---

## General Operation

1. **Human interpretation:** figures are translated into numeric or logical symbols.  
2. **RPN conversion:** expressions are transformed into Reverse Polish Notation using a *shunting-yard* algorithm.  
3. **Expansion:** control blocks (`IF`, `FOR`, `ELSE`, etc.) are expanded before execution.  
4. **Animated execution:** the stack updates step by step, displaying the results and the visual execution history.

---

## Control Structures

### FOR n DO … END

Repeats a block `n` times.  
After each iteration, an automatic `POP` is executed to clean the stack.

### IF / ELIF / ELSE

Evaluates a condition and expands only the true block before execution.  
Conditions return `1` (true) or `0` (false).

---

## Repository Files

| File | Description |
|----------|-------------|
| `VM_correcto.html` | Web application of the language: visual interface with figures, RPN parser, and animated execution. |
| `MV2.0.py` | Python version of the stack-based Virtual Machine that processes the language’s instructions. |
| `proyecto 1- figuras geométricas 2.pdf` | Project documentation explaining the language and its presentation. |
| `README.md` | Informational document detailing the structure, goals, and usage guide for the project. |

---

## Local Execution

1. Clone or download the repository:
   ```bash
   git clone https://github.com/<your-username>/GeoStack-LenguajeDeFiguras.git
   ```
2. Open the file `index.html` in a browser.  
3. Use the buttons to place figures, build expressions, and execute step-by-step.  
4. Observe the stack history and the operation log.

---

## Academic Context

Project developed for the **Languages and Programming Paradigms** course.  
It combines RPN, stack, and a visual language based on geometric figures.  
The objective is to physically and visually demonstrate how an interpreted language behaves.

---





   

