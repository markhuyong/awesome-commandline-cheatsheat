
# Vim

## How to Exit

| Command           | Action                                                                                                       |
| --------------- | ----------------------------------------------- |
| `:q[uit]`       | Quit VimThis fails when changes have been made. |
| `:q[uit]!`      | Quit without writing                            |
| `:qa`           | Quit all buffers / tabs                         |
| `:cq[uit]`      | Quit always, without writing                    |
| `:wq`           | Write the current file and exit                 |
| `:wqa`          | Quit and write all buffers / tabs               |
| `:wq!`          | Write the current file and exit always          |
| `:wq {file}`    | Write to {file}. Exit if not editing the last   |
| `:wq! {file}`   | Write to {file} and exit always                 |
| `:[range]wq[!]` | Write the lines in [range] and exit always      |
| `ZZ`            | Write current file, if modified, and exit       |
| `ZQ`            | Quit current file and exitSame as `:q!`.        |

## Editing a File

| Command           | Action                                                                                                       |
| ----------------- | ------------------------------------------------------------ |
| `:e[dit]`         | Edit the current fileThis is useful to re-edit the current file, when it has been changed outside of Vim. |
| `:e[dit]!`        | Edit the current file alwaysDiscard any changes to the current buffer. This is useful if you want to start all over again. |
| `:e[dit] {file}`  | Edit {file}                                                  |
| `:e[dit]! {file}` | Edit {file} alwaysDiscard any changes to the current buffer. |
| `gf`              | Edit the file whose name is under or after the cursorMnemonic: `goto file`. |

## Inserting Text

| Command           | Action                                                                                                       |
| ---- | ------------------------------------------------------------ |
| `a`  | Append text after the cursor [count] times                   |
| `A`  | Append text at the end of the line [count] times             |
| `i`  | Insert text before the cursor [count] times                  |
| `I`  | Insert text before the first non-blank in the line [count] times |
| `gI` | Insert text in column 1 [count] times                        |
| `o`  | Begin a new line below the cursor and insert text, repeat [count] times |
| `O`  | Begin a new line above the cursor and insert text, repeat [count] times |

## Inserting a File

| Command           | Action                                                                                                       |
| ---------------- | ------------------------------------------------------------ |
| `:r[ead] [name]` | Insert the file [name] below the cursor                      |
| `:r[ead] !{cmd}` | Execute {cmd} and insert its standard output below the cursor |

## Deleting Text

| Command           | Action                                                                                                       |
| ------------------------------ | ------------------------------------------------------------ |
| `<Del>`/`x`                     | Delete [count] characters under and after the cursor         |
| `X`                            | Delete [count] characters before the cursor                  |
| `d{motion}`                    | Delete text that {motion} moves over                         |
| `dd`                           | Delete [count] lines                                         |
| `D`                            | Delete the characters under the cursor until the end of the line |
| `{Visual}x`/`{Visual}d`         | Delete the highlighted textFor {Visual} see Selecting Text.  |
| `{Visual}CTRL-H`/`{Visual}<BS>` | Delete the highlighted text when in Select mode              |
| `{Visual}X`/`{Visual}D`         | Delete the highlighted lines                                 |
| `:[range]d[elete]`             | Delete [range] linesDefault: current line.                   |
| `:[range]d[elete] {count}`     | Delete {count} lines, starting with [range]                  |

## Changing / Replacing Text

| Command           | Action                                                                                                       |
| -------------------------- | ------------------------------------------------------------ |
| `r{char}`                  | Replace the character under the cursor with {char}           |
| `R`                        | Enter Insert mode, replacing characters rather than inserting |
| `~`                        | Switch case of the character under the cursor and move the cursor to the rightIf a [count] is given, do that many characters. |
| `g~{motion}`               | Switch case of {motion} text                                 |
| `{Visual}~`                | Switch case of highlighted text                              |
| `{Visual}U`                | Uppercase highlighted text                                   |
| `SHIFT+I<comment-char>ESC` | Comment vertical selectionSelect range in column where comment char should appear with `CTRL+V`. |
| `x`                        | Uncomment vertical selectionSelect range in column where comment char should be removed with `CTRL+V`. |

## Changing Case in Vim

| Command           | Action                                                                                                       |
| -------------------------- | ------------------------------------------------------------ |
|`~`    | Changes the case of current character|
|`guu`  | Change current line from upper to lower.|
|`gUU`  | Change current LINE from lower to upper.|
|`guw`  | Change to end of current WORD from upper to lower.|
|`guaw` | Change all of current WORD to lower.|
|`gUw`  | Change to end of current WORD from lower to upper.|
|`gUaw` | Change all of current WORD to upper.|
|`g~~`  | Invert case to entire line|

## Information

