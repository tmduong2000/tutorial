

###Cursor Movement
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
h | Move left | l | Move right
j | Move down | k | Move up
w | next word | b | the beginning of the word
W | next blank delimited word | B | the beginning of blank delimited word
e | the end of the word | E | the end of blank delimited word
( | previous sentence back | ) | next sentence
{ | previous paragraph | } | next paragraph
]] | sections forward next { in 1st col | [[ | sections backward to prev { in 1st col
][ | sections forward next } in 1st col | [] | sections backward to prev } in 1st col
^ | the beginning of the line (or 0) | $ | the end of line
1G | first line of file | G | last line of file
nG | nth line of file | :n | nth line of file
fc | Move forward to c | Fc | Move backward to c
H | top of screen | L | botton of screen
M | middle of screen | |
% | Move to associated (), {}, []


###Scrolling
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
^e | scroll down one line ("expose") | ^y | scroll up one line
^d | scroll down half screen | ^u | scroll down one screen
^f | scroll down one screen ("forward") | ^b | scroll up one screen
zz | center cursor line in window
zh | scroll left | zl | scroll right
zt | scroll top | zb | scroll bottom

###Insert Mode
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
i | insert before cursor | a | insert (append) after cursor
I | insert at the beginning of line | A | insert (append) at the end of line
o | open below curr line | O | open above curr line
ea | insert (append) at the end of word | Esc | exit insert mode

###Editing
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
r | replace a single char |  | 
J | join line below to the current one | |
cc | change (replace) entire line | c$ | replace to the end of line
cw | replace to the end of the word | |
s | delete char and substitue text | S | delete line and substitude text (same as cc)
xp | transpose two letters (delete and paste) | |
u | undo | Ctrl + r | redo

###Cut and Paste
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
yy | copy a line | nyy | copy n lines
yw | copy a word | y$ | copy to end of line
p | paste after cursor | P | paste before cursor
dd | delete a lien | ndd | delete n lines
dw | delete a word | D (d$) | delete to the end of line
x | delete char | nx | delete n-char

###Search and replace
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
/pattern | search for patter | ?pattern | search backward for pattern
n | repeat search in the same direction | N | repeat search in opposite direction
:%/old/new/g | replace all old with new throughout file | :%s/old/new/gc | replace all with confirmations

###Working with multiple files
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
:e fname | edit a file in new buff |  | 
:bnext (:bn) | go to next buff | :bprev (:bp) | go to prev buff
:bd | delete a buffer (close a file) | :bd! | force close
:sp fname | open file in new buff and split window | :vsp fname | open a file in new buff and V-Split
^ws | split windows | ^wv | vertical split window
^wq | quit windows | ^ww | split window
^wh | move cursor to L-Win (V-Split) | ^wl | move cursor to R-W (V-Split)
^wj | move cursor to Win below (H-Split) | ^wk | move cursor to win above (H-Split)

###MISC
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
:.= | display curr line | := | display total lines
:!cmd | exec Unix cmd | r!cmd | insert output from Unix cmd into file after cursor
:sh | startup a shell enter cmd
:r fn | read file 
:w | write to file | :w newF | write current content to new file
:12,35w newF | write line 12-35 to new file | :w! prevF | write content over a pre-existing file
:w>> otherF | append text to other File


###Tabs
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
:tabnew fn/:tabn fn | open a file in new tab | ^wT  | Move curr Split-win into its own Tab
:tabedit fn | edit specified file in a new tab | :tabfind fn | open a new tab with filename, searching the 'path to find it
gt/:tabnext/:tabn | move to next tab | gT/:tabprev/:tabp | move to prev-tab
:tabfirst | goto first tab | :tablast | goto last tab
^PgDn | goto next tab | ^PgUp | goto previous tab
#gt | move to tab number # starting from 1 | :tabmove # | move curr tab to #th position
:tabclose/:tabc {i} | close curr tab and all its windows | :tabonly/:tabo | clase all tabs except curr
:tab ball | show each buffer in a tab (up to 'tabpagemax' tabs) | :tab help | open a new help widnow in its own tab page
:tab drop {file} | open {file} in a new tab, or jump to a window/tab containing the file | :tab split | copy the curr window to a new tab of its own
:sp fn | creates a new window in the current tab editing the specified file | ^WT | window can be moved to a new tab by pressing
:tab sp | split the current window, but open the spit in a new tab
```
vim -p *.py
:set path=.,,**

set switchbuf=usetab
nnoremap <F8> :sbnext<CR>
nnoremap <S-F8> : sbprevious<CR>

nnoremap <C-Left> :tabprevious<CR>
nnoremap <C-Right> :tabnext<CR>
nnoremap <silent> <A-Left> : execute 'silent! tabmove ' . <tabpagenr()-2)<CR>
nnoremap <silent> <A-Right> :execute 'silent! tabmove ' . tabpagenr()<CR>

let notabs = 0
nnoremap <silent> <F8> :let notabs=!notabs<Bar>:if notabs<Bar>:tabo<Bar>:else<Bar>:tab ball<Bar>:tabn<Bar>:endif<CR>

```


###Marking text (visual mode)
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
v | start visual mode | V  | start linewise visual mode
^v | start visual block mode | |
o | move to other end of marked area | O | move to other corner of block
aw | mark a word | |
ab | a block with () | aB | a block with {}
ib | inner block with () | iB | inner block with {}
Esc | exit visual mode | |


###Visual commands
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :---
\> | shift text right | <  | shift text left
y | copy marked text | d | delete marked text
