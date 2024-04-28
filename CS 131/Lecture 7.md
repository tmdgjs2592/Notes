Why do we have types
- Correctness of operations
- Speed (helping compiler)
- documentation or annotation (help the reader)
What are types
- What you know about an expression statically
- A category of values sharing operations
- Ways to interpret bits in memory
Static vs dynamic type checking
- Static: C, C++, Java, OCaml
- Dynamic: Python, Java
- Strongly typed: language that makes sure the type is correct when you cast (string)
Type equivalence
- Name equivalence vs structural equivalence
```cpp
struct s{double re, im;};
struct t{double re, im;};
struct s a;
struct t b;
a=b;
```
- In terms of name equivalence, a $\neq$ b 
- In terms of structural equivalence a=b
- Name equivalence $\rightarrow$ struct
- Structural equivalence $\rightarrow$ typedef
**Polymorphism (Overloading)**
When a function can accept many forms and return many forms.
EX:
$$ sin(x)$$
sin(x) can take float and double type.
- float $\rightarrow$ float or double $\rightarrow$ double
**Coercion - converting values from one type to another**
```cpp
double f(double, float);
double f(float, double);
float x;
f(x,x);
```
This will cause an error since there are two ways to coerce $\rightarrow$ ambiguity

**Parametric Polymorphism (ad hoc polymorphism)**

```cpp
typedef char *T
typedef char const *u
T x; U y;
x=y;
y=x;
```