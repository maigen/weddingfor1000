# Wedding for $1000 Web App

This application is written in Ruby using the Rails framework; basic familiarity with both are assumed in this document.

## System dependencies
* Linux OS. Should run on a Mac, too, but this is secondary.
* Ruby. Ruby version and gemset (optional) are specified in the `.ruby-version` and `.ruby-gemset` files. Ruby version managers such as RVM will use these files to select the correct Ruby and gemset, but one could certainly manage this dependency manually, if desired.
* MySQL database. Could probably be swapped out for e.g. Postgres or SQLite, but this is untested.
* Some of the appplication dependencies have c-bindings to various libraries, which are compiled upon install. These libraries need to be installed in order for `bin/setup` to complete successfully. For example, on Ubuntu 14.04, the following will install the required packages:
```
sudo apt-get install build-essential libgmp-dev libmysqlclient-dev nodejs
```

## Getting started

1. Satisfy the system dependencies listed above.
2. Clone the site with git clone and cd into it.
3. Run `bin/setup` to bootstrap the site by installing all internal dependencies and creating and migrating the database.
4. Run `bin/test` to verify everything is working correctly.

## Usage of extra scripts during development

* `bin/setup`.
This script encapsulates the process for ensuring that all dependencies are installed (bundler) and the database schema is in the correct state (rake db:create db:migrate, etc). One would typically generally run this after cloning the site, or pulling fresh changes down from git, etc. Its important to note that this script is idempotent, so it can be run as many times as one likes.

* `bin/test`.
This script encapsulates the process for verifying the correctness of the application. It will precompile all the assets, run the unit tests with Rspec, and then run the acceptance tests in parallel with Cucumber and parallel_tests. Hooking this script up to a CI process is highly recommended. Note that one can also run tests individually with `bin/rspec` and `bin/cucumber`.

