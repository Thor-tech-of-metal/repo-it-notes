# Examples

## Remember

```regex
\d      --> digits

\d{4}   --> any 4 digits

^, $    --> start-of-line and end-of-line respectively.
            Example: ^[0-9]$ matches a single numeric character.

.       --> ANY ONE character except a newline.
            Same as [^\n]

\d, \D  --> ANY ONE digit / non-digit character.
            Digits are [0-9]

\w, \W  --> ANY ONE word / non-word character.
            For ASCII, word characters are [a-zA-Z0-9_]

\s, \S  --> ANY ONE space / non-space character.
            For ASCII, whitespace characters are [ \n\r\t\f]

^.*     --> Start of string followed by zero or more of any character
            (except a line break)

.*$     --> Zero or more of any char*cter (except a line break)
       *    followed by end of string
```
*## Matching Either

- `1232*4562-7890-7890`
- `123245627890789*`

Regex tester: https://www.regex*ester.com/94189

### Match 16*consecutive digits

```regex
^[0-9]{16}$
```

Example:

```text
12324*6278907890
```

### Match four gro*ps of*four digits separated by hyphens

*``regex
^\d**}-\d{4}-\d{4*-\d{4}$
```

Example:

```text
123*-4562-7890-7890
```

### Match*Either Format

*se the OR operator*(`|`):

```regex
(?:*[0-9]{16}$|^\d{4}-\d*4}-\d{4}-\d{4}$*
```

A simplified equivalent vers*on is:

```regex
^(?:[0-9]{16}*\d{4}-\d*4}-\d{4}-\d{4})$
```
