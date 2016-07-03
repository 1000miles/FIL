# Middleman

## Deploy to gh-pages

[Middleman](https://middlemanapp.com/) is a static sites generator for faster front-end development. 

### Install middleman

```
$ gem install middleman
```

#### Initialize your project with middleman:

via middleman only:
```
$ bundle exec middleman init your_project 
```

#### Make your changes and build the files:

```
$ bundle exec middleman build
```

Note: After the build the folder `build` appears in your current directory, this is the directory that delivers all your generated static files to the public. As this is your asset pipeline try to not touch this directory, if not really necessary. By default this directory is in your `.gitignore` file, so it will not be tracked by Github. 

#### Now, to make sure only the static files will be pushed to the gh-pages, we need to prepare a second git repo and branch. Change into the `build` directory:

``` 
$ cd build
```

#### Then create a new branch called `gh-pages` that is disconnected from your project root (parent):
```
$ git checkout --orphan gh-pages
$ git init # initialize the gh-pages branch as a separate repo
```

Note: While the `build` directory is ignored in the `parent repo`, the `build` directory in the `orphan repo` (gh-pages) will be tracked by Github. 

Learn more about it [here](https://help.github.com/articles/creating-project-pages-manually/)

Attention: The Github description is a bit confusing, you don't need to remove everything in the `build` directory. Just push the build directory to Github and make sure it contains an `index.html` file, otherwise the `gh-pages` branch will not appear in your branches tree and your live-website will throw a `404 Page not found` error.

#### Go back to the `project root` and add following to the `Gemfile`:
```
$ gem 'middleman-gh-pages'
```

And run:
```
$ bundle install
```

### Then create a `Rakefile` to use the rake commands:
```
$ cd .. # make sure to be in the project root
$ touch Rakefile
```
### Open the text editor of your choice:
```
$ subl . 

or:
$ atom .
```

#### Put following snippet to your `Rakefile`:

```
require 'middleman-gh-pages'
```

#### Finally, from the project root you can now run following commands:
```
Build files manually:
$ bundle exec rake build # instead of `$ bundle exec middleman build`

Build and publish files without the need to go into the `build` directory:
$ bundle exec rake publish
```

The gem `middleman-gh-pages` will now deploy your commits to gh-pages and deploy the changes live.
