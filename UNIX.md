## File Commands

* `mkdir` - Make a directory (`-p` for nested/file/structure)
* `touch` - Create a file
* `cp` - Copy (`-r` for recursive, `-i` to prompt for overwrites)
* `cmp` - Compare files
* `diff` - See difference between files. (`-i` for case-insentive, `-B` for ignore blanks, `-w` for ignore whitespace)
    * `<` - File 1
    * `>` - File 2
    * `d` - Delete
    * `a` - Add
    * `c` - Change
* `sdiff` - Advanced diff. (`-s` to ignore matches)
    * `nothing` - Identical
    * `<` - File 1
    * `>` - File 2
    * `|` - Different
* `dircmp` - Compare directories
* `ls` - List (`-a` to include hidden files, `-l` for long form, `-R` for recursive)
* `mv` - Move or rename (`-i` for interactive)
* `rmdir` - Remove directorys (can take multiple)
* find <directory> "<search string>"
    * `-print` (display results)
    * `-exec compress {} \;` (compress the file when you find it)
    * `-ok rm {} \;` (delete the file when you find it)
* `mtime -4` - (limit results to files modified in the last 4 days)
* `locate <filename>` - find system files
* `ln <first file> <second file>` - Hard link two files together. (`-s` for soft link, plus dirs)
    * Hard links are identical, soft links are dependent
* `file <file_name>` - Display file metadata
* `split -b 500M big_file.jpg` - Splits into 500MB chunks
    * Use cat to recombine
* `sort file_1 file_2 > destination_file` - Sort by first character of each line
    * `-t, +1` (comma delimited, sort on second field)
    * `-u` to eliminate duplicates
* `uniq <file_name>` - Removes duplicate lines
* `tr a-zA-Z A-Za-z < <file_name>` - Translate file
* `fmt <file_name> -w 60` - Format file to a 60 character line
* `wc = word count` - `-w` for words, `-l` for lines, `-c` for bytes). Can pipe from `ls`.

## Shell Commands

* `less` - Paging (scroll up and down with arrow keys)
* `more` - Paging (spacebar, b [if no pipes], q to quit)
* `|` - Pipe output to input
* `>` - Redirect output to something other than screen
* `>>` - Append to output
* `tee` - Sends output to multiple locations
    * <command> | tee <first_output> | <second_output>
* `chsh` - Change shell
* `tab` - Autocomplete, twice for options
    * up, down to search
* `ctrl + a` - Beginning of a line, ctrl + e = end of a line
* `stty`, `stty sane`, `reset` - Fix weird remote issues
* `exit` - Quit shell
* `alias` - Show a list of aliases
* `alias <new>=<old>` - Set a shortcut for the session only
* `;` - Separate commands on the same line
* `&&` - Same as `;`, but only runs if the first one succeeds
* `history <number>` - Show lines of history
* `env` - Print your environment variables
* `<variable_name>=<value>` - Sets a shell variable
* `export <variable_name>` - Makes a shell variable an environment variable
* `export <variable_name>=<value>` - Set an environment variable
* `echo $<variable_name>` - Show a variable

## Prompts

* `$PS1` - Regular prompt
* `$PS2` - Secondary prompt
* `%n` - Current user
* `%~` - Current directory with path
* `%c` - Current directory without path
* `%t` - Time
* `%w` - Date, no year
* `%W` - Date with year
* `\n` - Force new line
* `%m` - Hostname
* `%M` - Hostname with domain

## Search Commands

* `cat` - Display, can take multiple files, can redirect into another file
* `tac` - Reverse cat
* `head`/`tail -20` - File start or end of file. Can do multiple files.
* `tail -f` - "follow" updates
* `grep <needle regex> <haystack>` - search. (`-5` for context lines, `-c` for count, `-v` for all lines that don't match, `-i` for case-insensitive)
* `ctrl+r` - Reverse search through history

## `awk`/`sed`

* `sed 's/old/new/gim' <source_file> > <destination_file>` - Search & replace
    * Can save `sed`s as scripts
    * `g` = global, `i` = case-insensitive, `m` = multiline
* `awk -F, /search/{ <command> $1 } <file_name>` - Work with delimited files
    * `-F` sets delimiter, `$1` is the first field
    * Can save `awk`s as scripts

## Shells

* What shells do you have available? `cat /etc/shells`
* `sh` has no completion or aliasing
* `csh` allows you to script in C
* `bash`/`ksh`/`zsh` allows a blend of features and simple scripting
* Temporarily jump into a shell by executing it
* `zsh` autocompletion while cycle through options while tabbing

## Tips

* Multiple commands can be separated with ;
    * && is the same as ;, but only runs if the first one succeeds
* Find out what shell you’re using with echo $SHELL
* `*` is a general wildcard, `?` is a single-character wildcard
* History is in `~/.bash_history` - good for stubbing out scripts
* `^cd^ls` runs last command, swapping out `cd` for `ls`
* `nano` : `pico` :: `vim` : `vi`
* Find out what group you’re in with grep username /etc/passwd
* Find out general group info with `more /etc/group`
* A `t` at the end of a permissions list is a "sticky bit", and means it can only be modified by its owner
* You own any files that you `cp`
* Shell variables are tied to the shell, environment variables exist for any shell
* `zsh` config is in `/etc/zprofile`, `/etc/zshenv`, `/etc/zsh/zshrc`.
* User overrides are in `~/.zprofile`, `~/.zshrc`
* Edit the `PATH=` in `.zshrc` to add more default paths
* `alias <new>=<old>` - Set a shortcut. Goes in `.zshrc` file.
