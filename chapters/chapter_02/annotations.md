# Chapter 2: The Metacharacters

The original metacharacters are:

. ? * + ^ $ | [ ] { } ( ) \

| Metacharacter | Name         | 
| ------------- | ------------ | 
| .             | Point        | 
| []            | List         | 
| [^]           | Negated List |
| ?             | Optional     |
| *             | Asterisk     |
| +             | Plus         |
| {}            | Keys         |
| ^             | Circunflex   |
| $             | Dollar sign  |
| \b            | Border       |
| \             | Escape       |
| \|            | Or           |
| ()            | Group        |
| \1            | Backtrack    |

They are separeted in four distintic groups:

### Representants

| Metacharacter | Name         | Function                     |
| ------------- | ------------ | ---------------------------- |
|.              | Point        | Any character                |
| [...]         | List         | List of allowed characters   |
| [^...]        | Negated List | List of forbidden characters |

### Quantifiers

| Metacharacter | Name         | Function                     |
| ------------- | ------------ | ---------------------------- |
| ?             | Optional     | Zero or one                  |
| *             | Asterisk     | Zero, one or more            |
| +             | Plus         | One or more                  |
| {n,m}         | Keys         | From n to m                  |

### Anchors

| Metacharacter | Name         | Function                     |
| ------------- | ------------ | ---------------------------- |
| ^             | Circunflex   | Start of the line            |
| $             | Dollar sign  | End of the line              |
| \b            | Border       | Start or end of a word       |

### Others

| Metacharacter | Name         | Function                      |
| ------------- | ------------ | ----------------------------- |
| \c            | Escape       | Makes the character c literal |
| \|            | Or           | one or another                |
| (...)         | Group        | Delimits a group              |
| \1...\9       | Backtracking | Match text in the groups 1...9|

## Point

| Expression | Matches with              |
| ---------- | ------------------------- |
| n.o        | não, nao, ...             |
| .eyboard   | keyboard, Keyboard, ...   |
| e.tendido  | estendido, extendido, ... |
| 12.45      | 12:45, 12 45, 12.45, ...  |
| <.>        | \<B\>, \<i\>, \<p\>, ...  |

### Resume

* Point matches anything
* Point matches point
* Point is a wildcard to match a character

## List

| Expression   | Matches with              |
| ------------ | ------------------------- |
| n[ãa]o       | não, nao                  |
| [Kk]eyboard  | keyboard, Keyboard        |
| e[sx]tendido | estendido, extendido      |
| 12[:. ]45    | 12:45, 12.45, 12 45       |
| <[bip]>      | \<b\>, \<i\>, \<p\>       |
| [][-]        | [, ], -                   |
| [A-Za-z]     | A, a, B, b, ..., Z, z     |
| [0-9]        | 0, 1, 2, 3, ..., 7, 8, 9  |

### POSIX classes

| POSIX Class | Similar to  | Meaning                       |
| ----------- | ----------- | ----------------------------- |
| [:upper:]   | [A-Z]       | Capital letters               | 
| [:lower:]   | [a-z]       | Small letters                 | 
| [:alpha:]   | [A-Za-z]    | Capital letters/small letters |
| [:alnum:]   | [A-Za-z0-9] | Letters and numbers           |
| [:digit:]   | [0-9]       | Numbers                       |
| [:xdigit:]  | [0-9A-Fa-f] | Hexadecimal numbers           |
| [:punct:]   | [.,!?:...]  | Punctuation signs             |
| [:blank:]   | [ \\t]      | Space and Tab                 |
| [:space:]   | [ \\t\\n\\r\\f\\v] | Blank characters       |
| [:cntrl:]   |             | Control characters            |
| [:graph:]   | [^ \\t\\n\\r\\f\\v] | Printable characters  |
| [:print:]   | [^\\t\\n\\r\\f\\v]  | Printable and space   |

They must be used inside a list, they are not a list by themselves. So, to use [:upper:], you should write like this:

``` 
[[:upper:]]
```

<span style="color:red">Warning!</span> POSIX classes take in account the system location.

<span style="color:green">Suggestion!</span> For Portuguese, always prefer to use [:alpha:] instead of [A-Za-z].

### Resume

* The list matches who it knows and has its own rules;
* Inside the list, there are no metacharacters (everybody is normal);
* Inside the list, "-" means interval;
* A literal "-" must be the last item in the list;
* A literal "]" must be the first item in the list;
* The intervals follows the ASCII table (DO NOT USE A-z);
* POSIX classes includes accents, A-Z does not.
