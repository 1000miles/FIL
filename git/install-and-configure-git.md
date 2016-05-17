# Git

## 1. Check for Git

1.1 Open your terminal (Mac) or shell (Win) program

1.2 Check if you already have Git installed on your computer:
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
## 3. Configure Git

3.1 Configure your username globally for Git:
```
$ git config --global user.name "Firstname Lastname"
```
3.2 Configure your email address globally for Git:
```
$ git config --global user.email "email@example.com"
```

3.3 To avoid typing username and password again and again, we can use a helper. Check if you have the Git credentials helper on your computer:
```
$ git credential-osxkeychain
```
3.3.1 If it is already installed, output should be:
```
usage: git credential-osxkeychain <get|store|erase>
```
3.3.2 If it is not installed, download the helper with:
```
$ curl -O http://github-media-downloads.s3.amazonaws.com/osx/git-credential-osxkeychain
```
3.3.2.1 Then move the downloaded file to the /usr/local/bin/ directory:
```
$ sudo mv git-credential-osxkeychain /usr/local/bin/
```
- sudo = super user do
- mv = move
- /usr/local/bin = the path where all your local binaries are located

3.3.2.2 Make the file an executable, means in order to run and use it:
```
$ chmod u+x /usr/local/bin/git-credential-osxkeychain
```
chmod = change mode
u = user
+x = add & make it executable
