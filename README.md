<!---
{
  "id": "0b6b3ce8-418e-4900-ae42-a6d068389a12",
  "teaches": "Expressions and Functions",
  "depends_on": ["61354751-6887-4761-9ef0-ca25d237cf1c"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-02",
  "keywords": ["C Language", "Expressions", "Functions", "Operators"]
}
--->

# Expressions and Functions

## 1) Introduction
Expressions are the building blocks of computation — they represent values and operations. Functions let us abstract and name these computations.

In C, an **expression** is anything that can be *evaluated* (produces a value). This can be:
- a literal like `42`
- a variable like `x`
- a combination like `x + 3`
- a function call like `sqrt(x)`

Expressions always have a **type** and (usually) a **value**. Even assignments like `x = 4` are expressions in C — they evaluate to the assigned value.

To organize expressions and reuse logic, we group them into **functions**. A function is a named block of code that receives input (parameters) and returns a value. 
```C
return_type function_identifier (input_parameter_type_n local_input_parameter_identifier_n, ...)
{
  //definition: parameter values can be accessed by the local input parameter identifier
  return identifier_or_expression;  //the value-type must match the functions return-type
}
```

A function in C can be thought of as a **mapping** — from an object of the cartesian product of its input types to a single output type:

- `int add(int a, int b)` represents a function from Z × Z → Z
- `char to_ascii(int code)` might be seen as Z → Σ, where Σ is the character set
- `float half(float x)` defines a mapping from R → R

Understanding functions in this way allows us to reason more formally about **input**, **output**, and **side effects**.

Let’s review how all these pieces fit:
- An **identifier** names something (a variable, function, constant)
- An **expression** produces a value (e.g. `x + 3` or `sqrt(a*b)`)
- A **statement** does something (e.g. assignment, function call, control flow)
- An **operator** transforms or combines values (e.g. `+`, `-`, `*`, `/`)

Every function body is a collection of statements, many of which are made up of expressions.

## 2) Tasks
1. **Define Simple Functions**: Write the following functions:
   - `int add(int a, int b)` returns the sum
   - `float average(float x, float y)` returns the average
   - `char grade(int score)` returns 'A', 'B', etc., depending on score

2. **Use in `main()`**: Place the functions within your source-file above the start of `main()`. Call these functions from `main()` with example values and print the result using `printf`.
3. **Use in `main()`**: Place the functions below the end of `main()`. Call these functions from `main()` with example values and print the result using `printf`.
4. **Use in `main()`**: Place only the signature (`int add(int, int)` above the start of `main()`, leave the implementations below the end of `main()`. Call these functions from `main()` with example values and print the result using `printf`.
5. **#include "signatures.h"**: Run `gcc -E` on your current `main.c` file and redirect the output into a temporary file. Place the signatures in another file in the same directory called `signatures.h`. Use the preprocessor-directive `#include "signatures.h"` in the place where you formerly wrote the signatures themself. Run `gcc -E` and pipe it into a second file. Use `vimdiff` to compare the files. 

6. **Expression Trees**: Given `3 + a * (b - 2)`, draw the expression as a tree on paper or using ASCII.

7. **Function as Expression**: Assign the result of a function call to a variable: `int result = add(5, 6);`

8. **Compose Functions**: Call one function from inside another: `grade(add(a, b));`

## 3) Questions
1. What’s the difference between an expression and a statement in C?
2. Why can assignments like `x = y = z = 0;` be chained?
3. What is the return type of an expression like `x + 1.0` if `x` is `int`?
4. Can a function return the result of another function? What is evaluated first?
5. How does the compiler know the type of an expression?

## 4) Advice
Use `gcc -Wall -Wextra -o test test.c` to find type-related issues early. Try breaking long expressions into smaller sub-expressions and assign them to variables to understand their type and value. Don’t fear nesting — just make sure each function has one clear responsibility and its return type fits its purpose.
