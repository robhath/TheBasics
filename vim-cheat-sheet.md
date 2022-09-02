# Vim Cheat Sheet

Vim has modes-- 

* Command mode, in which keys allow you to move, mark, and modify the file, and some keys put you into...
* Insert/Replace mode, in which keys are entered as text, and the `ESC` key to returns you to Command mode.


## Command mode - cursor movement and file navigation

| key(s)   | where it goes                            |
| -------- | ---------------------------------------- |
| **h**    | left                                     |
| **j**    | down                                     |
| **k**    | up                                       |
| **l**    | right                                    |
|          |                                          |
| `ctrl-B` | back one page                            |
| `ctrl-F` | forward one page                         |
| **H**    | top of screen                            |
| **M**    | middle of screen                         |
| **L**    | bottom of screen                         |
|          |                                          |
| **w**    | start of next word                       |
| **W**    | start of next word (+punctuation)        |
| **b**    | start of previous word                   |
| **B**    | start of previous word (+punctuation)    |
| **e**    | end of word                              |
| **E**    | end of word (+punctuation)               |
|          |                                          |
| **^**    | first non-blank char on line             |
| **0**    | beginning of line                        |
| **$**    | end of line                              |
|          |                                          |
| **G**    | last line of the file                    |
| _n_**G** | line *n*                                 |
|          |                                          |
| **%**    | matching pair- (), {}, []                |
|          |                                          |
| _n{mov}_ | repeat movement *{mov} n* times          |
|          |                                          |
| **m**_c_ | mark current line using character _c_    |
| **'**_c_ | return to line marked with character _c_ |



## Insert/Replace mode

* These commands put you in insert/replace mode and allow you to enter text.
* `BACKSPACE`, `DELETE`, `HOME`, `END`, `PageUp`, `PageDown`, `Tab`, and arrow keys work (mostly) as expected in insert/replace mode. 
* When done entering text, press the `ESC` key to exit insert/replace mode.

| key(s)         | what it does                                 |
| -------------- | -------------------------------------------- |
| **i**          | insert at cursor                             |
| **I**          | insert at first non-blank character on line  |
| **a**          | append after cursor                          |
| **A**          | append at end of line                        |
| **o**          | open a line after and insert                 |
| **O**          | open a line before and insert                |
| **R**          | replace characters starting at cursor        |
|                |                                              |
| **s**          | substitute character at cursor (like 'xi')   |
| _n_**s**       | substitute *n* characters at cursor (*n*xi)  |
| **S**          | substitute entire line                       |
|                |                                              |
| **c**_n{mov}_  | change from cursor to '_{mov} n_ times'      |
| **c$**         | change from cursor to end of line            |
| **cw**         | change from cursor to end of word            |
| **cc**         | change entire line                           |
| **ct**_c_      | change from cursor to before character _c_   |


## Command mode - find, replace, copy, paste, etc.

* These commands do not put you in insert/replace mode.

| key(s)               | what it does                                    |
| -------------------- | ----------------------------------------------- |
| **r**_c_             | replace character at cursor with character _c_  |
| _n_**r**_c_          | replace _n_ chars at cursor with character _c_  |
| **x**                | delete character at cursor                      |
| _n_**x**             | delete _n_ characters at cursor                 |
|                      |                                                 |
| **d**_n{mov}_        | delete from cursor to '_{mov} n_ times'         |
| **d$**               | delete to end of line                           |
| **dw**               | delete word                                     |
| **dd**               | delete current line                             |
| **dt**_c_            | delete from cursor to before character _c_      |
|                      |                                                 |
| **y**_n{mov}_        | yank (copy) from cursor to '_{mov} n_ times'    |
| **y$**               | yank (copy) to end of line                      |
| **yw**               | yank (copy) current word                        |
| **yy**               | yank (copy) current line                        |
| **y'**_c_            | yank (copy) to line marked with character _c_   |
| **yt**_c_            | yank (copy) from cursor to before character _c_ |
|                      |                                                 |
| **p**                | paste copied/deleted text                       |
| **xp**               | swap character at cursor with next              |
| **ddp**              | swap line at cursor with next line              |
|                      |                                                 |
| **.**                | do it again                                     |
| **u**                | undo last change                                |
| `Ctrl-R`             | redo last undone                                |
|                      |                                                 |
| **\/**_{xxx}_`ENTER` | find next instance of characters '{xxx}'        |
| **?**_{xxx}_`ENTER`  | find previous instance of characters '{xxx}'    |
| **n**                | next (go to next match)                         |
| **N**                | previous (go to previous match)                 |
|                      |                                                 |
| **J**                | join next line to current line                  |



## Command mode - 'last line' commands for file handling, etc.

* Press the `:` (colon) key to enter 'last line' commands.
* When done entering the command, press the `ENTER` key to run the command.

| key(s)                        | what it does                                        |
| ----------------------------- | --------------------------------------------------- |
| **:w**                        | write current file                                  |
| **:w** _{fname}_              | write contents to file '_{fname}_'                  |
|                               |                                                     |
| **:q**                        | quit (exit) vim                                     |
| **:q!**                       | quit (exit) vim without saving current file         |
|                               |                                                     |
| **:e** _{fname}_              | edit file '_{fname}_'                               |
| **:e!** _{fname}_             | edit file '_{fname}_' without saving current file   |
| **:e #**                      | edit previous file                                  |
|                               |                                                     |
| **:r** _{fname}_              | read file '_{fname}_' and insert after current line |
|                               |                                                     |
| **:n**                        | edit next file specified (e.g. 'vim *.txt')         |
| **:n!**                       | edit next file specified without saving             |
|                               |                                                     |
| **:cn**                       | go to next error (if error file given at startup)   |
|                               |                                                     |
| **:%s/**_{f}_**/**_{r}_**/g** | find {f} and replace it with {r} globally           |
| **:%s/foo/bar/g**             | e.g. replace every 'foo' with 'bar'                 |
|                               |                                                     |
| `ctrl-G`                      | show current file name, size, position              |


Mastery comes from combining movement with change in the fewest keystrokes possible.
