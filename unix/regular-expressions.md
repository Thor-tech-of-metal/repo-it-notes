# Examples

#### Remember



```
\d --> digits

\d{4} --> any 4 digits

^, $ -->  start-of-line and end-of-line respectively. E.g., ^[0-9]$ matches a numeric string.

. (dot) -->  ANY ONE character except newline. Same as [^\n]
\d, \D  --> ANY ONE digit/non-digit character. Digits are [0-9]
\w, \W  --> ANY ONE word/non-word character. For ASCII, word characters are [a-zA-Z0-9_]
\s, \S  --> ANY ONE space/non-space character. For ASCII, whitespace characters are [ \n\r\t\f]

\S.{1,} --> One or any number of space/non-space character

^.* --> Start of string followed by zero or more of any character (except line break)

.*$ --> Zero or more of any character (except line break) followed by end of string

[abc]	any of a, b, or c
[^abc]	not a, b, or c
[a-g]	character between a & g

^abc$	start / end of the string

```

#### Combinations of 1232-4562-7890-7890 or 1232456278907890

https://www.regextester.com/94189

1232456278907890 this match with (?:^[0-9]{16}$)

1232-4562-7890-7890 this math with (^\d{4}-\d{4}-\d{4}-\d{4}$)

Then we use OR |

```
(?:^[0-9]{16}$|^\d{4}-\d{4}-\d{4}-\d{4}$)
```

#### Combinations of ${tobsssss.tobssss} or ${tobdddddd.tdddddob}:[rdd]

${tobdddddd.tdddddob} -->. ^\${\S.{1,}.\S.{1,}\}$
OR |
${tobdddddd.tdddddob}:[rdd] --> ^\${\S.{1,}.\S.{1,}\}:\[\S{1,}\]$

```
^\${\S.{1,}.\S.{1,}\}$|^\${\S.{1,}.\S.{1,}\}:\[\S{1,}\]$
```
