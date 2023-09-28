## VIM

vim guides: *02.5*	Undo and Redo

### operators
* x - delete character
* r - replace character. e.g. rg will replace current char with g
* c - change. e.g. ce change until end of the word, cd, c$
* p - put previously deleted text after cursor
* a - append after cursor
* A - append at the end of the line
* y - yank (copy). yy yanks whole line. yw janks word.

* 
### motions
* w - go to the beginning of next word
* e - go to the end of next word
* b - backward to the beginning of word
* ge - backward to the end of the word

### search:
* / - start searching
* ? - start searching in backward direction)
* n - next occurence
* N - prev occurence
* :set ic - ignore case while searching
* :set noic - no ingore icase
* /phrase/c - ignore case one time while searching

### substitute
* :s/thee/the - replace single occurence
* :s/thee/the/g - replace all occurences in the line
* :%s/thee/the/g - replace all occurences in the whole file
* :%s/thee/the/gc - the same as above but ask for Confirm before every corectness

### modes
* R - turn on replace mode
* v - visual selection mode


### other:
* hl -> left,right
* jk -> down,up
* o/O -> open line below/above
* Ctrl + U/D: Scroll up/down half a screen.
* Ctrl + B/F: Scroll backward/forward one screen
* Ctrl+G - current location in the file
* % - go to matching bracket

* v  motion  :w FILENAME  saves the Visually selected lines in file FILENAME.

* ciw - remove word and start insert mode
* cc - delete line and start insert mode
* dd - delete line and stay in normal mode
* dw - delete word and stay in normal mode(space is also removed before next word)
* de - delete word and stay in normal mode 
* d$ - delete to the end of the line
* gg - go to top of file
* G - go to bottom of file
* $ - go to the end of the line
* gx - open url under cursor in browser
* ct, - change to first ,


## vim-surround
suround selected text with curly braces:
```
hjkl to navigate to the start of selection
v - enter visual mode
hjkl to select code
S - start surround mode
b - surround with curly bracket without space (you can use '(' to have space)
```


## ideavim
* https://github.com/JetBrains/ideavim/blob/master/src/main/java/com/maddyhome/idea/vim/package-info.java
