****
**Imperative language**
- The program issues commands to the computer and computer executes each line of command
- Imperative language is bad in parallel operation because of the structure.
	- Shell has some way to operate in parallel
- Von Neumann bottleneck: the amount of work it can do is limited by the bandwidth of connection between CPU and memory
**Functional Language**
- no sequencing like imperative language
- no side effects $\rightarrow$ no assignments to variables like i=1
**Logic Language**
- Uses Predicate: Operations that check if the condition is true.
****
**ML basic properties**
- Compile-time type checking (static time checking)
	- OCaml checks types before the program runs
- Type inference → The compiler figures out the type
- No storage operation (delete or free)
	- When the program is executed, OCaml keeps track of the lifetime of variables and frees them when they are no longer needed (Garbage Collector)
- Higher order function
	- a function which returns another function
- Every element of the list has to be the same type
- Tuple can have multiple types
- () $\rightarrow$ unit tuple, tuple with nothing
- [] $\rightarrow$ 'a list
****
**OCaml Pattern Matching**
- _ matches anything but used to discard the result
- P::Q matches nonempty list that P matches head and Q matches tail
- P,Q,R matches tuple
- [P;Q;R] matches list
- +. $\rightarrow$ floating operation
- OCaml is strict when it comes to mixing types 
```Ocaml
let car(x::y) = x;;
car: 'a list -> 'a = <fun>
Passing [] will give an error
```
****
**Currying**
```OCaml
let ccar x y = x::y;;
ccar: 'a -> 'a list -> 'a list = <fun>
let fun1 = ccar 'a'
fun1 ['b'; 'c'] produces ['a';'b';'c']
```
****
**Higher Order Functions**
```OCaml
let max i lt = function
| [] -> i
| h::t -> let m = max i lt t in if lt(h m) then m else h
let integer_max = max -9999999 (<)
```
****
**Difference between fun and function**
$\rightarrow$ fun is for currying and function is for pattern matching
```OCaml
fun x y -> x+y (fun x -> fun y -> x+y)
function | 0 -> -3 | x -> x+1
```
**Type**
```OCaml
type 'a option =
| None
| Some of 'a 
```
****
**Syntax**
Lexical analysis
$\rightarrow$ reads in a stream of characters, identifies the lexemes in the stream, and categorizes them into tokens.
$\rightarrow$ tokenizers are greedy, i.e., takes the longest token
****
**Grammar**
EBNF (Extended BNF) vs BNF (grammar rule)
- The idea of EBNF is to use shorthand for strict BNF
- BNF consists of LHS and RHS 
- LHS: nonterminal symbol | RHS: any sequence of terminals or nonterminals
-  specifying what's allowed in a language
- EBNF has to be convertible to BNF
Meta-notation
- ?: zero or one (something is optional)
- $*$: as many as you like
Regular language: one where grammar can be converted into a regular expression $\rightarrow$ easy to parse

 ISO standard for EBNF
 "terminal", 'terminal', [option], {repetition}, (grouping), N$*$X repetition 
 X-Y set difference, X,Y concatenation, X|Y disjunction, X=Y (lhs: nonterminal, rhs: rule)
 
 What can go wrong?
 - parser that calls itself: S $\rightarrow$ S (no progress)
 - Non-reachable symbols: S $\rightarrow$ aTb (T is not defined)
 - Left recursive grammar: 