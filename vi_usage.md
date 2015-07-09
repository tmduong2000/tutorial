

###Cursor Movement
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
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
zz | center cursor line in window
zh | scroll left | zl | scroll right
zt | scroll top | zb | scroll bottom

###Insert Mode
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
i | insert before cursor | a | insert (append) after cursor
I | insert at the beginning of line | A | insert (append) at the end of line
o | open below curr line | O | open above curr line
ea | insert (append) at the end of word | Esc | exit insert mode

###Editing
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
r | replace a single char |  | 
J | join line below to the current one | |
cc | change (replace) entire line | c$ | replace to the end of line
cw | replace to the end of the word | |
s | delete char and substitue text | S | delete line and substitude text (same as cc)
xp | transpose two letters (delete and paste) | |
u | undo | Ctrl + r | redo

###Cut and Paste
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
yy | copy a line | nyy | copy n lines
yw | copy a word | y$ | copy to end of line
p | paste after cursor | P | paste before cursor
dd | delete a lien | ndd | delete n lines
dw | delete a word | D (d$) | delete to the end of line
x | delete char | nx | delete n-char

###Search and replace
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
/pattern | search for patter | ?pattern | search backward for pattern
n | repeat search in the same direction | N | repeat search in opposite direction
:%/old/new/g | replace all old with new throughout file | :%s/old/new/gc | replace all with confirmations

###Working with multiple files
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
:e fname | edit a file in new buff |  | 
:bnext (:bn) | go to next buff | :bprev (:bp) | go to prev buff
:bd | delete a buffer (close a file) | :bd! | force close
:sp fname | open file in new buff and split window | :vsp fname | open a file in new buff and V-Split
Ctrl + ws | split windows | Ctrl + wv | vertical split window
Ctrl + wq | quit windows | Ctrl + ww | split window
Ctrl + wh | move cursor to L-Win (V-Split) | Ctrl + wl | move cursor to R-W (V-Split)
Ctrl + wj | move cursor to Win below (H-Split) | Ctrl + wk | move cursor to win above (H-Split)


###Tabs
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
:tabnew fn (:tabn fn) | open a file in new tab | Ctrl + wT  | Move curr Split-win into its own Tab
gt (:tabnext or :tabn) | move to next tab | gT (:tabprev or :tabp) | move to prev-tab
#gt | move to tab number # | :tabmove # | move curr tab to #th position
:tabclose (:tabc) | close curr tab and all its windows | :tabonly (:tabo) | clase all tabs except curr

###Marking text (visual mode)
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
v | start visual mode | V  | start linewise visual mode
Ctrl + v | start visual block mode | |
o | move to other end of marked area | O | move to other corner of block
aw | mark a word | |
ab | a block with () | aB | a block with {}
ib | inner block with () | iB | inner block with {}
Esc | exit visual mode | |


###Visual commands
Keys     | Description | Keys | Description   
:--- | :--- | :--- | :--- | :---
> | shift text right | <  | shift text left
y | copy marked text | d | delete marked text
