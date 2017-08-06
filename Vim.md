## Modes

* `i`, `a` - Insert mode
* `<esc>`, `<ctrl> + [` - Normal mode
* `Q` - Go to ex mode
* `visual` - To vim from ex mode`

## CLI Commands

* `vim <filename> <filename>` - Open multiple files
* `vim + <filename>` - Open file at last line
* `vim +<num> <filename>` - Open file at a specific line
* `vim +/<pattern> <filename>` - Open file at the first occurrence of pattern
* `vim -R <filename>` - Read-only
* `vim -r` - Show recovered files
* `vim -r <filename>` - Recover file

## Save/Quit

* `:w <new filename>` - Save (write)
* `:w! <new filename>` - Save with overwrite
* `:w %` - Save current file
* `:q` - Quit
* `:q!` - Force quit, no save
* `:wq` - Write and quit
* `:x` - Write and quit (doesn’t update modified time if not changed)
* `:e!` - Reset this file
* `:r` - Import contents of file
* `:pre` - Preserve buffer (if the file turns out to be read only, for example)
* `ZZ` - Save and quit

## Open

* `:n` - Next open file
* `:e <filename>` - Edit a file while keeping the current one open
    * `Ctrl + ^` - Switch between open files
    * `:e #` - Switch between open files

## Movement Commands

* `w` - forward one word
* `W` - Forward one word, skip punctuation
* `b` - Backward one word
* `B` - Backward one word, skip punctuation
* `0` - Beginning of line
* `$` - End of line
* `gg` - Beginning of file
* `G` - End of file
* `G<number>` - Go to line
* ```` - Go to your last edit
* `''` - Go to the beginning of the line your last edit was on
* `+` - First character of next line
* `-` - First character of previous line
* `^` - First non-blank character in a line
* `<num> |` - Move to a specific line’s column
* `(` - Beginning of sentence
* `)` - End of sentence (looks for . ? or ! followed by two spaces)
* `{` - Beginning of paragraph
* `}` - End of paragraph (looks for sentence followed by paragraph marker)
* `{{` - Beginning of section
* `}}` - End of section (looks for sentence followed by section marker)

## Markers

* `m <marker name>` - Set a named marker
* `' <marker name>` - Jump to beginning of marker’s name
* ``` <marker name>`` - Jump to marker

## Screen Commands

* `ctrl + f` - Page forward
* `ctrl + b` - Page backward
* `ctrl + d` - Half page forward
* `ctrl + u` - Half page backward
* `ctrl + y` - One line forward
* `ctrl + e` - One line backward
* `z <enter>` - Cursor to top and recenter
* `z .` - Recenter screen
* `z -` - Cursor to bottom and recenter
* `<num>z` - Center on a specific line
* `H` - "home", top line of screen
    * numeric prefix is lines away from top
* `M` - "middle", middle line on screen
* `L` - "last", last line on screen
    * numeric prefix is lines away from bottom
* `Ctrl + L` - Redraw the screen`

## Search

These can all be used with the other vim commands (eg, change, delete)

* `/<search>` - Regex search (n for next, N for previous)
* `?<search>` - Regex search backward (n for next, N for previous)
* `/<enter>` - Repeat search
* `?<enter>` - Repeat search backward
* `/~` - `~` is a glob for your last regex

## Find within a line

These can all be used with the other vim commands (eg, change, delete)

* `f <character>` - Find next character in the current line
* `F <character>` - Find previous character in the current line
* `t <character>` - Find the character before the next <character> in the current line
* `T <character>` - Find the character before the previous <character> in the current line
* `;` - Next, same direction
* `,` - Next, opposite direction

## Replace

* `%s/<search>/<replace>/<options>` - Regex search and replace
    * `g` - Global
    * `i` - Case insensitive
    * `c` - Confirm
* `:g/<pattern>/s/<old>/<new>/g` - Find lines that match, then run :s
* `ctrl + v` - Escape next character

## Insert Commands

`<num><insert command><character><normal mode>` - Insert repeating characters.

* `a` - Add text after cursor
* `A` - Add text at end of line
* `i` - Add text before cursor
* `I` - Add text at beginning of line
* `o` - Insert blank line after
* `O` - Insert blank line before

## Change Commands

* `c<num><type>` - Change some text. `w`/`W`, `e/E`, `b/B`, `0`, `$`, `G`, `gg`, <pattern>
    * Shortcuts: `cc` (whole line), `C` (to end of line)
* `r` - replace character
    * Can take a numeric prefix to change multiple characters
* `R` - Replace text, insert style
* `s` - (substitute) delete character, enter insert mode
    * Can take a numeric prefix to change the middle part of a word
* `S` - Delete line, enter insert mode

## Delete Commands

* `d<num><type>` - Delete some text. `w`/`W`, `e/E`, `b/B`, `0`, `$`, `G`, `gg`, <pattern>
    * Shortcuts: `dd` (whole line), `D` (to end of line)
* `"<buffer name><command>` - delete into named buffer
* `x` - Delete character under cursor
* `X` - Delete character behind cursor

## Copy/Paste Commands

* `y<num><type>` - Copy some text. `w`/`W`, `e`/`E`, `b`, `0`, `$`, `G`, `gg`
    * Shortcuts: yy/Y (copy current line)
* `"<buffer name><command>` - Yank into named buffer
* `p` - Paste
* `"<num>p` - Paste buffers 1-9
    * `.` increments the number
* `"<buffer name>p` - Paste named buffer
* Yank and delete share number buffers. Yank can also use named buffers.

## Edit

* `J` - Join current and next line
    * Accepts numeric argument
* `~` - Change case of letter

## Undo/Repeat

* `u` - Undo last change
* `U` - Undo all changes on this line
* `.` - Repeat last command

## CLI

* `:!<command>` - Execute a unix command
* `:sh` - Temporarily switch to a console
    * Ctrl+D to switch back

## Ex Commands

* Ex takes a line address, a command, and a return.
* `|` - Execute multiple ex commands
* `:<address>r !<some unix command>` - Insert result of a unix command
* Can use ex as STDIN to unix command, `:r access STDOUT`

### Line addresses

* A number (`10`)
* A range (`1,100`)
* A relative range (`1;+8`)
* `$` (last line)
* `%` (all lines)
* `.` (current line)
* Expression (eg `$-20`)
* `+`,`++`, `-`, `--`
* `/pattern/`

### Edit Commands

* `:<lines>co<destination>` - Copy (also could use “t”)
* `:<lines>m<destination>` - Move
* `:<lines>d` - Delete
* `:<lines>w <new filename>` - Save out part of a file
* `:<lines>w >><new filename>` - Append to a file
* `:<address>r` - Read a file in

## Set Options

* `:set option` to set, `:set nooption` to unset
* `:set all` - Show all current settings
* `:set` - Show all settings that have been explicitly set
* `:set option?` - Show a specific setting

### Useful options

* `wrapmargin=15`
* `ignorecase`
* `wrapscan` (during global searches)
* `magic` (recognize wildcard characters)
* `autoindent`
* `showmatch`
* `tabstop`
* `shiftwidth`
* `number`
* `list`
* `autowrite`

## Miscellaneous

* `<number><command><text>` is the same as `<command><number><text>`
* `Ctrl + G` - Show page stats at the bottom of the screen`
* The leader key is a prefix for custom hotkeys
