# Scanner

A lexical scanner for the Jay language, written in Java. It reads a source file and breaks it into tokens.

## Files

| File | What it does |
|---|---|
| `TokenStream.java` | The scanner. `nextToken()` returns the next token. |
| `Token.java` | Holds a token's type and value. |
| `ScannerDemo.java` | Runs the scanner and prints every token. |
| `prog1.jay` | Test input. |

## How to run

```bash
javac *.java
java ScannerDemo
```

To scan a different file, change `file1` in `ScannerDemo.java`.

## Token types

| Type | Examples |
|---|---|
| `Keyword` | `boolean` `else` `if` `int` `main` `void` `while` |
| `Identifier` | `a`, `counter`, `X3` |
| `Literal` | `0`, `44444`, `true`, `false` |
| `Separator` | `(` `)` `{` `}` `;` `,` |
| `Operator` | `+` `-` `*` `/` `=` `<` `>` `!` `<=` `>=` `==` `!=` `&&` `\|\|` |
| `Other` | Anything invalid, like `@`, `:`, or `3aaa2` |

## Rules

- Whitespace and `//` comments are skipped.
- Keywords are case sensitive. `while` is a keyword, `While` is an identifier.
- Two-character operators like `<=` and `!=` are read as one token.
- A single `&` or `|` is invalid. Only `&&` and `||` count.
- A number followed by a letter, like `3aaa2`, is invalid.

## Sample output

Input:

```
int i;
i = 7;
```

Output:

```
Token 1 - Type: Keyword - Value: int
Token 2 - Type: Identifier - Value: i
Token 3 - Type: Separator - Value: ;
Token 4 - Type: Identifier - Value: i
Token 5 - Type: Operator - Value: =
Token 6 - Type: Literal - Value: 7
Token 7 - Type: Separator - Value: ;
```