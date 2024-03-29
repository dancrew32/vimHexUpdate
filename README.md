## HexUpdate
### What it does
This will help update hex color values of words (that your cursor is currently on) up or down a shade.


### Installation
- Move `/cssScript` into `~/.vim/`
- Add the following to your `~/.vimrc` (remap to whatever you prefer)


```vimscript
"Update a hex value up/down a shade
function! HexUpdate(operator, shade)
    let hex = expand("<cword>")
    let newHex = system("php ~/.vim/cssScript/hex.php ". hex ." ". a:operator . a:shade)
    execute "normal ciw". newHex
endfunction

nnoremap <F8> :call HexUpdate("-",1)<CR>
nnoremap <F9> :call HexUpdate("+",1)<CR>
```


- run `:so %` in your `~/.vimrc` file or restart vim
- move your cursor over a hex color value, e.g.

```css
/* your cursor could be here: #f0|0f00; */
background-color: #f00f00;
```


- hit `<F9>` to go up one shade
- hit `<F8>` to go down one shade
- enjoy

### Where would this be useful?
Imagine you need to quickly add a :hover and an :active pseudo state
to some css selection:

- First do this:

```css
a {
    color: #0f0;	
}
a:hover {
    color: #0f0;	
}
a:active {
    color: #0f0;	
}
```

- Move to the `:hover` color and hit `<F9>` to go up one shade
- Move to the `:active` color and hit `<F9>` two times to go up two shades

You should end up with this:

```css
a {
    color: #0f0;	
}
a:hover {
    color: #26ff26;	
}
a:active {
    color: #46ff46;	
}
```
