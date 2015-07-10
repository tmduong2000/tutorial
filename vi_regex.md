## Substitude command
### Search & Replace
```html
:range s[substitude]/pattern/string/cgiI
   c   cofirm each substitution
   g   replace all occurrences in the line
   i   ignore case
   I   don't ignore case
```

### Range of peration, line addressing
```
Specifier                    Description
#                 an absolute line number
.                 current line
$                 last line
%                 whole file.  The same as 1,$
't                position of mark "t"
/pattern[/]       next line where text pattern match
?pattern[?]       previous line where text pattern matches
\/                next line where the previously used search pattern matches
\?                previous line where the previously used search pattern matches
\&                the next line where the previously used substitute pattern matches
```

Example | Explain
--- | ---
10, 20 | from 10 to line 20
/section 1/+,/section 2/- | all lines between section 1 and section 2, non-inclusively, i.e. the lines containing section 1  and section 2 will not be affected
/section 1/;/Subsection/-,/Subsection/+ | first find section 1, then first line with Subsection, step one line down (beginning of the range) and find the next line with Subsection, step one line up (end of range)
: /Section/+ y | this will search for the Section line and yank (copy) one line after into buffer
: // normal p | and that will search for the next Section line and put (patse) the saved text on the next line
s: /dir1/dir1.0: /dir1/dir1.1:g | is equivalent to s/\/dir1\/dir1.0\/dir1\/dir1.1/g


### "Escaped" characters or metacharacters
no |     Matching      | no |        Matching
---| --- | --- | ---
. | any char except new line
\s | whitespace char | \S | non-whitespace char
\d | digit | \D | non-digit
\x | hex digit | \X | non-hex digit
\o | octal digit | \O | non-octal digit
\h | head of word char (a,..,Z, _) | \H | non-head of word char
\p | printable char | \P | linke \p, but excluding digits
\a | alphabetic char | \A | non-alphabetic char
\l | lowercase char | \L | non-lowercase char
\u | uppercase char | \U | non-uppercase char


### Quantifiers, Greedy and Non-Greedy
Quantifier | Description
--- | ---
* | matches 0 or more of preceding char, ranges or metacharacters .* matches everything including empty line
\\+ | matches 1 or more of preceding charac
\\= | matches 0 or 1 more of the preceding char
\\{n,m} | matches from n to m
\\{n} | matches exactly n times
\\{,m} | matches at most m
\\{n,} | matches at least n
\\{-} | matches 0 or more of the preceding atom
\\{n,m} | matches 1 or more of the preceding char
\\{-n, } | matches at least or more of the preceding chars
\\{-,m} | matches 1 or more of the preceding char


### Grouping and backreferences
no | meaning | no | meaning
--- | --- | --- | ---
& | whole matched pattern | \L | the following char are made lowercase
\0 | whole matched pattern | \U | the following char are made uppercase
\1 | matched pattern in first part of \(\) | \E | end of \U and \L
\2 | matched pattern in the second pair | \e | end of \U and \L
... | ... | \r | split line in two at this poind
\9 | matched pattern in the ninth pari | \l | next char made lower case
~ | the previous substitute string | \u | next char made uupper case

### Regexp Operator Precedence
Precedence | Regexp | Description
--- | --- | ---
1 | \(\) | grouping
2 | \=,\+,*,\{n} etc. | quantifiers
3 | abc\t\.\w | sequence of chars/metachars, not containing quatifiers or grouping operators
4 | \| | alternation

### Global search and execution
```
:range g[lobal][!]/pattern/cmd
Execute the Ex command cmd (default ":p") on the lines within [range] where pattern matches.  If pattern is preceded with a ! - only where match does not occur.
```
#### Example
Example | Explain
--- | ---
:g/^$/ d | delete all empty lines in a file
:g/^$/,/./-j | reduce multiple blank lines to a single blank
:10,20g/^/ mo 10 | reverse the order of the lines starting from the line 10 up to the line 20
:'a,'b g/^Error/ .w >> errors.txt | in the text block marked by 'a and 'b find all the lines starting with Error and copy (append) them to "errors.txt" file.
:g/^Error: / copy $ \| s /Error/copy of the error/ | will copy all Error line to the end of the file and then make a substitution in the copied line.  Without giving the line addresss : s will operate on the current line, which is the newly copied line.
:g/^Error: / s /Error/copy of the error/ \| copy $ | here the order is reversed: first modify the string then copy to the end
