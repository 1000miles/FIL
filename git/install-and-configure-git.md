# Git

## 1. Check for Git:

### Open your terminal (Mac) or shell (Win) program. Check if you already have Git installed on your computer:
```
$ git --version
```
Output Example:
```
git version 2.6.4
```

## 2. Install Git:

Mac:
```
Go to https://git-scm.com/download/mac
```

Linux:
```
$ sudo yum install git-all
```

Debian-based Linux, e.g. Ubuntu:
```
$ sudo apt-get install git-all

```
## 3. Configure Git:

### Configure your username globally for Git:
```
$ git config --global user.name "Firstname Lastname"
```
### Configure your email address globally for Git:
```
$ git config --global user.email "email@example.com"
```

### Configure your username project-related for it:
```
$ git config user.name "Firstname Lastname"
```
### Configure your email address project-related for Git:
```
$ git config user.email "email@example.com"
```

### To avoid typing username and password again and again, we can use a helper. Check if you have the Git credentials helper on your computer:
```
$ git credential-osxkeychain
```
#### If it is already installed, output should be:
```
usage: git credential-osxkeychain <get|store|erase>
```
#### If it is not installed, download the helper with:
```
$ curl -O http://github-media-downloads.s3.amazonaws.com/osx/git-credential-osxkeychain
```
##### Then move the downloaded file to the /usr/local/bin/ directory:
```
$ sudo mv git-credential-osxkeychain /usr/local/bin/
```
- sudo = super user do
- mv = move
- /usr/local/bin = the path where all your local binaries are located

##### Make the file an executable, means in order to run and use it:
```
$ chmod u+x /usr/local/bin/git-credential-osxkeychain
```
chmod = change mode
u = user
+x = add & make it executable
