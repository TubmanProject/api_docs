# Tubman Project API Documentation

The Tubman Project API is a web service that exposes endpoints available for interacting with the Tubman Project.  This repository contains the source code for the Tubman Project API's documentation.  Documentation for the Tubman Project's API is powered by [Slate](https://github.com/lord/slate).

# Installation

Reference the [Getting Started with Slate](https://github.com/lord/slate#getting-started-with-slate) section of the, "Slate API Docs Generator," for detailed installation instructions.

## Prerequisites

For local development the following is needed:

* **Vagrant** - Download and install vagrant from <https://www.vagrantup.com/downloads.html>
* **Linux or OSx** - Ubuntu 16.04 is installed automatically when developing locally with Vagrant
* **Ruby, version 2.3.1 or newer**
* **Bundler** - Run `gem install bundler` if the `bundle` command doesn't work

## Getting Started

1. Fork this repository on GitHub.
2. Clone *your forked repository* to your hard drive with `git clone https://github.com/YOURUSERNAME/api_docs.git`
3. `cd /path/to/forked/repository` - *Hint: this directory will have a file called `Vagrantfile`*
4. Start slate by running the command `vagrant up`

After following the above steps the API documentation should be available to view at <http://localhost:4567>

# Usage

Reference the [Slate wiki](https://github.com/lord/slate/wiki) for instructions that describe editing of these API docs.  

The `source/` directory contains the [Markdown](https://daringfireball.net/projects/markdown/) files and static assets the must be edited in order to edit these API docs.  

The paths to static assets are set in the `config.rb` file at the root of this project.  The following section of `config.rb` must be updated to change the path of static assets:

```
# Assets
set :css_dir, 'static/assets/css'
set :js_dir, 'static/assets/javascript'
set :images_dir, 'static/assets/images'
set :fonts_dir, 'static/assets/fonts'
```

The Tubman Project API docs take advantage of Slate's [include](https://github.com/lord/slate/wiki/Using-Includes) feature in order to minimize the size of `index.html.md`.  Each endpoint is documented using a markdown file in the `source/includes/` directory and is added to the API documentation by adding it to the *includes* section of `index.html.md`.  See below for an example:

```
includes:
  - dispositions
  - filings
  - fields
  - errors
```

To publish static files that can be deployed to a server run `bundle exec middleman build --clean` to build the website into the project's `build/` directory.  Further details can be found at [Deploying Slate](https://github.com/lord/slate/wiki/Deploying-Slate) on the Slate wiki.  

# Contributing

The Tubman Project is a volunteer effort. We encourage you to contribute and [join the team](http://www.tubmanproject.com)

A great place to start contributing is to check out and tackle one of our [Issues](https://github.com/tubmanproject/api_docs/issues).

# Credits

* [Slate](https://github.com/lord/slate)

# License

See the LICENSE file in the root directory of this project.
