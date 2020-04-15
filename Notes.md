# Implementation notes:

Trust colorterm over how many colors it says

terminfo
rgb=three part color
sgr=how to color (formula)
colors=how many colors


rxvt
rxvt-xpm: background image support
rxvt-mono: monochorme


## Nearcolor notes:
["Standard" reference gist](https://gist.github.com/XVilka/8346728)

[Zsh Nearcolor
code](https://github.com/zsh-users/zsh/blob/master/Src/Modules/nearcolor.c)

[Pastel](https://github.com/sharkdp/pastel/blob/master/src/lib.rs)

[ANSI](https://en.wikipedia.org/wiki/ANSI_escape_code#Colors)

# Terminal tests

| Terminal | `TERM` | `COLORTERM` | 16 palette | `colors` | `RGB` | `setrgbf` | `setrgbb` | colons |
| -------- | ------ | ----------- | ---------- | -------- | ----- | --------- | --------- | ------ |
| `alacritty` | `alacritty` | `truecolor` | custom | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `;` only |
| `gnome-terminal` | `xterm-256color` | `truecolor` | custom (configurable, has xterm, has "rxvt"<sup>1</sup>) | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | both |
| `kitty` | `xterm-kitty` | `truecolor` | custom, near xterm | 256 | unset | `\E[38:2:%p1%d:%p2%d:%p3%dm` (ANSI w/ colons) | `\E[48:2:%p1%d:%p2%d:%p3%dm` (ANSI w/ colons) | both |
| `konsole` | `xterm-256color` | `truecolor` | custom (configurable) | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `;` only |
| Linux virtual terminal | `linux` | unset | VGA? (no brights, configurable) | 8 | unset | unsupported | unsupported | `;` only |
| `urxvt` | `rxvt-unicode-256color` | `rxvt` | xterm | 256 | unset | unsupported | unsupported | `;` only |
| `st` (unconfigured) | `st-256color` | `rxvt` | xterm | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `;` only |
| `terminator` | `xterm-256color` | `truecolor` | custom | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | both |
| `xfce4-terminal` | `xterm-256color` | `truecolor` | VGA (configurable) | 256 | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | both |
| `uxterm` | `xterm` | unset | xterm | 8 (supports 256) | unset | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | both |
| `uxterm -tn xterm-direct` | `xterm-direct` | unset | xterm | 16777216 (>8 maps to 3-byte RGB) | set | `\E[38;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | `\E[48;2;%p1%d;%p2%d;%p3%dm` (unset, ANSI) | both |

<sup>1</sup> `gnome-terminal`'s rxvt color scheme uses #FAEBD7 for white and has a darker bright black than the real rxvt
=======
[Lab color](http://www.photoshopbuzz.com/what-is-lab-color-photoshop/)


Other links:
 - https://gist.github.com/XVilka/8346728
 - https://gist.github.com/zchee/9f6f2ca17acf49e04088
 - 
