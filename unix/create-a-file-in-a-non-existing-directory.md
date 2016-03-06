# Create a File in a non-existing Directory

If we want to create a new file and organize them in folders, we often do this:

First we create a new directory:
```
$ mkdir foldername
```
Then we create a file in this folder:

```
$ touch filename.md
```

The current structure would be like this:
```
.
├── foldername
│   └── filename.md
```

If we create a file with

```
$ touch another_foldername/another_fileame.md
```

and want to have it in a specific folder that isn't there, we would get an error:
```
touch: another_foldername/another_fileame.md: No such file or directory
```

Well, there is a short and handy workaround to create a file AND a folder at the same time:

```
$ mkdir -p another_foldername/another_fileame.md
```

The new structure would be like this:
```
.
├── foldername
│   └── filename.md
├── another_foldername
    └── another_filename.md
```

Explanation: The `p` stands for path and allows to create a path at the same time while you are creating a new file. Isn't that great? :)
