## Examples

```bash
sed '1,5/find-me/' input_file.txt
```

Can create a sed script with:

```bash
#!/bin/sed -f

s/find/replace/gp
```

You can edit something different than your match:

```bash
sed -n '/matched-text/s/old-text/new-text/g' input-file.txt

# On any line containing "matched-text", substitute "old-text" for "new-text"
```

## Expression Options

* `/g` - global
* `/p` - print affected lines
* `/I` - case insensitive

## CLI Flags

* `-f` - Reads script from file
* `-n` - Supress unaffected areas

## Special characters

* `'` - Hide shell variables
* `"` - Expand shell variables
* `()` - Execute a statement
* `:` - Set a label
* `&1` - First match

## Search types

`s/` - Substitute pattern
`d/` - Delete pattern
`y/` - Character replacement

Can contain ranges:

`1,5s` - Substitute within the first and fifth lines

## Commands

`/c` - Change line
`/d` - Delete line
`/i` - Add line above
`/a` - Add line below
