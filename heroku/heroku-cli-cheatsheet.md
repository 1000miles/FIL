# Heroku CLI Cheatsheet

Reference: https://devcenter.heroku.com/articles/heroku-cli-commands

## 1. Login/Logout

### Login/Logout to/from Heroku from your Terminal shell

```zsh
# Get your heroku username and password ready
$ heroku login
$ heroku logout
```

## 2. Run commands

### Run herokuapp locally

```zsh
USAGE
  $ heroku local [PROCESSNAME]

OPTIONS
  -e, --env=env            location of env file (defaults to .env)
  -f, --procfile=procfile  use a different Procfile
  -p, --port=port          port to listen on

DESCRIPTION
  Start the application specified by a Procfile (defaults to ./Procfile)

ALIASES
  $ heroku local:start

EXAMPLE
  $ heroku local
  $ heroku local web
  $ heroku local web=2
  $ heroku local web=1,worker=2
```

### Run a one-off command

```zsh
$ heroku local:run bin/migrate
```

### Navigate to the project folder, run Heroku command line tool (CLI) in the shell

```zsh
$ heroku run bash
```

### Run node in project folder

```zsh
$ heroku run node path-to-file

# Example:
$ heroku run node bin/seed.js
```

## 3. Configuration

### Get heroku configs of an app

```zsh
$ heroku config
```

### Create a new app on heroku

```zsh
$ heroku apps:create
```

### Show detailed app information

```zsh
$ heroku apps:info
```

### Rename an app

```zsh
$ heroku apps:rename NEWNAME
```

### Show list of available apps

```zsh
$ heroku apps:stacks

 ▸    heroku-cli: update available from 6.13.19 to 6.99.0-ec9edad
=== ⬢ mind-the-board Available Stacks
* heroku-18
  heroku-16
  cedar-14
  container
```

### Adds a git remote to an app repo

```zsh
$ heroku git:remote
```

## 4. Errors/Logs

## View App Errors

```zsh
$ heroku apps:errors
```

### Display recent log output

```zsh
$ heroku logs

$ heroku logs -t # Stream logs
```

## 5. Database

### Show database info

```zsh
  $ heroku pg [DATABASE]
```

### Show current database settings

```zsh
$ heroku pg:settings [DATABASE]
```

### Delete all data in database

```zsh
$ heroku pg:reset [DATABASE]
```

## 6. Pipeline

### Setup pipeline

```zsh
$ heroku pipelines:setup [NAME] [REPO]

# Example:
$ heroku pipelines:setup example githuborg/reponame -o example-org
```

### List pipelines you have access to

```zsh
$ heroku pipelines
```

### Connect a github repo to an existing pipeline

```zsh
$ heroku pipelines:connect [NAME]

# Example:
$ heroku pipelines:connect example -r githuborg/reponame
```

### Create a new pipeline

```zsh
$ heroku pipelines:create [NAME]

# Example:
$ heroku pipelines:create -a example-staging
```

### Destroy pipeline

```zsh
$ heroku pipelines:destroy PIPELINE

# Example:
$ heroku pipelines:destroy example
```

### Compares the latest release of this app to its downstream app(s)

```zsh
$ heroku pipelines:diff

OPTIONS
  -a, --app=app        (required) app to run command against
  -r, --remote=remote  git remote of app to use

EXAMPLES
  $ heroku pipelines:diff --app murmuring-headland-14719
```

### Show list of apps in pipeline

```zsh
$ heroku pipelines:info PIPELINE

# Example:
$ heroku pipelines:info example
```

## 7. Buildpacks

### Show buildpacks

```zsh
$ heroku buildpacks

 ▸    heroku-cli: update available from 6.13.19 to 6.99.0-ec9edad
=== mind-the-board Buildpack URL
heroku/nodejs
```

### Add new app buildpack to project

```zsh
$ heroku buildpacks:add BUILDPACK
```

### Fetch info about a buildpack

```zsh
$ heroku buildpacks:info BUILDPACK
```

### Clear all buildpacks set on the app


```zsh
$ heroku buildpacks:add BUILDPACK
```

### Remove a buildpack set on the app

```zsh
$ heroku buildpacks:remove [BUILDPACK]
```

### Search for a buildpack

```zsh
$ heroku buildpacks:search [TERM]
```

### Set buildpacks

```zsh
$ heroku buildpacks:set BUILDPACK
```

### List versions of a buildpack

```zsh
$ heroku buildpacks:versions BUILDPACK
```

## 8. Authentication

### Output your current CLI authentication token

```zsh
$ heroku auth:token
```

### Display the current logged in user

```zsh
$ heroku whoami
```

### List oAuth authorizations

```zsh
$ heroku authorizations
```

### Create a new oAuth authorization

```zsh
$ heroku authorizations:create
```

### Show, revoke or update an existing oAuth authorization

```zsh
$ heroku authorizations:info ID # show
$ heroku authorizations:revoke ID # revoke
$ heroku authorizations:update ID # update

$ heroku authorizations:rotate ID # update oAuth authorization token
```

## 9. Certifications

### List certificates for an app

```zsh
$ heroku certs
```

### Add an SSL certificate to an app

```zsh
$ heroku certs:add CRT KEY

EXAMPLES
  $ heroku certs:add example.com.crt example.com.key
```

### Generate a key and a CSR or self-signed cert

```zsh
$ heroku certs:generate example.com
```

### Show cert information for an SSL cert

```zsh
$ heroku certs:info
```

### Print the correct key for the given certificate

```zsh
$ heroku certs:key example.com.crt example.com.key
```

### Remove an SSL cert from an app

```zsh
$ heroku certs:remove
```

### Generate 2fa recovery codes

```zsh
$ heroku auth:2fa:generate-recovery-codes
```

### Adds an SSH key for a user

```zsh
$ heroku keys:add /my/key.pub
```

### Remove an SSH key from the user

```zsh
$ heroku keys:remove email@example.com
```

### Remove all ssh keys for current user

```zsh
$ heroku keys:clear
```

## 10. Git

### Show all git remotes (on Github and Heroku)

```zsh
$ git remote -v
```

### Create a new heroku app

```zsh
$ heroku create
```

### Set git remote heroku to heroku app url

```zsh
$ heroku git:remote -a thawing-inlet-61413
```

### Rename heroku git remote

```zsh
$ git remote rename heroku heroku-staging
```

### Deploy to heroku master branch

```zsh
$ git push heroku master
```

### Deploy to another branch than heroku master

```zsh
$ git push heroku testbranch:master
```

### Deploy with `-f` force flag to avoid deployment conflicts

```zsh
$ git add -A
$ git commit -m "heroku deployment message"
$ git push -f heroku
```

## SSH Git

### Configure to use ssh with Heroku globally

```zsh
# Example
$ git config --global url.ssh://git@heroku.com # instead of https://git.heroku.com
```

### Remove ssh with Heroku globally

```zsh
$ git config --global --remove-section url.ssh://git@heroku.com/
```
