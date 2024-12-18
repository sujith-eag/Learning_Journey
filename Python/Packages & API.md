```python CS50
# 3rd party libraries called packages can be gotten at "pypi.org" (python package index)
# "pip" is a program within python to install package by running a command

# command for downloading cow say   "pip install cowsay" ,  ASKI art
import cowsay
import sys      # to allow for command line entry

if len(sys.argv) == 2:
    cowsay.cow ( "hello, " + sys.argv[1] )   # this only takes one argument so no ","  it has been concatinated with "+"
if len(sys.argv) == 2:
    cowsay.trex ( "hello, " + sys.argv[1] )   # yup, a trex art
```

```python CS50  
APIs (Application Programing interface)  

# not general to python, 3rd party services that we can talk to and download data to our system

# "requests" is a popular package that can be installed to make web and internet requests

# pypi.org/project/requests
pip install requests

# JSON - Java script object notation (getting the file data from itune in text file)
# language agnostics means any language can be used to read and edit it
# json library (comes with python)
# docs.python.org/3/library/json.html

import json
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()     # break is used to exit a loop,  sys.exit exits the whole program
response = requests.get ("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print ( response.json( ) )

# using if to make sure the length is atleast one word, then exit
# response is stored in variable called "response"
# requests.get is a function to get a requests
# url is based on the document,  last bit of name is left to be entered by + concatinate
# the data is printed as json without formating
```

```python
# to format it a little bit more
import json
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()        

response = requests.get ("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print (  json.dumps (response.json( ), indent=2 ) )

# json.dumps meaning dump string formats it to make it readable
# indent = 2 makes it have 2 spaces

  
# taking out just the trackname of a single song
import json
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()        
  
response = requests.get ("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
data = response.json()            # the data is stored in json format
for list in data["results"]:     # "results" is the key word in the json file from itune which has the list having "trackName"
    print( list["trackName"] )   
# list gets only the list of trackName with songs as values
# only the values of each keyword is printed

  
import json
import requests
import sys
  
if len(sys.argv) != 2:
    sys.exit()        

response = requests.get ("https://itunes.apple.com/search?entity=song&limit=50&term=" + sys.argv[1])

data = response.json()
for list in data["results"]:  
    print( list["trackName"] )    # ok gets 50 trackNames
```