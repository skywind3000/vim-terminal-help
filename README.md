# vim-terminal-help
vim/neovim builtin terminal helper


## Requirements

- vim: 8.1
- neovim: 0.3 and install [neovim-remote](https://github.com/mhinz/neovim-remote) package.

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

Inside the terminal:

```bash
drop abc.txt
```

tell vim to open `abc.txt`

## Settings

- `g:terminal_height`: new terminal height, default to 10.
- `g:terminal_pos`: where to open the terminal, default to `rightbelow`.
- `g:terminal_shell`: specify shell rather than default one.
- `g:terminal_edit`: how to open the file in vim, default to `tab drop`.
- `g:terminal_kill`: set to `term` to kill term session when exiting vim.
- `g:terminal_list`: set to 0 to hide terminal buffer in the buffer list.
