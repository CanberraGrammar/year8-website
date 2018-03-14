# Year 9 IST Website

This website is written in AsciiDoc and uses [Asciidoctor](http://asciidoctor.org) to convert the `adoc` files into `html` files which are served via GitHub Pages.

The `master` branch of this repo contains the `adoc` source files, along with lots of other supporting files and the build scripts. The `gh-pages` branch contains the rendered HTML5 website which is then served via GitHub Pages and available at http://year9.cgscomputing.com

Travis CI is used to run the `build.sh` script whenever code is pushed to the repo and regenerate the HTML pages for the website.

## Setting up a local development environment

If you intend to fork and provide changes to the source files then you should setup a local development environment so that you can process the `adoc` files locally and check they parse correctly to HTML.

1. Make sure you have Xcode installed and then run the `xcode-select --install` command in order to install the command line tools, which are needed to build the gems. 

2. Install **Bundler** to enable you to manage gems (particuarly, AsciiDoctor) using the command `gem install --user-install bundler`. This will install Bundler under the current user, so you do not need sudo.

3. Install **Jekyll** (the static site generator, the same as used in GitHub pages) using the command `gem install --user-install jekyll`. This will install Jekyll under the current user, so you do not need sudo.

4. Make sure that the path to the local gem install (e.g. `/Users/username/.gem/ruby/2.0.0/bin` is included in the Terminal path. To check, do `echo $PATH`. If it's not included, create a new file called `.bash_profile` in the root of your home folder and add the following lines

    ```bash
    if which ruby >/dev/null && which gem >/dev/null; then
        PATH="$(ruby -rubygems -e 'puts Gem.user_dir')/bin:$PATH"
    fi
    ```
    then restart the Terminal for the changes to take effect.
    
5. Clone the repo to your computer, or (if you intend to submit a pull request) then fork the repo and clone your fork.

6. Run `bundle install --path ~/.gem` to install the required gems - these are defined in the `Gemfile`. Currently the only gem to be installed is the latest development version of AsciiDoctor. You need to define the `--path` otherwise it will install globally (which is okay, but I don't like installing stuff as sudo unless absolutely necessary). It will install into `~/.gem/ruby/<ruby version>/bundler`

7. Run `bundle exec jekyll build` to build the site, which will be build into `_site` (this folder is included in the `.gitignore` file so it won't be commited).

8. Run `bundle exec jekyll serve` to serve the website on localhost port 4000

If you would like more information on forking a repo, and submitting a pull request, then visit this article on  GitHub Help: https://help.github.com/articles/fork-a-repo/