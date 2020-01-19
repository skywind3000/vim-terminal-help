# Preface

I use vscode for markdown editing and vscode has a `CTRL+backtick` hot key to toggle internal terminal. I use it a lot and it's very handy. At the meantime both vim/nvim have internal terminal too, but most of us still prefer working in a tmux split rather than using the internal terminal.

Therefor, I started to wonder, is there something I can do, to make vim's internal terminal has a better experience ? As a result, here this plugin exists with three little changes:

Firstly, this plugin setup a keymap `ALT+=` (can be changed) to toggle terminal window, like vscode's `CTRL+backtick`. When you press `ALT+=` it will open a new terminal below your current window, and initiate the shell working directory to where the parent directory of current file. Most time you want to do something to the current file, so open the shell in the current file directory will make life easier.

When you finished, just press `ALT+=` again to hide the terminal, so you always press `ALT+=` to toggle your terminal window, but if you run `exit` and quit the previous terminal session and hit `ALT+=` again, a new terminal will be created.

In addition, you are able to use `ALT+SHIFT+h/j/k/l` to move around between windows. Most vim users uses `CTRL+h/j/k/l` to switch window, but these keys are very useful in the terminal applications, for example if you use `tnoremap` to override `CTRL+j` or `CTRL+k`, you will not be able to use them in fzf. So `CTRL+h/j/k/l` will not be used for `tnoremap`, `terminal-help` encourage you to use the new `ALT+SHIFT+h/j/k/l` to jump between windows.

Finally, it provides a `drop` command in the internal terminal to tell outside vim to open a file. When you are working in the internal terminal and you want to edit a file in the current directory (not vim's `pwd`), how do you do ? Especially the `pwd` in the terminal is different of vim's `pwd`. You have to switch to terminal normal mode and use vim `e` command with a long path name.

With `drop` command, it is simple to tell outside vim open a specific file precisely:

```bash
cd /xxx/some/where
drop abc.txt
```

I always believe that small changes can make big difference.

## Requirements

- vim: 8.1
- neovim: 0.3 and install [neovim-remote](https://github.com/mhinz/neovim-remote) package if you need drop command.

## Installation

```VimL
Plug 'skywind3000/vim-terminal-help'
```

## Usage

- `ALT` + `=`: toggle terminal below.
- `ALT` + `SHIFT` + `h`: move to the window on the left.
- `ALT` + `SHIFT` + `l`: move to the window on the right.
- `ALT` + `SHIFT` + `j`: move to the window below.
- `ALT` + `SHIFT` + `k`: move to the window above.
- `ALT` + `-`: paste register 0 to terminal

Inside the terminal:

```bash
drop abc.txt
```

tell vim to open `abc.txt`


## Settings

- `g:terminal_key`: which key will be used to toggle terminal window, default to `<m-=>`.
- `g:terminal_cwd`: initialize working dir: `0` for unchanged, `1` for file path and `2` for project root.
- `g:terminal_height`: new terminal height, default to 10.
- `g:terminal_pos`: where to open the terminal, default to `rightbelow`.
- `g:terminal_shell`: specify shell rather than default one.
- `g:terminal_edit`: how to open the file in vim, default to `tab drop`.
- `g:terminal_kill`: set to `term` to kill term session when exiting vim.
- `g:terminal_list`: set to 0 to hide terminal buffer in the buffer list.


## Remember

The internal terminal in both vim/neovim has `NORMAL` and `INSERT` mode. When you are in `INSERT` mode, you can enter shell commands. And if you want to scroll terminal screen or copy / paste texts to a normal vim buffer, you need to switch to `NORMAL` mode by `<c-\><c-n>` (like tmux's `<c-b>` + left square bracket).

If you want to re-enter `INSERT` mode, just press `i` or `a`, and you can input shell commands again.