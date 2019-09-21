# Forcing name changes to lowercase or capitalize on a Mac system

The `mv` (move) command is very powerful. It does not only move your files and folders but can also rename them at the same time.

On a Mac system searching for and listing a file or folder in the terminal is case-insensitive, means the terminal ignores any capital letters and will print out all variations.

To move or change a file name you would usually do by:

```zsh

$ ls # List everything in current directory

file1.js file2.js file3.js

# mv = move
$ mv file1.js File1.js # Change file name `file1.js` to `File1.js`

$ ls

File1.js file2.js file3.js

$ mv file2.js bin/file2.js # Move `file2.js` from current folder into bin/ folder

$ ls # List everything in current directory

File1.js file3.js

$ ls bin/ # List everything in bin/ folder

file2.js

$ mv file3.js bin/File3.js # Move `file3.js` from current directory into `bin/` folder and rename it at the same to `File3.js`

$ ls

< empty >

$ ls bin/ # List everything in `bin/` folder

file2.js File3.js
```

This so far looks pretty neat and does what we want. However, sometimes we need to use  `mv -f filename new_filename` with a force-flag to rename a file or folder.

### Git > Heroku Deployment

For example we originally named our module `./models/employee.js` instead of `./models/Employee.js`. In nodejs (and other programming languages) models are named in capital letters by convention which is why heroku couldn't find our model. Even though the deployment was successful we still faced an application error so that the website didn't show up on heroku. Once we noticed that we renamed the file to `./models/Employee.js` on our local machine and the file name looked as it should be. We then pushed the change to Github and merged to trigger a new automatic deployment to heroku. For strange reasons we still got the same error.

To dive deeper into the error we ran:

```zsh
$ heroku logs ---tail # Print out log stream
```

heroku still could not find the model `Employee`.

We then executed the bash command on the heroku app and navigated to the affected file:

```zsh
$ heroku run bash # requires a heroku login and connection to the app before
$ cd models/
$ ls

employee.js
```

Alright, heroku still has the file `employee.js` of the first deployment on the server. We then looked at Github and saw following:
https://github.com/username/repo-name/tree/master/models/employee.js

That gave us an indication that git never pushed our change to Github because it didn't recognize our change as a change.

Since git still has the old version tracked we needed a way to trigger a change to Github along with the move force command:

```zsh
$ git mv -f models/employee.js models/Employee.js
```

Awesome! That worked and heroku deployed now a working version for the website.




