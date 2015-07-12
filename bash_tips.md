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