| Command           | Action                                                                                                       |
| ---- | ---------------------------------------------- |
| `%`  | Jump to matching brace                         |
| `*`  | Highlight all occurrences of word under cursor |
| `ga` | Show ASCII value of char under cursor          |

## Ranges

## Substituting

For each line in [range] replace a match of {pattern} with {string}
`:[range]s[ubstitute]/{pattern}/{string}/[c][e][g][p][r][i][I] [count]`

Repeat last :substitute with same search pattern and substitute string, but without the same flags
`:[range]s[ubstitute] [c][e][g][r][i][I] [count] :[range]&[c][e][g][r][i][I] [count]`
You may add extra flags.

The arguments that you can use for the substitute commands:
* `[c]` Confirm each substitution. Vim positions the cursor on the matching string. You can type:
  - `y` to substitute this match
  - `n` to skip this match
  - `<Esc>` to skip this match
  - `a` to substitute this and all remaining matches {not in Vi}
  - `q` to quit substituting {not in Vi}
  - `CTRL-E` to scroll the screen up {not in Vi}
  - `CTRL-Y` to scroll the screen down {not in Vi}`
* `[e]` When the search pattern fails, do not issue an error message and, in particular, continue in maps as if no error occurred
* `[g]` Replace all occurrences in the line. Without this argument, replacement occurs only for the first occurrence in each line
* `[i]` Ignore case for the pattern
* `[I]` Don't ignore case for the pattern
* `[p]` Print the line containing the last substitute

## Copying and Moving Text

| Command           | Action                                                                                                       |
| -------------------------------------- | ------------------------------------------------------------ |
| `"{a-zA-Z0-9.%#:-"}`                   | Use register {a-zA-Z0-9.%#:-"} for next delete, yank or putUse uppercase character to append with delete and yank. {.%#:} only work with put. |
| `:reg[isters]`/`:di[splay]`             | Display the contents of all numbered and named registers     |
| `:reg[isters] {arg}`/`:di[splay] [arg]` | Display the contents of the numbered and named registers that are mentioned in {arg} |
| `["x]y{motion}`                        | Yank {motion} text [into register x]                         |
| `["x]yy`/`["x]Y`                         | Yank [count] lines [into register x]                         |
| `{Visual}["x]y`                        | Yank the highlighted text [into register x]For {Visual} see Selecting Text. |
| `{Visual}["x]Y`                        | Yank the highlighted lines [into register x]                 |
| `:[range]y[ank] [x]`                   | Yank [range] lines [into register x]                         |
| `:[range]y[ank] [x] {count}`           | Yank {count} lines, starting with last line number in [range], [into register x]Default: current line. |
| `["x]p`                                | Put the text [from register x] after the cursor [count] times |
| `["x]P`                                | Put the text [from register x] before the cursor [count] times |
| `["x]gp`                               | Just like `p`, but leave the cursor just after the new text  |
| `["x]gP`                               | Just like `P`, but leave the cursor just after the new text  |
| `:[line]pu[t] [x]`                     | Put the text [from register x] after [line]Default: current line. |
| `:[line]pu[t]! [x]`                    | Put the text [from register x] before [line]Default: current line. |

## Undo, Redo and Repeat

| Command           | Action                                                                                                       |
| --------- | ------------------------------------------------------------ |
| `u`       | Undo [count] changes                                         |
| `:u[ndo]` | Undo one change                                              |
| `CTRL-R`  | Redo [count] changes which were undone                       |
| `:red[o]` | Redo one change which was undone                             |
| `U`       | Undo all latest changes on one line. {Vi: while not moved off of it} |
| `.`       | Repeat last change, with count replaced with [count]         |

## Moving Around

| Command           | Action                                                                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Basic motion commands|`k <up> h <left> l <right> j <down>` |                                                              |
| `h`/`<Left>`                                                  | [count] characters to the left (exclusive)                   |
| `l`/`<Right>``<Space>`                                        | [count] characters to the right (exclusive)                  |
| `k`/`<Up>``CTRL-P`                                            | [count] lines upward                                         |
| `j`/`<Down>``CTRL-J``<NL>``CTRL-N`                            | [count] lines downward (linewise)                            |
| `0`/`<Home>`                                                  | To the first character of the line (exclusive)               |
| `^`                                                          | To the first non-blank character of the line                 |
| `$`/`<End>`                                                   | To the end of the line and [count - 1] lines downward        |
| `g0`/`g<Home>`                                                | To the first character of the screen line (exclusive) when lines wrap ('wrap on). Differs from `0` when a line is wider than the screenTo the leftmost character of the current line that is on the screen when lines don't wrap ('wrap' off). Differs from `0` when the first character of the line is not on the screen |
| `g^`                                                         | To the first non-blank character of the screen line (exclusive) when lines wrap ('wrap' on). Differs from `^` when a line is wider than the screen. To the leftmost non-blank character of the current line that is on the screen when lines don't wrap ('wrap' off). Differs from `^` when the first non-blank character of the line is not on the screen |
| `g$`/`g<End>`                                                 | To the last character of the screen line and [count - 1] screen lines downward (inclusive) when lines wrap ('wrap' on). Differs from `$` when a line is wider than the screen. To the rightmost character of the current line that is visible on the screen when lines don't wrap ('wrap' off). Differs from `$` when the last character of the line is not on the screen or when a count is used |
| `f{char}`                                                    | To [count]'th occurrence of {char} to the right. The cursor is placed on {char} (inclusive) |
| `F{char}`                                                    | To the [count]'th occurrence of {char} to the left. The cursor is placed on {char} (inclusive) |
| `t{char}`                                                    | Till before [count]'th occurrence of {char} to the right. The cursor is placed on the character left of {char} (inclusive) |
| `T{char}`                                                    | Till after [count]'th occurrence of {char} to the left. The cursor is placed on the character right of {char} (inclusive) |
| `;`                                                          | Repeat latest f, t, F or T [count] times                     |
| `,`                                                          | Repeat latest f, t, F or T in opposite direction [count] times |
| `- <minus>`                                                  | [count] lines upward, on the first non-blank character (linewise) |
| `+``CTRL-M`/`<CR>`                                            | [count] lines downward, on the first non-blank character (linewise) |
| `_ <underscore>`                                             | [count] - 1 lines downward, on the first non-blank character (linewise) |
| `<C-End>``G`                                                 | Goto line [count] on the first non-blank characterDefault: last line. |
| `<C-Home>``gg`                                               | Goto line [count] on the first non-blank characterDefault: first line. |
| `<S-Right>``w`                                               | [count] words forward                                        |
| `<C-Right>``W`                                               | [count] WORDS forward                                        |
| `e`                                                          | Forward to the end of word [count]                           |
| `E`                                                          | Forward to the end of WORD [count]                           |
| `<S-Left>``b`                                                | [count] words backward                                       |
| `<C-Left>``B`                                                | [count] WORDS backward                                       |
| `ge`                                                         | Backward to the end of word [count]                          |
| `gE`                                                         | Backward to the end of WORD [count]                          |
| The following commands move over words or WORDS.A word consists of a sequence of letters, digits and underscores, or a sequence of other non-blank characters, separated with white space (spaces, tabs, <EOL>). This can be changed with the 'iskeyword' option.A WORD consists of a sequence of non-blank characters, separated with white space. An empty line is also considered to be a word and a WORD. |                                                              |
| `(`                                                          | [count] sentences backward                                   |
| `)`                                                          | [count] sentences forward                                    |
| `{`                                                          | [count] paragraphs backward                                  |
| `}`                                                          | [count] paragraphs forward                                   |
| `]]`                                                         | [count] sections forward or to the next '{' in the first columnWhen used after an operator, then the '}' in the first column. |
| `][`                                                         | [count] sections forward or to the next '}' in the first column |
| `[[`                                                         | [count] sections backward or to the previous '{' in the first column |
| `[]`                                                         | [count] sections backward or to the previous '}' in the first column |

## Marks

| Command           | Action                                                                                                       |
| -------------------------------------------- | ------------------------------------------------------------ |
| `m{a-zA-Z}`                                  | Set mark {a-zA-Z} at cursor positionDoes not move the cursor, this is not a motion command. |
| `m'`/ m\\\`                                    | Set the previous context markThis can be jumped to with the `''` or ```` command. Does not move the cursor, this is not a motion command. |
| `:[range]ma[rk] {a-zA-Z}`/`:[range]k{a-zA-Z}` | Set mark {a-zA-Z} at last line number in [range], column 0Default is cursor line. |
| `'{a-z}`                                     | To the first non-blank character on the line with mark {a-z} (linewise) |
| `'{A-Z0-9}`                                  | To the first non-blank character on the line with mark {A-Z0-9} in the correct file |
| ``{a-z}`                                     | To the mark {a-z}                                            |
| ``{A-Z0-9}`                                  | To the mark {A-Z0-9} in the correct file                     |
| `:marks`                                     | List all the current marks (not a motion command)            |
| `:marks {arg}`                               | List the marks that are mentioned in {arg} (not a motion command). For example: |

## Searching

| Command           | Action                                                                                                       |
| -------------------------------- | ------------------------------------------------------------ |
| `/{pattern}[/]<CR>`              | Search forward for the [count]'th occurrence of {pattern}    |
| `/{pattern}/{offset}<CR>`        | Search forward for the [count]'th occurrence of {pattern} and go {offset} lines up or down |
| `/<CR>`                          | Search forward for the [count]'th latest used pattern        |
| `//{offset}<CR>`                 | Search forward for the [count]'th latest used pattern with newIf {offset} is empty no offset is used. |
| `?{pattern}[?]<CR>`              | Search backward for the [count]'th previous occurrence of {pattern} |
| `?{pattern}?{offset}<CR>`        | Search backward for the [count]'th previous occurrence of {pattern} and go {offset} lines up or down |
| `?<CR>`                          | Search backward for the [count]'th latest used pattern       |
| `??{offset}<CR>`                 | Search backward for the [count]'th latest used pattern with new {offset}If {offset} is empty no offset is used. |
| `n`                              | Repeat the latest `/` or `?` [count] times                   |
| `N`                              | Repeat the latest `/` or `?` [count] times in opposite direction |
| `:lv {pattern} [g][j] {file(s)}` | Search in files with internal grepResults are put into "quickfix list" open with `:cw`'g' return all matches not just one per line 'j' don't jump to first match automaticallyfor recursive search use `**` file pattern like `**/*.c` |

## Selecting Text (Visual Mode)

| Command           | Action                                                                                                       |
| ------------------------------------------------------------ | ----------------------------------------------------------- |
| To select text, enter visual mode with one of the commands below, and use motion commands to highlight the text you are interested in. Then, use some command on the text.The operators that can be used are:`~` switch case`d` delete`c` change`y` yank`>` shift right`<` shift left`!` filter through external command`=` filter through 'equalprg' option command`gq` format lines to 'textwidth' length |                                                             |
| `v`                                                          | Start Visual mode per character                             |
| `V`                                                          | Start Visual mode linewise (horizontal selection)           |
| `CTRL-V`                                                     | Start Visual mode columnwise (vertical selection)           |
| `<Esc>`                                                      | Exit Visual mode without making any changes                 |
| `viw`                                                        | Visually select inner word (where the cursor is positioned) |

## How to Suspend

| Command           | Action                                                                                                       |
| --------------------------- | ------------------------------------------------------------ |
| `CTRL-Z`                    | Suspend VimLike `:stop`. Works in Normal and in Visual mode. In Insert and Command-line mode, the CTRL-Z is inserted as a normal character. |
| `:sus[pend][!]``:st[op][!]` | Suspend Vim!If the '!' is not given and 'autowrite' is set, every buffer with changes and a file name is written out. If the '!' is given or 'autowrite' is not set, changed buffers are not written, don't forget to bring Vim back to the foreground later! |

## Multiple Windows

| Command           | Action                                                                                                       |
| ----------------- | ------------------------------------------------------------ |
| `:e filename`     | Edit another file                                            |
| `:split filename` | Split window and load another file                           |
| `CTRL-WV`         | Vertical split current window                                |
| `CTRL-WS`         | Horizontal split current window                              |
| `CTRL-W Arrow Up` | Move cursor up a window                                      |
| `CTRL-W CTRL-W`   | Move cursor to another window (cycle)                        |
| `CTRL-W_`         | Maximize current window                                      |
| `CTRL-W=`         | Make all equal size                                          |
| `10 CTRL-W+`      | Increase window size by 10 lines                             |
| `:vsplit file`    | Vertical split                                               |
| `:sview file`     | Same as split, but readonly                                  |
| `:hide`           | Close current window                                         |
| `:only`           | Keep only this window open                                   |
| `:ls`             | Show current buffers                                         |
| `:b 2`            | Open buffer #2 in this window                                |
| `:bd[n]`          | Close current bufferIf `[n]` is given close buffer `#n`. `#n` can be gathered with `:ls`. |

## Browsing with Tags

When editing programs, there is often a need to jump to another location. Vim uses a tags file that lists each word and location. The tags file has to be created by a utility able to handle the syntax of your files, and has to be updated after significant editing has occurred.
| Command           | Action                                                                                                       |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `CTRL-]`/`LMB-on-tag+CTRL`/`g LMB-on-tag`                      | Jump to tagPostion the cursor over a tag name, visually select text, use the left-mouse-button (LMB). Pushes current location to tag stack for later return. |
| `CTRL+t`                                                     | Return after jumpPops location to jump to from tag stack.    |
| `:tags`                                                      | Show tag stackList of return locations, used by `CTRL+t`.    |

## Internal Lists

Vim has one global quickfix list. The list contains file positions filled by other commands.Vim has one location list per window. The list is similar to a quickfix list and contains a list of positions in filesi.
| Command           | Action                                                                                                       |
| ------------------------------------------------------------ | -------------------------------------- |
| `:cw`                                                        | Open "quickfix list" (one global list) |
| `:ccl`                                                       | Close "quickfix list"                  |
| `:lw`                                                        | Open "location list" (one per window)  |

## Notes

- Based on the cheat sheet from [fprintf](http://www.fprintf.net/vimCheatSheet.html).
- Converted by [Arief Bayu Purwanto](https://github.com/ariefbayu).
