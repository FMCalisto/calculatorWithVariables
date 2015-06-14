# Calculator with Variables

This example implements a simple calculator. The calculator has an unspecified number of integer variables and the common binary integer operators (namely, addition, subtraction, multiplication, division, and modulus), and unary integer operators (+ and -).
The language will contain the following concepts (tokens): VAR (a variable: the corresponding s attribute will contain its name); INT (an integer: the corresponding i attribute contains its value); and the operators (see below).

## The Lexical Analyzer (Flex) Specification

The lexical analyzer (vars.l) is very simple and limited to recognizing variable names (token VAR), integers numbers (token INT), and the operators themselves.

## The Syntactic Analyzer (YACC) Specification

The syntactic analyzer will be built to immediately compute the expressions in a syntax-directed fashion as they occur. It is, thus, important to use trees that build nodes as the expressions occur (left-recursive grammars). If the grammar were right-recursive, the last node would be the first to be built and the (syntax-directed) evaluation would be from the last expression to the first.

### How to Compile?

The Flex specification is processed as follows (the file lex.yy.c is produced):

```
 flex vars.l
```
 
The YACC specification is processed as follows (files y.tab.h, needed by the Flex-generated code, and y.tab.c):

```
 yacc -dtv vars.y
```

Compiling the C/C++ code (it is C++ simply because we programmed the extra code in that language):

```
 g++ -c lex.yy.c
 g++ -c y.tab.c
 g++ -o vars y.tab.o lex.yy.o
```

### Acknowledgement

Thank you to Professor David Matos.

Main source:

https://www.l2f.inesc-id.pt/~david/w/pt/The_YACC_Parser_Generator/Example:_Calculator_with_Variables
