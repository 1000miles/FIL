# Compiling Stylesheets with Sass

If you are using Ruby and want to compile sass or scss files into css stylesheets in your projects there is a simple way to do so. Compiling means that you gather materials from several sources and put them into one file.

##### 1. First you need to install the gem sass from the source Rubygems.org with:

Mac:
```
gem install sass
```
Linux:
```
sudo su -c 'gem install sass'
```

After you have installed the gem you are ready to start. :)

##### 2. Create a folder for your new project which is at the same time your root directory, e.g.:

```
mkdir my_project
```

##### 3. Go into the new project directory with:

```
cd my_project
```

##### 4. In your root directory create 2 directories at the same time and call them 'sass' and 'stylesheets' with:

`mkdir sass stylesheets`

##### 5. Sass comes a long with a handy watch method to keep track of all changes in a directory or a single file:

```
sass --watch input.sass:output.css
sass --watch input-dir:output-dir
```

For a single file, run this command in your command line tool (CLI):
```
sass --watch sass/base.sass:stylesheets/base.css
```
For directories, run this command in your command line tool (CLI):
```
sass --watch sass:stylesheets
```
The output in your cli would be like this:

```
>>> Sass is watching for changes. Press Ctrl-C to stop.
      write stylesheets/base.css
      write stylesheets/base.css.map
sass sass>>> Change detected to: sass/base.sass
      write stylesheets/base.css
      write stylesheets/base.css.map
```

##### 6. Create a file in the sass directory called 'base.sass' with:

```
touch sass/base.sass
```

##### 7. Add following code into the 'base.sass' file.

```
$font-default: Arial, sans-serif
$default-color: #222

body
  font: 100% $font-default
  color: $default-color
```
Explanation: The elements `$font-default`and `$default-color` are called `variables` and can be named as you like, they are not reserved terms. It is recommended to call the variables precisely and understandable, so they can be easy to remember.

##### Compile the 'base.sass' file of the 'sass' directory into a new css-file in the 'stylesheets' directory with:

```
sass sass/base.sass stylesheets/base.css
```

Explanation: After you have compiled the base.sass file you should see this code in the file `base.css` of the stylesheets folder:

```
body {
  font: Arial, sans-serif;
  color: #222; }

/*# sourceMappingURL=base.css.map */
```

You may have recognized that there is a another new file automatically added to the stylesheets folder called `base.css.map`? This file is very helpful to keep track of the original files as your project grows and becomes more complex.


That's it. That's all you need to know for now to compile a stylesheet with sass. :)
