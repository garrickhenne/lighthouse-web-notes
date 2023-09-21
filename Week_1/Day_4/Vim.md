# Vim

Vim operates on two modes
- Edit mode: the state in which the keys you type on are actually inserted in your document.
- Command mode: Allows you to navigate through the document, search and replace text, copy and paste, etc.  

By default when you open a file, you're placed in command mode.

## Moving Around

- `H` moves _left_
- `K` moves _up_
- `L` moves _right_
- `J` moves _down_

Or you can just use arrow keys.

## Edit a file

To switch to edit mode (also called "insert mode") you need to give VIM a command to tell it to switch modes. There are two ways to do this:

- Press `i` to begin inserting text at the current cursor position.
- Press `a` to begin inserting after the current cursor position.

Getting out of editing mode is a bit more intuitive: just hit the `ESC` key.

- `Y` copies a line of text to the buffer.
- `P` pastes it to the cursor's current position.
- `dd` will delete the whole line of text. This will also effectively "cut" a line of - text as well. When you delete a line, it's placed in the buffer.
- `yy` copies a whole line of text.

## Saving a file
- Make sure you are in command mode. Use escape key to make sure.
- type `:w`

## Quit vim

- `:wq` - write (save) and quit file (and vim)
- `:q!` - quit and ignore changes made since last file save.

### Cheatsheet 
![](vi-vim-cheat-sheet.gif)