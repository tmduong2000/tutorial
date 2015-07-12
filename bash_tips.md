### Getops Usage
#### Used variables
```bash
getopts OPTSTRING VARNAME [ARGS...]
```
variable | description
--- | ---
OPTIND | Holds the index to the next argument to be process
OPTARG | will store value of flag
OPTERR | (0\|1) 

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
