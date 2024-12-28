
In reality a directory stores links to files and sub directories.
The links are formally known as `hard links`

Each hard link consists of the `item's name` and item's dedicated `inode number`.
The inode number is used to index into or reach the `idode`, which is stores on the disk.
It is through the `inode` that the item's location is reached.

Name in the directory references an inode which contains the pointer's to the physical location(s).

Generally there are one hard link per file and to hard links per directory.
We can create additional links and store them in other locations or by other names.

If we create a hard link to a file somewhere, we are then duplicating the original link which points to the location of the file's disk block. (both the hard links will be identical)
Hard links are more efficient 

A soft link or symbolic link to a file will store a pointer to the original hard link.
(shown as `l` file type when viewed using `ls -l` ). It does not increase the link count.

___


Creating a link is handled through the `ln` instruction.
`ln [-s] existingfile newfile`
where `existingfile` must permit links (there are permissions to forbid links to a file) and `newfile` is the newly created file.
`-s` is used to create a symbolic link, otherwise the default is a hard link.

* Hard links can only point to contents within their current partition. (`/home` is a partition `/etc` is another)
* When a file has two hard links pointing to it with different names, the link count will be 2. when one link is deleted the count becomes 1 but the actual file is not deleted as one is still linking to it. If that is also deleted, then count becomes 0 and file is deleted.
* In a symbolic link, deleting it does not affect the hard link count at all, but if the link it is pointing to is deleted then it becomes a dead link.

If a user does not have access to view the file then the command to make a link will fail.
When creating a hard link, the new hard link takes on the same permissions as the original.

The most common use of hard links is to have multiple access points to directories which have a link count of 2 at minimum.

Common use of symbolic links is to point to files that have been moved or to provide easy shortcut to those files.

