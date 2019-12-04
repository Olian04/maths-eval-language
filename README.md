# maths-eval-language 

Usage example (Minimal Viable Product)
```
f(x) = x*2

y = 5
print(f(y)) # should print 10

y = 10
print(f(y)) # should print 20
```

EBNF syntax declaration:
```bnf
<syntax> ::= <row> (<EOL> <syntax>)?
<row> ::= (<logic>)? (<comment>)?
<comment> ::= " "? "#" (<string> " "?)*
<logic> ::= <function_call> | <decleration>

<decleration> ::= (<function_declaration> | <string>) "=" <expression>
<expression> ::= <signature> | "(" <expression> ")" | <expression> <operation> <expression>
<signature> ::= <function_call> | <symbol>
<function_call> ::= <string> "(" <symbol> ("," <symbol>)* ")"
<function_declaration> ::= <string> "(" <string> ("," <string>)* ")"
<symbol> ::= <number> | <string>

<EOL> ::= "\n"
<number> ::= " "? "-"? [1-9]+ | [1-9]+ "." [0-9]+ " "?
<string> ::= " "? ([a-z] | [A-Z])+ " "?
<operation> ::= "*" | "-" | "/" | "^" | "+"
```

## Resources

BNF playground: https://bnfplayground.pauliankline.com/

Implementing a language (tutorial): http://lisperator.net/pltut/

EBFN Parser for nodejs (if all else fails): https://www.npmjs.com/package/ebnf

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
