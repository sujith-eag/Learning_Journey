
```bash
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "hello" 
hello
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "hello" | tr 'a-z' 'A-Z'
HELLO
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLO LINUX" | tr 'A-Z' 'a-z'
hello linux
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLO LINUX1234" | tr 'A-Z'
tr: missing operand after ‘A-Z’
Two strings must be given when translating.
Try 'tr --help' for more information.
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLO LINUX1234" | tr 'A-Z' 'a-z' | tr -d '0-9'
hello linux
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | -s 'a-z'
-s: command not found
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'a-z'
helo linux
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l' 'o'
heo oinuxxx
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l,o'
helo linuxxx
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' | tr -d '0-9' | tr -s 'l,o,x'
helo linux
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z' -d '0-9' -s 'l,o,x'
tr: extra operand ‘-d’
Try 'tr --help' for more information.
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr -d '0-9' -s 'l,o,x'
tr: extra operand ‘-s’
Try 'tr --help' for more information.
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr -d -s '0-9' 'l,o,x'
HELLOOOO LLLINUXx
sujith@sujith-Latitude-7490:~/Desktop/labFiles$ echo "HELLOOOO LLLINUXxx1234" | tr 'A-Z' 'a-z'| tr -d -s '0-9' 'l,o,x'
helo linux

```