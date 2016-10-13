## The hacklang.org landing page content

This directory will contain the landing page and other documentation for [hacklang.org](http://hacklang.org). It will contain links to the [Hack user documentation over at docs.hhvm.com](http://docs.hhvm.com/hack) and other relevant places. [hacklang.org](http://hacklang.org) will be hosted on GitHub pages.

### Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for details on how to add or modify content.

### Run the Site Locally

The requirements for running a GitHub pages site locally is described in [GitHub help](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/#requirements). The steps below summarize these steps.

> If you have run the site before, you can start with step 1 and then move on to step 5.

1. Ensure that you are in the root directory of the hacklang.org repo (i.e., the same directory where this `README.md` exists). The below RubyGems commands, etc. must be run from there.

1. Make sure you have Ruby and [RubyGems](https://rubygems.org/) installed.

   > Ruby >= 2.2 is required for the gems. On the latest versions of Mac OS X, Ruby 2.0 is the
   > default. Use `brew install ruby` (or your preferred upgrade mechanism) to install a newer
   > version of Ruby for your Mac OS X system.

1. Make sure you have [Bundler](http://bundler.io/) installed.

    ```
    # may require sudo
    gem install bundler
    ```
1. Install the project's dependencies

    ```
    # run this in the 'docs' directory
    bundle install
    ```

    > If you get an error when installing `nokogiri`, you may be running into the problem described
    > in [this nokogiri issue](https://github.com/sparklemotion/nokogiri/issues/1483). You can
    > either `brew uninstall xz` (and then `brew install xz` after the bundle is installed) or
    > `xcode-select --install` (although this may not work if you have already installed command
    > line tools).

1. Run Jekyll's server.

    - On first runs or for structural changes to the documentation (e.g., new sidebar menu item), do a full build.

    ```
    bundle exec jekyll serve --config=_config.yml,_config_local_dev.yml
    ```

    - For content changes only, you can use `--incremental` for faster builds.

    ```
    bundle exec jekyll serve --config=_config.yml,_config_local_dev.yml --incremental
    ```

    > We use `bundle exec` instead of running straight `jekyll` because `bundle exec` will always use the version of Jekyll from our `Gemfile`. Just running `jekyll` will use the system version and may not necessarily be compatible.

    > The `_config_local_dev` file overrides some URL settings that you might be using in production to allow you to test links, etc. locally.

1. Either of commands in the previous step will serve up the site on your local device at http://127.0.0.1:4000/ or http://localhost:4000.

### Updating the Bundle

The site depends on Github Pages and the installed bundle is based on the `github-pages` gem.
Occasionally that gem might get updated with new or changed functionality. If that is the case,
you can run:

```
bundle update
```

to get the latest packages for the installation.
