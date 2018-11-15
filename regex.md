## Character Classes

* `.` - Single character
* `<character>*` - 0 or more of the character before the * (greedy- matches full string, then backtracks)
* `<character>*?` - 0 or more of the character before the * (lazy- matches nothing, moves forward)
* `<character>*+` - 0 or more of the character before the * (possessive, matches full string, no backtrack)
* `<character>+` - 1 or more of the character before the +
* `<character>?` - 0 or 1 of the character before the ?
* `<character>{2}` - 2 of the character before the {2}
* `<character>{2,}` - 2 or more of the character before the {2,}
* `<character>{2,4}` - 2, 3, or 4 character before the {2,4}
* `^<character>` - Must be the beginning of the line
* `[^character]` - Not
* `(this|that)` - Or
* `$` - Must be the end of the line
* `\` - Escape
* `-` - Range (a-z, A-Z, 0-9)
* `[<characters>]` - Sets and options
    * A character set will match any individual item in it
* `\s` - Whitespace
* `\S` - Non-whitespace
* `\d` - Digit
* `\D` - Non-digit
* `\b` - Word boundary
* `\B` - Non-word boundary
* `\w` - Word character
* `\W` - Non-word character
* `\(<some term>\)` - Save a back reference
* `\1` - Back reference
* `q(?!u)` - Negative lookahead (q not followed by u)
* `q(?-u)` = positive lookahead (q followed by a u)

## POSIX Classes

* [:alpha:]
* [:alnum:]
* [:digit:]
* [:lower:]
* [:upper:]
* [:punct:]
* [:xdigit:]
* [:blank:]
* [:print:]
* [:graph:]
* [:space:]
* [:cntrl:]

## In JS

* Use the literal by default, use the constructor if you need to use variables
