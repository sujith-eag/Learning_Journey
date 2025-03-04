
```bash
$ echo "hello" 
hello

$ echo "hello" | tr 'a-z' 'A-Z'
HELLO

$ echo "HELLO LINUX" | tr 'A-Z' 'a-z'
hello linux

$ echo "HELLO LINUX1234" | tr 'A-Z'
tr: missing operand after ‘A-Z’
Two strings must be given when translating.

$ echo "HELLO LINUX1234" | tr 'A-Z' 'a-z' | tr -d '0-9'
hello linux

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | -s 'a-z'
-s: command not found

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'a-z'
helo linux

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l' 'o'
heo oinuxxx

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l,o'
helo linuxxx

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l,o,x'
helo linux

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' -d '0-9' -s 'l,o,x'
tr: extra operand ‘-d’
Try 'tr --help' for more information.

$ echo "HELLOOOO LLLINUXxx1234" | tr -d '0-9' -s 'l,o,x'
tr: extra operand ‘-s’

$ echo "HELLOOOO LLLINUXxx1234" | tr -d -s '0-9' 'l,o,x'
HELLOOOO LLLINUXx

$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z'| tr -d -s '0-9' 'l,o,x'
helo linux

```