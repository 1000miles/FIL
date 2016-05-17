# Unix
## Cheat Sheet

Create a new file in the directory where you are, do:
```
$ touch file.format => file.md (example)
```

Create a new directory (=folder) from the project root, do:
```
$ mkdir foldername
```

Change the name of a file(filename1) to another name (filename2) in the same directory, do:
```
$ mv file1.rb file2.rb
```

Change a file name (`file1`) of one directory to another name (`file2`) in another directory, do:
```
$ mv this_directory/filename1.rb another_directory/filename2.rb
```
Check the current working directory, do:
```
$ pwd
```

List all files in the current directory:
```
$ ls
```

List all files of a directory before you change into that directory:
```
$ ls + tab => ls first_directory/second_directory/file.rb
```

List all files of a directory showing additional infos about permission rights in the long version:
```
$ ls -ll
```

Output:
```
-rw-r--r--  1 username  staff   942 Apr 29 22:09 copy-and-curl-file-from-external-source
-rw-r--r--  1 username  staff  1054 Apr  6 15:58 create-a-file-in-a-non-existing-directory.md
-rw-r--r--  1 username  staff   690 Apr  6 15:58 show-specific-number-of-lines-of-a-file.md
-rw-r--r--  1 username  staff   503 Apr 29 22:19 unix-commands.md
```

List all files including permission rights, group id, username, group role, file size, last changed date and hidden directories/files:
```
$ ls -lha
```

Output:
```
total 32
drwxr-xr-x  6 username  staff   204B Apr 29 22:19 .
drwxr-xr-x  8 username  staff   272B Apr  6 16:03 ..
-rw-r--r--  1 username  staff   942B Apr 29 22:09 copy-and-curl-file-from-external-source
-rw-r--r--  1 username  staff   1.0K Apr  6 15:58 create-a-file-in-a-non-existing-directory.md
-rw-r--r--  1 username  staff   690B Apr  6 15:58 show-specific-number-of-lines-of-a-file.md
-rw-r--r--  1 username  staff   503B Apr 29 22:19 unix-commands.md
```
