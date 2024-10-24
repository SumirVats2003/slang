# SLang

A C-like language compiler developed using flex and bison by me.
The following is the description of the language.

## Part 1 : Lexical Analysis

| **lexeme**           | **token**   |
| -------------------- | ----------- |
| int                  | int         |
| float                | float       |
| double               | double      |
| char                 | char        |
| void                 | void        |
| return               | return      |
| if                   | if          |
| else                 | else        |
| while                | while       |
| for                  | for         |
| (a-zA-Z)(a-zA-Z0-9)* | id          |
| (0-9)+               | number      |
| ;                    | ;           |
| (                    | (           |
| )                    | )           |
| {                    | {           |
| }                    | }           |
| [                    | [           |
| ]                    | ]           |
| ,                    | ,           |
| &&                   | &&          |
| \|\|                 | \|\|        |
| !                    | !           |
| =                    | =           |
| ==                   | comparision |
| !=                   | comparision |
| <                    | comparision |
| <=                   | comparision |
| >                    | comparision |
| >=                   | comparision |
| // ...               | comment     |
| /\* ... \*/          | comment     |

## Part 2 : Syntax Analysis

Production Rules for the Context Free Grammar which represents the language.

```
S : S ';'
  | S ';' S ';'
  | if (B) { S }
  | if (B) { S } else { S }
  | for(S; B; S) { S }
  | while (B) { S }
  | id = E ';'
  ;

B : E comparision E
  | B && B
  | B || B
  | !B
  ;

E : E + E
  | E * E
  | E / E
  | - E
  | (E)
  | id
  ;
```

