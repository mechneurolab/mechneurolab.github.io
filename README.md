# mechneurolab.github.io - Open Source @ GitHub 

This is a basic static website (Built with Jekyll) to higlight the open sourece and open science projects of the Mechanical Neuroimaging Lab at the University of Delaware. Click [here](https://mechneurolab.github.io) to check out the live version.

---

## Requirements to build and update the website

- Clone this repository. We recommend forking to your namespace and using pull requests to modify the active github.io website.
- (On macOS) Install [homebrew](https://brew.sh)
- Install [Jekyll](https://jekyllrb.com) on your local machine.

### Install Jekyll on macOS
    # install the command line tools
    xcode-select --install

    # Add the following lines to your ~/.zshrc file
    export SDKROOT=$(xcrun --show-sdk-path)

    # Install rbenv and ruby-build
    brew install rbenv

    # Set up rbenv integration with your shell
    rbenv init

    # Check your installation
    curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash

    # Update .zshrc to use rbenv every time
    printf 'eval "$(rbenv init - zsh)"\n' >> ~/.zshrc

    # Install ruby 3.1.1 and set to run from terminal by default
    rbenv install 3.1.1
    rbenv global 3.1.1

    # Use correct gem path for the ruby version
    printf 'export PATH="$HOME/.gem/ruby/3.1.0/bin:$PATH"\n' >> ~/.zshrc

    # Install bundler and Jekyll to your machine
    gem install --user-install bundler jekyll

## Working with the repository

The basic workflow is to make a change to the markdown files or configuration files of the page, preview the changes locally with `bundler exec jekyll serve`. Once the page looks appropriate, you can merge the code into the lab repository via a pull request. Once the code is in the main laboratory repository, it will be automatically redeployed to the live page via [GitHub Actions](https://github.com/features/actions).

### Basic steps in creating a new project page

- Copy and rename a new markdown file in the `/_projects` folder
- Edit the page with the documentation. An example of a `new_project.md` file is below
  
```Markdown
---
title: "INSERT TITLE OF PROJECT HERE"
excerpt: "Excerpt to be displayed on projects listing page"
header:
  teaser: /assets/images/fileToDisplayOnProjectPage.png
---

{% include figure image_path="/assets/images/elastome.png" alt="This " %}

Markdown text that describes the project goes here. This will be rendered on the individual project page.

Here's an HTML link<a href="https://onlinelibrary.wiley.com/doi/full/10.1002/hbm.25192">

And this is a button with

[<i class='fab fa-github-square'></i> Visit MRE134 GitHub repository](https://github.com/mechneurolab/mre134){: .btn .btn--primary}
```

- Preview the page with `bundle exec jekyll serve` viewing the page via a web browser at the IP and port listed. Note that changes to `_config.yml` will only be reflected by stopping jekyll with Ctrl-C and rerunning `bundle exec jekyll serve`
- Merge the changes into the main [mechneurolab repository](https://github.com/mechneurolab.github.io) via a pull request.

## Resources and acknowledgements

If you have a question about using Jekyll, start a discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll). Other resources:

- [Minimal Mistakes template used for this project](https://github.com/mmistakes/minimal-mistakes)
  - [HTML Tags and formatting built into minimal mistakes](https://mmistakes.github.io/minimal-mistakes/markup/markup-html-tags-and-formatting/)
  - [Minimal Mistakes Documentation](https://mmistakes.github.io/minimal-mistakes/)
- [Jekyll: Static Site Generator](https://jekyllrb.com)
- [Ruby 101](https://jekyllrb.com/docs/ruby-101/)
- [Setting up a Jekyll site with GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Configuring GitHub Metadata](https://github.com/jekyll/github-metadata/blob/master/docs/configuration.md#configuration) to work properly when developing locally and avoid `No GitHub API authentication could be found. Some fields may be missing or have incorrect data.` warnings.
