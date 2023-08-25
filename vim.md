## VIM
vim tutor: Lesson 3.4: MORE CHANGES USING c

operators
* x - delete character
* r - replace character. e.g. rg will replace current char with g
* c - change. e.g. ce change until end of the word

* 
motions


* hl -> left,right
* jk -> down,up
* o/O -> insert line below/above
* Ctrl + U/D: Scroll up/down half a screen.
* Ctrl + B/F: Scroll backward/forward one screen

* p - put previously deleted text after cursor
* ciw - remove word and start insert mode
* cc - delete line and start insert mode
* dd - delete line and stay in normal mode
* dw - delete word and stay in normal mode(space is also removed before next word)
* de - delete word and stay in normal mode 
* d$ - delete to the end of the line
* gg - go to top of file
* G - go to bottom of file
* A - go to the end of the line and insert (append)
* w - go to the next word
* e - go to the next word

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
