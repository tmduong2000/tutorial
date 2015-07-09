

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
^ | the beginning of the line (or 0) | $ | the end of line
1G | first line of file | G | last line of file
nG | nth line of file | :n | nth line of file
fc | Move forward to c | Fc | Move backward to c
H | top of screen | L | botton of screen
M | middle of screen | |
% | Move to associated (), {}, []

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
:bd | delete a buffer (close a file) | |
:sp fname : open file in new buff and split window | :vsp fname | open a file in new buff and V-Split
Ctrl + ws | split windows | Ctrl + wv | vertical split window
Ctrl + wq | quit windows | Ctrl + ww | split window
Ctrl + wh | move cursor to L-Win (V-Split) | Ctrl + wl | move cursor to R-W (V-Split)
Ctrl + wj | move cursor to Win below (H-Split) | Ctrl + wk | move cursor to win above (H-Split)
