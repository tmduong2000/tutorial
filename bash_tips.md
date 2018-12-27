### Variable
##### Special Parameters

Character | Definition
--- | ---
$* | Expands to the positional parameters, starting from one. When the expansion occurs within double quotes, it expands to a single word with the value of each parameter separated by the first character of the IFS special variable.
$@ | Expands to the positional parameters, starting from one. When the expansion occurs within double quotes, each parameter expands to a separate word.
$# | Expands to the number of positional parameters in decimal.
$? | Expands to the exit status of the most recently executed foreground pipeline.
$- | A hyphen expands to the current option flags as specified upon invocation, by the set built-in command, or those set by the shell itself (such as the -i).
$$ | Exapnds to the process ID of the shell.
$! | Exapnds to the process ID of the most recently executed background (asynchronous) command
$0 | Exapnds to the name of the shell or shell script
$_ | The underscore variable is set at shell startup and contains the absolute file name of the shell or script being executed as passed in the argument list. Subsequently, it expands to the last argument to the previous command, after expansion. It is also set to the full pathname of each command executed and placed in the environment exported to that command. When checking mail, this parameter holds the name of the mail file.

<hr>

### Test, [ -- condition valuation utility ]

##### Synopsis
```bash
test expression
[ expression ]
[[ expression ]]

The double bracket [[  construct, also known as 'extended test' or 'New Test' is more versatile, the old test [ is more portable.
To do a simple numeric comparison, use (( )) instead of test
```

Operator | Description | Example
--- | ---- | ---
exit_code | &nbsp;&nbsp;0  --- expression evaluated to true.<br>&nbsp;&nbsp;1 --- expression evaluated to false or expression was missing.<br>>1 --- An error occurred|
-b file | True if file exists and is a block special file. |
-c file | True if file exists and is a character special file. |
-d file | True if file exists and is a directory. |
-e file | True if file exists (regardless of type). |
-f file | True if file exists and is a regular file. |
-g file | True if file exists and its set group ID flag is set. |
-h file | True if file exists and is a symbolic link.|
-k file | True if file exists and its sticky bit is set. |
-p file | True if file is a name pipe (FIFO). |
-r file | True if file exists and is readable. |
-s file | True if file exists and has a size greater than zero.|
-t fd | True if file descriptor is open and is associated with a terminal |
-u file | True if file exists and its user ID flag is set. |
-w file | True if file exists and is writable. |
-x file | True if file exists and is executable. |
-L file | True if file exists and is a symbolic link. |
-O file | True if file exists and its owner matches the euid of this process. |
-G file | True if file exists and its group matches and egid of this process. |
-S file | True if file exists and is a socket. |
fn1 -nt fn2 | True if file1 exists and newer than file2 |
fn1 -ot fn2 | True if file1 exists and older than file2 |
fn1 -ef fn2 | True if file1 and file2 and refer to the same file. |
fn1 -nt fn2 | True if file1 exists and newer than file2 |
-n string | True if the length of string is nonzero. |
-z string | True if length of string is zero |
string | True if string is not the null string. |
s1 = s2 | True if string s1 and s2 are identical. |
s1 != s2 | True if string s1 and s2 are not identical. |
s1 < s2 | True if s1 comes before s2 based on the binary value of chars.|
s2 > s2 | True if s1 comes after s2 based on the binary value of chars. |
n1 -eq n2 | True if the integers n1 and n2 are equal. | a=9 && b="9" && [[ $a = $b ]] && echo "$a == $b" &#124;&#124; echo "$a != $b"
n1 -ne n2 | True if the integers n1 and n2 are not equal. | a=9 && b="5" && [[ $a = $b ]] && echo "$a == $b" &#124;&#124; echo "$a != $b"
n1 -gt n2 | True if the integer n1 is greater than n2. |
n1 -ge n2 | True if the integer n1 is greater and equal n2. |
n1 -lt n2 | True if the integer n1 is less than n2. |
n1 -le n2 | True if the integer n1 is less and equal than n2. |
! expression | True if expression is false. |
e1 -a e2 | True if both exp1 and exp2 are true.<br>The -a operator has higher precedence than -o |
e1 -o e2 | True if both exp1 or exp2 are true |
( expr ) | True if expression is true. |
e1 && e2 | True if both exp1 and exp2 are true |
e1 &#124;&#124; e2 | True if both exp1 or exp2 are true |


### Getops Usage
#### Used variables
```bash
getopts OPTSTRING VARNAME [ARGS...]
```
variable | description
--- | ---
OPTIND | Holds the index to the next argument to be process
OPTARG | will store value of flag
OPTERR | (0&#124;1) 

```bash
############################
# Filename: testgetopt.sh
############################
#!/bin/bash
while getopts "fup:" opt; do
    case $opt in
        f)	flag = $opt
            flag_valule = $OPTARG
            ;;
        \?)
            echo "Invalid option: -$OPTARGS" >&2
            ;;
    esac
done

# This tells getops to move to the next argument.
shift (( $OPTIND - 1 ))

#############################

$ ./testgetopt.sh -f fileabc.txt -u user_abc

```

### Colors and Cursor Movement with tput

#### tput color capabilities
command | description
--- | ---
tput setab [1-7] | set a background color using ANSI escape
tput setb [1-7] | set a background color
tput setaf [1-7] | set a foreground color using ANSI escape
tput setf [1-7] | set a foreground color

#### tput text mode capabilities
command | description
--- | ---
tput bold | set bold mode
tput dim | turn on half-bright mode
tput smul | begin underline mode
tput rmul | exit underline mode
tput rev | turn on reverse mode
tput smso | enter standout mode (bold on rxvt)
tput rmso | exit standout mode
tput sgr0 | turn off all attributes (doesn't work quite as expected)

#### tput cursor movement capabilities
command | description
--- | ---
tput cup Y X | move cursor to screen location X,Y (top left is 0,0)
tput sc | save the cursor position
tput rc | restore the cursor position
tput lines | output the number of lines of the terminal
tput cols | output the number of columns of the terminal
tput cub N | move N character left
tput cub1 | move left one space
tput cuf1 | non-destructive space (move right one space)
tput ll | last line, first column (if no cup)
tput cuu1 | up one line
 
#### tput clear and insert capabilities
command | description
--- | ---
tput ech N | Erase N characters
tput clear | clear screen and home cursor
tput el1 | clear to beginning of line
tput el | clear to end of line
tput ed | clear to end of screen
tput ich N | insert N chars (moves rest of line forward
tput il N | insert N lines

```bash
NORM=$(tput sgr0)
BOLD=$(tput bold)
REV=$(tput smso)
BLUE="$(tput setaf 4 ; tput bold)"

echo -e "Example: ${BOLD} shellscript.sh -a${NORM} foo ${BOLD}-b${NORM} man ${BOLD}-c${NORM} chu ${BOLD}-d${NORM} bar file.ext${NORM}\\n"


```
