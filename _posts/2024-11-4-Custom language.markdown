---
layout: post
title: "Custom Language"
---

Long time no see...

For a the past couple of weeks I have been programming a interpreter/compiler for a general purpose language.
I read a couple of hundred of pages of [dragon book](https://en.wikipedia.org/wiki/Compilers:_Principles,_Techniques,_and_Tools), but this book is way harder than I initially thought. I moved to [crafting interpreters](https://craftinginterpreters.com/) and GOD! this book is great! Easy to get started and it doesn't get a rocker science to understand what's going on.

I'd chosen a python as a desire language to write a interpreter in, probably because of [Tscoding](https://www.youtube.com/watch?v=8QP2fDBIxjM). Right now code is available on my github [repo](https://github.com/alexanderKus/Lang-custom-language).

Quick look at grammar
```
program      -> declaration* OEF ;
declaration  -> classDecl
                | funDecl
                | varDecl
                | statement ;
classDecl    -> "class" IDENTIFIER ( "<" IDENTIFIER )? "{" function* "}"
funDecl      -> "fun" function ;
function     -> IDENTIFIER functionBody;
functionBody -> "(" parameters? ")" block ;
parameters   -> IDENTIFIER ( "," IDENTIFIER )* ;
varDecl      -> "var" IDENTIFIER ( "=" expression )? ";" ;
statement    -> exprStmt
                | forStmt
                | ifStmt
                | printStmt
                | returnStmt
                | whileStmt
                | break
                | block ;
forStmt      -> "for" "(" ( varDecl | exprStmt| ";" )
                  expression? ";"
                  expression? ")" statement ;
exprStmt     -> expression ";" ;
ifStmt       -> "if" "(" expression ")" statement ( "else" statement )? ;
printStmt    -> "print" expression ";" ;
returnStmt   -> "return" expression? ";" ;
whileStmt    -> "while" "(" expression ")" statement ;
block        -> "{" declaration* "}" ;
expression   -> assignment ;
assignment   -> ( call "." )? IDENTIFIER "=" assignment
                | logic_or ;
logic_or     -> logic_and ( "or" logic_and )* ;
logic and    -> equality ( "and" equality )* ;
equality     -> comparison ( ( "!=" | "==" ) comparison )* ;
comparison   -> term ( ( ">" | ">=" | ">" | ">=" ) term )* ;
term         -> factor ( ( "-" | "+" ) factor )* ;
factor       -> unary ( ( "/" | "*" ) unary )* ;
unary        -> ( "!" | "-" ) unary
                | call ;
call         -> primary ( "(" arguments? ")" | "." IDENTIFIER)* ;
primary      -> NUMBER | STRING | IDENTIFIER | "true" | "false" | "nil" | "this
                | "(" expression ")" ;
                | "super" "." IDENTIFIER
                | functionBody;
arguments    -> expression ( "," expression )* ;
```

Here is a quick sample of what language is capable of.

```
class Base {
  foo() {
    print "foo";
  }
}

class Square < Base {
  init(n) {
    this.n = n;
  }
  calc() {
    return this.n * 2;
  }
}

class Rectangle < Base {
  init(a, b) {
    this.a = a;
    this.b = b;
  }
  calc() {
    return this.a * this.b;
  }

  foo() {
    print "boo";
  }
}

var s = Square(10);
var r = Rectangle(25, 2);
print "Square: " + s.calc();
print "Rectangle: " + r.calc();
s.foo();
r.foo();
```

and the result:
```
Square: 20
Rectangle: 50

"foo"
"boo"
```

Classes, inheritance, method overriding.. What does it sound to you? like OOP?
And all of that in **pure python without any dependencies** with 1709 lines of code.
Maybe even I would improve standard library to handle user input and file manipulation?
So many possibilities!

It's good to be back!
