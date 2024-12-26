

A path is a description of how to reach a particular location in the file location. is is needed when the file is not in the present working directory.
Path can be absolute or relative.

The path can be omitted for executable files if the file is stored in our `PATH` variable.

`absolute path` always starts from the root level of file space(`/`) and specifies each directory from there to the location of interest, separating each by `/`.
The correct notation is to end the directory name with `/`. but for a directory it can be omitted.
`/home/foxr/temp`

`relative path` describes the change from where we are (working directory) to where we want to go.
The relative path does not start with `/`, it should not.  (`/` in beginning should start from root, home)
`../xaps/dir`  moving up and down.


#### Filename arguments with Paths

`./` indicates the current directory when multiple directories are being passed as argument.

#### `PATH` variable

The environment variable we have is `PATH` which has the paths to various directories that might contain executable programs.  `cat, ls, cd` are all in `user/bin`

```bash
/home/sujith/.nvm/versions/node/v20.17.0/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```
We can modify `PATH` using assignment statement.
Value for it can include the variable's value itself that is `$PATH`.
Contents of it are list of directories separated by `:`
To add to the path we can `PATH=$PATH:new_directory`  or `PATH=new_directory:$PATH`.

It makes sense to have the most commonly used directories listed earlier.

#### Specifying filenames with wildcards

`ls *` is same as `ls`
`ls *.txt`  `ls f*.txt`   `ls f*.*`
The bash interpreter performs the filename expansion or `globbing` prior to the execution.

`*` Match with everything
`?` match any one character
`[chars]` match any one character in the list  `[aeiou]`   one `[]` is for one character only.
	`ls [abc][abc][abc]`
`[char1-char2]` match any one of the character in the range. `[0-9] [a-e] [A-Z]`
`{word1,word2,word3}` match any one of the words   
	`file?.{dat,txt}`  `{aa,file1,mystuff,target}.txt`
`[!chars]`  match any one character not in the list   `ls [!a]*` first character not `a`

