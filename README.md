Repsitory for personal website. 

## Local System
- Machine: Apple Macbook Air (M1, 2020)
- OS: macOS Monterey Version 12.2

## Setup Procedure
1.  Installed [Homebrew:beer:](https://brew.sh)
    ```zsh
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```
2. Used the following script to enable `brew` command 
    ```zsh
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/$USER/.zprofile
    ```
3. Followed the [instructions](https://jekyllrb.com/docs/installation/macos/) to install Jekyll on macOS
    - Because I am using macOS Monterey Version 12.2 which is later than macOS Catalina, run the following to avoid failure of instalation
        ```zsh
        export SDKROOT=$(xcrun --show-sdk-path)`
        ```
    - Installed Ruby by `brew install ruby`
    - Checked shell type by `echo $SHELL`. (The default on macOS is `/bin/zsh`)
    - Tried the following script, but found the terminal was not able to find the newly installed Ruby
        ```zsh
        echo 'export PATH="/usr/local/opt/ruby/bin:/usr/local/lib/ruby/gems/3.0.0/bin:$PATH"' >> ~/.zshrc
        ```
    - Based on the info provided by `brew install ruby`, try the following script and found successful
        ```zsh
        echo 'export PATH="/opt/homebrew/opt/ruby/bin:/opt/homebrew/opt/ruby/gems/3.0.0/:$PATH"' >> ~/.zshrc
        ```
    - Confirmed the ruby version is correct by `ruby -v`
        > ruby 3.0.3p157 (2021-11-24 revision 3fb7d2cadc) [arm64-darwin21]
    - Ran `gem install --user-install bundler jekyll` to install `bundler` and `jekyll` on the user level
    - Found the terminal was not able to find `jekyll` after installation
    - Identified the installed directory is:
        >`/Users/$USER/.local/share/gem/ruby/3.0.0/bin`
    - Based on the info provided by `gem install --user-install bundler jekyll`, tried the following script and found successful (`$USER` is the username of the machine)
        ```zsh
        echo 'export PATH="/Users/$USER/.local/share/gem/ruby/3.0.0/bin:$PATH"' >> ~/.zshrc
        ```
    - Ran `gem env` to check the environment
    - Ran `which jekyll` and `which bundler` to make sure the terminal is calling the right command
4. Built the website locally
    - Forked `minimal-mistake` repo from [mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)
    - Cloned the repo to the local machine
    - `cd` to `Github/minimalbb.github.io/` 
    - Installed the theme by remote theme method following the quick start [guidance](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remote-theme-method)
        - Replaced the contents of `Gemfile` with the following
            ```ruby
            source "https://rubygems.org"
            gem "github-pages", group: :jekyll_plugins
            gem "jekyll-include-cache", group: :jekyll_plugins
            ```
        - Checked `jekyll-include-cache` is in the `plugins` array of `_config.yml`
        - Ran `bundler` to fetch and to update bundled gems
    - Add `remote_theme: "mmistakes/minimal-mistakes@4.24.0"` to `_config.yml` file.
    - Made a commit and push to Github to check if the website appears normally
    - Removed the unnecessary following the [guidance](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remove-the-unnecessary)
        - Ran `defaults write com.apple.Finder AppleShowAllFiles true` and then `killall Finder` to find hidden files and folders on my laptop
    - Changed the `Gemfile` into the following based on the installation [guide](https://mmistakes.github.io/minimal-mistakes/docs/installation/#install-dependencies), but switch `gem "jekyll"` into `gem "github-pages", group: :jekyll_plugins` because I want the local version looks just the same as on GitHub Pages
        ```ruby
        source "https://rubygems.org"

        # Hello! This is where you manage which Jekyll version is used to run.
        # When you want to use a different version, change it below, save the
        # file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
        #
        #     bundle exec jekyll serve
        #
        # This will help ensure the proper Jekyll version is running.
        # Happy Jekylling!

        # gem "github-pages", group: :jekyll_plugins

        # To upgrade, run `bundle update`.

        gem "github-pages", group: :jekyll_plugins
        gem "minimal-mistakes-jekyll"

        # The following plugins are automatically loaded by the theme-gem:
        #   gem "jekyll-paginate"
        #   gem "jekyll-sitemap"
        #   gem "jekyll-gist"
        #   gem "jekyll-feed"
        #   gem "jekyll-include-cache"
        #
        # If you have any other plugins, put them here!
        # Cf. https://jekyllrb.com/docs/plugins/installation/
        group :jekyll_plugins do
        end
        ```
    - Ran `bundle install` again to re-install the dependencies resulted from the modified `Gemfile` above
    - Tried `bundle exec jekyll serve`, but the following error message  showed up

        >GitHub Metadata: No GitHub API authentication could be found. Some fields may be missing or have incorrect data.

    - Found solution in a GitHub [issue](https://github.com/github/pages-gem/issues/399#issuecomment-301827749) and solved the problem. The solution adds `github: [metadata]` into `_config.yml`. It seems like GitHub Pages automatically fetch the metadata, but to test it locally we have to include in the `_config.yml` file
    - Tried `bundle exec jekyll serve` again, but the following error message  showed up

        >bundler: failed to load command: jekyll (/opt/homebrew/lib/ruby/gems/3.0.0/bin/jekyll)

    - Found solution in a stack overflow [page](https://stackoverflow.com/questions/69890412/bundler-failed-to-load-command-jekyll) which points to a GitHub [issue](https://github.com/github/pages-gem/issues/752#issuecomment-764647862). It turned out [Ruby 3.0 no longer commes with a gem called webrick](https://github.com/jekyll/jekyll/issues/8523). So, the solution is to add `gem "werbrick"` into `_config.yml` or to run `bundle add wabrick` in the command line
    - Tried `bundle exec jekyll serve` once again and the command was successful hosting the website locally
    - Based on the [GitHub Docs](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll/#building-your-site-locally), open the browser and navigate to `http://localhost:4000`
    - Successfully test the site locally with Jekyll :tada:

