# maths-eval-language 

Usage example (Minimal Viable Product)
```
f(x) = x*2
y = 5
z = f(y)

print(z) # should print 10

y = 10
print(z) # should print 20
```

BNF syntax declaration:
```bnf
<syntax> ::= <row> | <row> <EOL> <syntax>
<row> ::= <logic> | <comment> | <logic> <comment>
<comment> ::= "#" <string>
<logic> ::= <function> | <decleration>
<function> ::= <symbol> "(" <function_arguments> ")"
<function_arguments> ::= <symbol> | <symbol> <function_arguments>
<decleration> ::= <signature> "=" <expression>
<signature> ::= <function> | <symbol>
<expression> ::= <signature> | "(" <expression> ")" | <expression> <operation> <expression>
<operation> ::= "*" | "-" | "/" | "^" | "+"

<EOL> ::= "\n"
<string> ::= <char> | <char> <string>
<char> ::= "a" | "b" | "c" | "d" | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n" | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x" | "y" | "z"
<symbol> ::= <string>
```

## Resources

BNF playground: https://bnfplayground.pauliankline.com/

Implementing a language (tutorial): http://lisperator.net/pltut/

## Javascript Library (first implementation goal)

```js
import { VM, evalExpression } from 'maths-eval';

console.log(evalExpression('10 * (6^(4/3)) - 8')); // 101.02723557

const maths = new VM({
  context: {
    someValue: 10,
  },
});

maths.run(`
  f(x) = x*(6^(4/3)) - 8
`);

const output = maths.run(`
  print(f(someValue))
`);

console.log(output); // [ 101.02723557 ]
```

## Rust compiler (seccond implementation goal)

TBD
