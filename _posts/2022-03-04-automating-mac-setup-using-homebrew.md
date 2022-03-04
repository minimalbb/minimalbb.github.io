---
title: "Automating Mac Setup using Homebrew"
date: 2022-03-04T00:40:00-06:00
categories:
  - blog
tags:
  - Shell
  - Homebrew
toc_sticky: false
---

My shell script used to automate the setup process using [Homebrew]:beer: can now be found on my [mac-setup-homebrew] GitHub repository. To be specific, the script do the following things:

1. Install `brew`
2. Set environment for `brew`
3. Update `brew`
4. Install [Homebrew Cask]
5. Install programming languages, tools and apps, etc

No clicking, no dragging, no dropping. Check README for the complete list of tool it installs.

[Homebrew]: https://brew.sh "https://brew.sh"
[mac-setup-homebrew]: https://github.com/minimalbb/mac-setup-homebrew "https://github.com/minimalbb/mac-setup-homebrew"
[Homebrew Cask]: https://github.com/Homebrew/homebrew-cask