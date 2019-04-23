# RailsGoat [![Build Status](https://api.travis-ci.org/OWASP/railsgoat.png?branch=master)](https://travis-ci.org/OWASP/railsgoat) [![Code Climate](https://codeclimate.com/github/OWASP/railsgoat.png)](https://codeclimate.com/github/OWASP/railsgoat)

RailsGoat is a vulnerable version of the Ruby on Rails Framework from versions 3 to 5. It includes vulnerabilities from the OWASP Top 10, as well as some "extras" that the initial project contributors felt worthwhile to share. This project is designed to educate both developers, as well as security professionals.

## Important Note

These directions have been modified from those on the OWASP official version,
for easier (I think) setup.

## Getting Started

To begin, if you do not have Ruby, and Git I suggest using the docker-compose
setup. If you can setup the application before you arrive at he workshop, that
will help enormously (if only to save bandwidth vs walk-ins).

## Clone this repo

```bash
$ git clone git@github.com:paytonrules/railsgoat.git
```

### Docker Install
To run Railsgoat with Docker you must first have [Docker](https://docs.docker.com/engine/installation/) and [Docker Compose](https://docs.docker.com/compose/install/) installed. Once those dependencies are installed, cd into the Railsgoat directory where you've cloned the code and run. Rails requires Compose **1.6.0** or above and require a Docker Engine of version **1.10.0** or above.

```
#~/code/railsgoat
$ docker-compose build
$ docker-compose run web rails db:setup
$ docker-compose up
...
  Creating railsgoat_web_1
  Attaching to railsgoat_web_1
$
```
Once you see the preceeding message Railsgoat is running on your localhost on port 3000.

Open your favorite browser, navigate to `http://<dockerIP>:3000` and start hacking! The Docker IP is usually `192.168.99.100`. Run `docker-machine env` to verify.

Note: if your container exits with an error, it may be because a server is already running:
```
A server is already running. Check /myapp/tmp/pids/server.pid.
=> Booting Thin
=> Rails 5.0.1 application starting in development on
http://0.0.0.0:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
Exiting
```
In this case, remove that server.pid file and try again. Note also that this file is in your current working directory, not inside the container.

### Non-Docker Install (Mac)

For Mac users I recommend using [asdf](https://asdf-vm.com/#/) to version the
Ruby environment. Assuming you've installed ~asdf~ you can navigate to the
rails-goat directory:

``` bash
asdf plugin-add ruby
asdf install ruby 2.6.1
asdf local ruby 2.6.1
bundle install
```

If you receive an error, make sure you have `bundler` installed:

```bash
gem install bundler
```

Initialize the database:

```bash
bundle exec rails db:setup
```

Start the Thin web server:

```bash
bundle exec rails server
```

Open your favorite browser, navigate to `http://localhost:3000` and start hacking!

### Non-Mac Users

You can use your personal ruby version manager, and follow the directions to get setup. 
I am not a regular Windows or Linux user, so rather than recommending a setup I would 
say that you probably know how to set it up better than I do.


## Contributing


This version of RailsGoat is custom-built for my workshops. If you're looking
to contribute head to the [official repository](https://github.com/OWASP/railsgoat).

Conversion to the OWASP Top Ten 2013 completed in November, 2013.

# License

[The MIT License (MIT)](./LICENSE.md)
