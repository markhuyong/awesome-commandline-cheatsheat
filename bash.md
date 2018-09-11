## Bash Shortcuts
### Command Editing Shortcuts

| Command           | Action                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------ |
| `CTRL+A` `CTRL+E` | Go to the start/end of the command line                                                                      |
| `CTRL+W` `ALT+D`  | Delete from cursor to start/end of word (whole word if at the boundary)                                      |
| `CTRL+Y`          | Paste word or text that was cut using one of the deletion shortcuts (such as the one above) after the cursor |
| `CTRL+XX`         | Move between start of command line and current cursor position (and back again)                              |
| `ALT+B` `ALT+F`   | Move backward/forward one word (or go to start of word the cursor is currently on)                           |
| `ALT+C`           | Capitalize to end of word starting at cursor (whole word if cursor is at the beginning of word)              |
| `ALT+U`           | Make uppercase from cursor to end of word                                                                    |
| `ALT+L`           | Make lowercase from cursor to end of word                                                                    |
| `ALT+T`           | Swap current word with previous                                                                              |
| `CTRL+F` `CTRL+B` | Move forward/backward one character                                                                          |
| `CTRL+D` `CTRL+H` | Delete character after/before under cursor                                                                   |
| `CTRL+T`          | Swap character under cursor with the previous one                                                            |

### Command Recall Shortcuts
| Command  | Action                                                                    |
| -------- | ------------------------------------------------------------------------- |
| `CTRL+R` | Search the history backwards                                              |
| `CTRL+G` | Escape from history searching mode                                        |
| `CTRL+P` | Previous command in history (i.e., walk back through the command history) |
| `CTRL+N` | Next command in history (i.e., walk forward through the command history)  |
| `ALT+.`  | Use the last word of the previous command                                 |

### Command Control Shortcuts
| Command  | Action                                                                 |
| -------- | ---------------------------------------------------------------------- |
| `CTRL+L` | Clear the screen                                                       |
| `CTRL+S` | Stops the output to the screen (for long running verbose command)      |
| `CTRL+Q` | Allow output to the screen (if previously stopped using command above) |
| `CTRL+C` | Terminate the command                                                  |
| `CTRL+Z` | Suspend/stop the command                                               |

### Bash Bang Shortcuts
| Command   | Action                                                                                                                                |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| `!!`      | Run last command                                                                                                                      |
| `!blah`   | Run the most recent command that starts with `blah`                                                                                   |
| `!blah:p` | Print out the command that `!blah` would run (also adds it as the latest command in the command history                               |
| `!$`      | The last word of the previous command (same as `ALT+.`)                                                                               |
| `!$:p`    | Print out the word that `!$` would substitute                                                                                         |
| `!*`      | The previous command except for the first word (e.g., if you type `find some_file.txt /`, then `!*` would give you `some_file.txt /`) |
| `!*:p`    | Print out what `!*` would substitute                                                                                                                                      |
