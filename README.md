# Ukrainian keymap for Neovim
Typing in languages, other than English can be a pain in Neovim, since Vim motions only work when your keyboard input language is English. 
So you'd have to constantly switch to English in order to move, and to your language of choice to actually type.
But keymaps allow you to remap English characters to characters of your language. 
That way all of the motions still work and you can type in your desired language.

Neovim already comes with a set of keymaps for a number of different languages, including Ukrainian with the JCUKEN layout. However, that keymap maps some characters incorrectly. For example, it maps the ```$``` symbol to ```*```, when in reality, it should be ```;```

This keymap accurately maps characters from English QWERTY layout to [Ukrainian JCUKEN layout](https://en.wikipedia.org/wiki/JCUKEN#Ukrainian).

## How to use
1. Firstly, you need to find a folder where Neovim keeps all of the keymaps. You can do that by executing the following command in Neovim itself:
```vim
:echo globpath(&rtp, "keymap/*.vim")
```
This will give you a list of paths to every keymap file.

2. Then, you need to copy [ukrainian-jcuken-improved.vim](ukrainian-jcuken-improved.vim) file into the same folder.
3. After that, tell Neovim to use the added keymap. If you use Lua for you configuration, add the following line to your ```init.lua``` or any other configuration file:
```lua
vim.opt.keymap = "ukrainian-jcuken-improved"
```
If you use Vimscript for your configuration, you can set the keymap like this:
```vim
set keymap=ukrainian-jcuken-improved
```
4. Use ```Ctrl-^``` in Insert mode to switch between English and a keymap.

## Additional settings
When using a keymap there are a few more settings that can improve your life:

```iminsert``` - it specifies whether to use English or a keymap by default in Insert mode. By default it seems to use the keymap, but most of the time you'd probably want English. To make Neovim use English set this option to ```0```:

Lua:
```lua
vim.opt.iminsert = 0
```
Vimscript:
```vim
set iminsert=0
```
For more info, see the [documentation](https://neovim.io/doc/user/options.html#'iminsert')

```imsearch``` - it specifies whether to use English or a keymap by default when entering a search pattern. Setting this option to ```-1``` makes it use the value of ```iminsert```, which is the best option, in my opinion.

Lua:
```lua
vim.opt.imsearch = -1
```
Vimscript:
```vim
set imsearch=-1
```
For more info, see the [documentation](https://neovim.io/doc/user/options.html#'imsearch')

I also like to remap the key to toggle between English and a keymap, since ```Ctrl-^``` does not seem convenient for me. I use ```Ctrl-L``` to do that:

Lua:
```lua
vim.keymap.set("i", "<C-l>", "<C-^>")
```
Vimscript:
```vim
inoremap <C-l> <C-^>
```
