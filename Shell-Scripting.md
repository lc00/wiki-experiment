## Scripting

* `#!/bin/bash` - Tell what shell to use to execute the script if flagged as executable.
    * If not executable, specify the shell to run it. bash <script_name>
    * Add flag with `chmod u+x <script_name>`
* Script must be in the `PATH` variable to work. `pwd ; echo $PATH`
* `#` - Comment
* `echo` - Print to screen (`-e` = allow formatting flags)
    * `\b` - Move cursor back one space
    * `\c` - No new line after print
    * `\f <number>` - Force a specific horizontal location on the next line
    * `\n` - Newline
    * `\t` - Tab
* Use `history <number> > <script_name>` to stub out a script.
* Time formats:
* `%d` = day, `%y` = 2-digit year, etc.
* $1-$9 are CLI arguments at runtime
* `read <variable_name>` will prompt a user for input.
    * Used in script with $varible_name
* `sh -x <script_name>` displays each line for debugging
* [[UNIX-Loops]] & [[UNIX-Conditionals]]
