# Show specific numbers of lines of a file

Sometimes we have a file with thousands of lines of code and feel a bit overwhelmed.

With this command you can show the first 10 lines of code counting from the head:
```
$ head -n 10 filename.md
```
If you want to count the lines from the bottom, run this command:
```
$ tail -n 10 filename.md
```
If you are searching for a specific term (let's say 'folder'), you can use this:
```
$ head -n 10 create-a-file-in-a-non-existing-directory.md | grep folder
```

The output in your CLI would be this:

```
If we want to create a new file and organize them in folders, we often do this:
$ mkdir foldername
Then we create a file in this folder:
```
