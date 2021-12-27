---
description: >-
  A short walkthrough of how to setup GitHub pages for local editing and some
  references of similar GitHub based websites and portals.
---

# GitHub Pages

## Running Jekyll For Local Editing:

### Installation:

Before we install Jekyll, we need to make sure we have all the required dependencies.

```text
sudo apt-get install ruby-full build-essential zlib1g-dev
```

It is best to avoid installing Ruby Gems as the root user. Therefore, we need to set up a gem installation directory for your user account. The following commands will add environment variables to your `~/.bashrc` file to configure the gem installation path. Run them now:

```text
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Finally, install Jekyll:

```text
gem install jekyll bundler
```

That’s it! You’re ready to start using Jekyll.

### Usage:

```text
cd <cloned-github-directory>
```

```text
$ bundle exec jekyll serve
> Configuration file: /Users/octocat/my-site/_config.yml
>            Source: /Users/octocat/my-site
>       Destination: /Users/octocat/my-site/_site
> Incremental build: disabled. Enable with --incremental
>      Generating...
>                    done in 0.309 seconds.
> Auto-regeneration: enabled for '/Users/octocat/my-site'
> Configuration file: /Users/octocat/my-site/_config.yml
>    Server address: <http://127.0.0.1:4000/>
>  Server running... press ctrl-c to stop.
```

To preview your site, in your web browser, navigate to [**http://localhost:4000**](http://localhost:4000)**.**

### Reference Links:

* [https://github.com/techfolios/template](https://github.com/techfolios/template)
* [http://techfolios.github.io/quickstart.html](http://techfolios.github.io/quickstart.html)
* [https://github.com/YoussefRaafatNasry/portfolYOU](https://github.com/YoussefRaafatNasry/portfolYOU)

