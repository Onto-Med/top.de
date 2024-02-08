<img align="right" width="200" height="200" src="public/logo.svg" alt="TOP">

# TOP Website

[![deploy](https://github.com/Onto-Med/top.de/actions/workflows/deploy.yml/badge.svg)](https://github.com/Onto-Med/top.de/actions/workflows/deploy.yml)
[![License: CC0](https://img.shields.io/badge/license-CC0-blue)](LICENSE)

Live on <https://onto-med.github.io/top.de/>.
This is the website for TOP – a junior research group for [Developing a Terminology and Ontology-based Phenotyping Framework](https://www.gesundheitsforschung-bmbf.de/de/nachwuchsgruppe-entwicklung-eines-terminologie-und-ontologie-basierten-14115.php).
It uses [Hyde layout](https://github.com/poole/hyde/tree/v3), which itself is based on the [Poole theme](https://github.com/poole/poole) for [Jekyll, a static site generator](http://jekyllrb.com/).

## GitHub does everything

All the steps below are *only* necessary if you want to preview or build the page yourself.
GitHub Pages is powered by Jekyll and does all the building and hosting automatically.

## Setup

1. Install Ruby
2. Install Bundler
3. Use Bundler to install the dependencies

### Example for Arch Linux

    $ sudo pacman -S ruby

Add the following to your environment configuration file, such as `.profile` or `.zshrc` and reload (`source ~/.zshrc`) it:

    export GEM_HOME="$(ruby -e 'puts Gem.user_dir')"
    export PATH="$PATH:$GEM_HOME/bin"

Use bundler with the provided Gemfile:

    $ gem install bundler
    $ bundle install

However that resulted in the error `Bundler::GemNotFound: Could not find jekyll-4.2.1.gem for installation` in testing on one machine.

### Example for MacOS (with Homebrew)

Install Ruby:

    $ brew install ruby

Add the brew ruby path to your shell configuration.
If you're using Zsh, add the following lines to `~/.zshrc`

    export GEM_HOME="$(ruby -e 'puts Gem.user_dir')"
    export PATH="$PATH:$GEM_HOME/bin"

Install bundler and the gems:

    $ gem install --user-install bundler
    $ bundle install

## Preview
Switch to the `master` branch and run `bundle exec jekyll serve --incremental`.
Check if everything looks normal.

## Build
The GitHub workflow in `.github/workflows/deploy.yml` automatically builds the master branch and deploys it on the static branch.
To build locally, run `bundle exec jekyll build (--incremental)`, 
This will put the static HTML content into the `_site` folder.

## Deploy
We serve the content of the static branch at the official TOP website <https://top.de> where it needs to be manually updated.
The static branch is also automatically served using GitHub pages at <https://onto-med.github.io/top.de/>.

## Using Docker
If you cannot or do not want to install Ruby and the gems on your system, or there is some problem with Ruby, you can also use the Dockerfile, which should work everywhere.
Use the following commands or execute the associated script.

| goal         | command                                                                   | script                     |
|--------------|---------------------------------------------------------------------------|----------------------------|
| build image  | docker build -t top.de .                                          | scripts/docker-build       |
| preview page | docker run --rm --network="host" top.de                           | scripts/docker-run-preview |
| build page   | docker run --rm -it --volume="$PWD:/usr/src/app" -it top.de build | scripts/docker-run-build   |

## Troubleshooting

### Ruby cannot find the native extensions

#### Exemplary error message

    bundler: failed to load command: jekyll (/home/konrad/.local/share/gem/ruby/3.0.0/bin/jekyll)
    /home/konrad/.local/share/gem/ruby/3.0.0/gems/ffi-1.15.1/lib/ffi.rb:5:in `require': libffi.so.7: cannot open shared object file: No such file or directory - /home/konrad/.local/share/gem/ruby/3.0.0/extensions/x86_64-linux/3.0.0/ffi-1.15.1/ffi_c.so (LoadError)

This can happen if you already built the native extensions (e.g. via `bundle install`) with an older version of Ruby and then upgrade Ruby.
Even `bundle install` will not rebuild the native extensions in that case if they are already present.
To fix this, run `bundle pristine`.
It is also possible that you installed some dependencies using `gem install` system- or user-wide, which bundler will not overwrite by default.
In this case, even `bundle pristine` may not be enough.
In our experience, this can be fixed by deinstalling Ruby, deleting all leftover gem directories and reinstalling Ruby afterwards.

### Preview URL not working in MacOS using Docker

Docker may run in it's own virtual machine under MacOS and not thus not forward `--network="host"` to the network of the machine itself.
While the default way of port mapping in Docker using the `-p 4000:4000` gets forwarded to the local host under MacOS, this does not work with the underlying Jekyll server of this website.
Thus, there may not be a way to preview the docker build using `jekyll serve` on MacOS.
However you can still build it using Docker and use a local webserver to preview the _site folder.

### Online Editing---Directly on Master
If you want to change content in a page on the website and your GitHub account has the required rights, you can log in to GitHub and edit the content using the pen symbol ("Edit this file") in one of the files, for example [index.md](https://github.com/Onto-Med/top.de/blob/master/index.md) for the home page.
GitHub will give you a basic idea of how it will turn out in the "Preview" tab next to "Edit file", however it will not include any of the styling of Jekyll, so the layout will be broken and there is no sidebar but you can at least see the text.
Then you can commit the changes to the master branch.
Normally you should always make sure that the master branch is in a functioning state, which you can't preview, but if you don't have any other option and you only make small textual changes it is relatively low risk.
There are automatic actions in place that will now build the website and deploy it on the ["static" branch](https://github.com/Onto-Med/top.de/tree/static) as HTML.
When the [actions are successfully finished (green checkmark)](https://github.com/Onto-Med/top.de/actions), the page is automatically published on GitHub pages at <https://onto-med.github.io/top.de/>, where you can check if everything is working as expected.
Then someone with access to the server can do a `git pull` of the static branch.
It is also possible to circumvent the server entirely and [point a domain to GitHub pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site), however then you can't check between build and deploy.

### Online Editing---Pull request
If you don't have edit rights, you can instead choose to create a pull request.
This is also good if you want to edit multiple files, such as an image and it's refering text, because then those with write access can perform a squash merge to combine your changes into a single commit.

Delete and add images in the `public` folder as needed, change content in the appropriate `.md` files.

1. Perform the first change on the website and create a pull request in a new branch with a note to not merge it yet.
2. Perform the other changes on the website on the same branch.
3. Use a "Squash Merge" to combine all commits into one into the master branch and delete the temporary branch.
4. Wait until the [build and deploy actions](https://github.com/Onto-Med/top.de/actions) are finished, then check <https://onto-med.github.io/top.de/> if everything is correct.
5. Update the repository on the server.

### GitHub Desktop
You can also use the [GitHub Desktop client on Windows](https://desktop.github.com/).
Modify the files using your normal tools like a file explorer and text editor and then commit the changes to the master branch.

### Preview on Windows
There may be a more elegant way to accomplish this, if you know one, please create a pull request or an issue.
Needs the Windows package manager `winget` on your system.

    winget install RubyInstallerTeam.RubyWithDevKit

Open a terminal as administrator

	ridk install

Start `gem`, it will tell you a path for your gemfiles.
Open a new terminal so that the `gem` command is available.
Add that path your PATH environment variable but replace the slashes '/' with backslashes '\'.

Open a new terminal in your project directory, e.g. using GitHub Desktop.

	gem install --user-install bundler
	bundle install

Then you should be able to run `bundle exec jekyll serve --incremental`, which shows a link like <http://127.0.0.1:4000> that you can enter in the browser to preview the page.
