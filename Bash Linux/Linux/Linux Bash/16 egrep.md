

[*grep*](/personal-site/docs/bash-linux/command-docs/grep) stands for "global/regular expression/print."       
It is a powerful tool for searching text and is commonly used in UNIX text editors.    

`grep` program searches one or more files by line to match against a specified regular expression. Each line is treated as the string and `grep` searches for any substring of the line that matches the regex. If found, by default `grep` outputs the matching lines.

`grep` only applies the POSIX basic regular expression set and extended regular expressions set `egrep` is used.      
`egrep` can do everything `grep` can do, there is no need to use anything other than `egrep`.

```bash {frame="none"}
egrep [options] regex filename(s)

grep [OPTIONS] PATTERNS [FILE(s)]
```
regex is a string that can but does not have to include metacharacters.     
Files can be listed with space or wildcards.     

>[!important]
>The regex is placed in single quotes `' '` to avoid metacharacters being interpreted as wildcards and doing filename expansion (globbing) on wildcards `* ? []`.     
>`|` will sets up pipes instead of performing OR action. 
>Items Found in `" "` are interpreted, they are not treated literally like in `' '`



To search for a specific phrase using quotes makes it easier to search for phrases or single words:
```bash {frame="none"}
$ egrep "is not" haiku.txt

$ egrep "not" haiku.txt
```

```bash {frame="none"}
egrep 2022 *.txt  
# all lines that contain 2022

egrep ^a *.txt
# all lines that start with an a
```

```bash {frame="none"}
egrep '[Ss]mith' *.txt
# Find lines having smith or Smith

egrep 'Duke|Zappa' *.txt
# Find lines containing Duke or Zappa
```

```bash {frame="none"}
egrep '[0-9]+' *.txt
# Find lines that contain atleast one digit

egrep '[A-Za-z]+[[:punct:]]' *.txt
# Find lines that contain letters followed by any punctuation mark anywhere in the line. 
```

```bash {frame="none"}
egrep '^[0-9]*[^0-9]+$' *.txt
# Finds lines that if they have digits are found at the beginning of the line.

egrep '^[A-Z][a-z]+ [A-Z][a-z]+$' *.txt
# Find all lines that contain exactly two words, both capitalized

egrep '[a-z]+ [a-z]+ [a-z]+' *.txt
# Find lines that contain at least 3 words, lowercased
```

_____
`-i, --ignore-case`    ignore case distinctions in patterns and data 
(Perform case-insensitive search  `grep -i "error\|fail" logfile.txt`)

`-c, --count`               print only a count of selected lines per FILE 
(Count the number of lines that match the pattern)  `grep -c "error" logfile.txt`

`-h, --no-filename `        suppress the file name prefix on output 
( Suppress filename outputs when searching multiple files `grep -h "error" *.log`)

`-l, --files-with-matches`  print only names of FILEs with selected lines
`grep -l "error" *.log`

`-n, --line-number  `       print line number along with matching output lines
`grep -n "error" logfile.txt`

`-v, --invert-match`        select non-matching lines (print the lines that do not have the pattern) `grep -v "sucess" logfile.txt`

`-o, --only-matching `      show only nonempty parts of lines that match
(Display on the matched text instead of the full line) `grep -o "error" logfile.txt`

`-e, --regexp=PATTERNS `    use PATTERNS for matching
(Use extended regex pattern for complex patterns ) `grep -e "error\|fail" logfile.txt`

`^` Matches the lines that starts with the specific pattern
`$` Match lines that end with specific pattern
`grep "^Start" logfile.txt`   `grep "End$" logfile.txt`

`-r, --recursive`    like `--directories=recurse`

`-w, --word-regexp`   match only whole words

`-f, --file=FILE`       take PATTERNS from FILE




### Options

- **Recursive Search (`-r`)**: Searches through all files in the directory and subdirectories.
```bash {frame="none"}
$ egrep -r "Yesterday"
```



- **Word Boundary (`-w`)**: Limits matches to whole words only.
```bash {frame="none"}
$ grep -w "The" haiku.txt
```

- **Line Numbers (`-n`)**: Numbers the results with the line numbers.
```bash {frame="none"}
$ grep -n "it" haiku.txt
```

- **Case Insensitivity (`-i`)**: Makes the search case insensitive.
```bash {frame="none"}
$ grep -n -w -i "the" haiku.txt
```

- **Invert Match (`-v`)**: Inverts the search to get all lines that do not match.
```bash {frame="none"}
$ grep -v -n -w "the" haiku.txt
```

Regex can be placed in a file and `-f` option can be used to reference the file.    

`-e` and `-f` ???

_______

The outputs of `ls` are piped to `egrep`, Outputs are all regular files whose owner permissions are `rwx`. `^` starts the regex, since `$` is not given, doesn't match whole string. 
```bash {frame="none"}
ls -l /etc | egrep '^-rwx'
```

???
```bash {frame="none"}
ls -l /etc | egrep '.{13}[^1]'
```

____

```bash {frame="none"}
$ cat singly_list_final.c | grep "struct" 
struct node 
	struct node* next;
typedef struct node Node;   // 'Node' as alias for 'struct node'

$ cat singly_list_final.c | grep -o "struct"
struct
struct
struct
struct
```

- **Count (`-c`)**: Gives the count of the matches for each file instead of a list.
```bash {frame="none"}
$ egrep -c '[0-9]{1,3}' /etc/resolve.conf

$ cat singly_list_final.c | grep -c "struct"
3

$ cat singly_list_final.c | grep -cv "struct" 
393
```



```bash {frame="none"}
/c_data_structures$ cat singly_list_final.c | grep -o "struct"
struct
struct
struct
struct
```

```bash {frame="none"}
/c_data_structures$ grep "struct" *.c
circular_singly_linked_list.c:struct node 
circular_singly_linked_list.c:	struct node *next;
doubly_circular_linked_list.c:typedef struct node Node;
Rr.c:typedef struct node Node;
singly_list.c:struct node
singly_list.c:    struct node *next;
singly_list.c:    struct node new* = (struct node*) malloc(sizeof(struct node));
singly_list.c:        struct node temp* = head;
singly_list.c:    struct node tem* = head;

singly_list_final.c:struct node 
singly_list_final.c:	struct node* next;
singly_list_final.c:typedef struct node Node;   // 'Node' as alias for 'struct node'
```

```bash {frame="none"}
/c_data_structures$ grep -o "struct" *.c
circular_singly_linked_list.c:struct
circular_singly_linked_list.c:struct
doubly_circular_linked_list.c:struct
Rr.c:struct
singly_list.c:struct
singly_list.c:struct
singly_list_final.c:struct
```

```bash {frame="none"}
/c_data_structures$ grep -on "struct" *.c
circular_singly_linked_list.c:6:struct
doubly_circular_linked_list.c:4:struct
Rr.c:4:struct
singly_list.c:33:struct
singly_list.c:66:struct
singly_list_final.c:4:struct
```

```bash {frame="none"}
/c_data_structures$ grep -on -l "struct" *.c
circular_singly_linked_list.c
doubly_circular_linked_list.c
singly_list.c
singly_list_final.c

/c_data_structures$ grep -o -l "struct" *.c
circular_singly_linked_list.c
doubly_circular_linked_list.c
singly_list.c
singly_list_final.c

/c_data_structures$ grep -n -l "struct" *.c
circular_singly_linked_list.c
doubly_circular_linked_list.c
singly_list.c
singly_list_final.c

/c_data_structures$ grep -l "struct" *.c
circular_singly_linked_list.c
doubly_circular_linked_list.c
singly_list.c
singly_list_final.c
```


