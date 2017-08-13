## Basic Structure

_pattern_ { action }

BEGIN _pattern_ { action }
    { action }
END _pattern_ { action }

## Print Options

* `print` - The action to print
* `/t` - Tab
* Invoke `awk -F,` to comma-separate

## Regex

* `word ~ /(first_word|second_word)/` - Matches
* `word !~ /WORD/` - Doesn't match

## Scripting

* `'` nests
* `exit` - Early-exit the script

### `awk` Syntax

```awk
#!/bin/awk -f
BEGIN { print "File\tOwner" } 
    { print $8, "\t", $3}   
END { print " - DONE -" } 
```

### `bash` Syntax

```awk
    #!/bin/sh
    awk '{print $'$column'}'
```

### Variables

* `name="Kyle"` - Assignment
* `$0` is the whole line
* `$1`, `$4`, etc. - Gives you each column
* `$name` - Named variable
* Globals
    * You can use more than one character
    * `NF` - Number of fields
    * `NR` - Number of records, or the current record
    * `ORS` Record separator
    * `FS` - Column separator
    * `FILENAME` - Current filename
    * `ARGV[1]` - An array of arguments
    * `ENVIRON["name"]` - Array of variables

```awk
#!/bin/sh
column=${1:-1} # 1 is first variable passed in, -1 is default value
awk '{print $'$column'}'
```

### Conditionals

```awk
#!/bin/awk

if (conditional){
} else if {
} else {
}
```

### Loops

```awk
while ( conditional ) {
    next
}
for ( expression ; conditional ; expression ) {
    continue
}
for ( variable in array ) statement {
    break
}
```

### Functions

* `substr(string,position,length)`
* `split(string,array,separator)`
* `tolower(string)`
* `toupper(string)`
* `sub(/pattern/, replacement, string)`
* `match(string, pattern)`
    * `RSTART` - Index of start
    * `RLENGTH` - Length of match
* `system("unix_command")` - Returns exit code
* `function(parameter){}`

### No input processing

```awk
#!/bin/awk -f
# Doesn't process any text
BEGIN {
    print "File\tOwner"
    exit;
}
```

## Notes

* You can't interpolate variables in actions
