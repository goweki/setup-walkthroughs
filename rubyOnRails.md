# `Ruby on Rails` Environment Setup Guide

This guide will walk you through the steps required to set up a Ruby environment on your system using `rbenv` and `ruby-build`. The last step sets up the Rails web application framework.

## Table of Contents

- [Dependencies](#step-1-dependencies)
- [Install `rbenv` and `ruby-build`](#step-2-install-rbenv-and-ruby-build)
- [Add `rbenv` to System PATH`](#step-3-add-rbenv-to-system-path)
- [Install Ruby](#step-4-install-ruby)
- [Install Rails](#step-5-install-rails)

## Prerequisites

Some steps will require sudo privileges on your system.

## Step 1: Dependencies

First, update the package index and install the packages required for the `ruby-build` tool to build Ruby from source:

```bash
sudo apt-get remove ruby
sudo apt update
sudo apt install git curl libssl-dev libreadline-dev zlib1g-dev autoconf bison build-essential libyaml-dev libreadline-dev libncurses5-dev libffi-dev libgdbm-dev
```

These packages provide the necessary dependencies to compile Ruby from source.

## Step 2: Install `rbenv` and `ruby-build`

Next, install both `rbenv` and `ruby-build` by running the following command:

```bash
curl -sSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-installer | bash -
```

This command will download 'rbenv' and 'ruby-build' from the github repo and install them into your system.

## Step 3: Add `rbenv` to System PATH

To make `rbenv` available in your shell, you need to add `$HOME/.rbenv/bin` to your system's `PATH`. If you are using Bash, run the following commands:

```bash
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

- The first command adds `rbenv` to your `PATH` by appending it to your `~/.bashrc` file.
- The second command configures your shell to initialize `rbenv` whenever a new terminal session starts.
- The third command reloads your `~/.bashrc` file to apply the changes immediately.

## Step 4: Install Ruby

Install Ruby version 3.1.2

```bash
rbenv install 3.1.2
```

List all available Ruby versions (installed &) you can use:

```bash
rbenv install -l
```

Set Ruby version 3.1.2 as the default (global) Ruby version for the system:

```bash
rbenv global 3.1.2
```

To verify that Ruby was properly installed, print out the Ruby version number

```bash
ruby -v
```

## Step 5: Install Rails

Many popular UNIX-like OSes ship with an acceptable version of `SQLite`. On Windows, if you installed Rails through Rails Installer, you already have SQLite installed. Others can find installation instructions at the [SQLite website](https://www.sqlite.org/). Verify that it is correctly installed and in your PATH:

```bash
sqlite3 --version
```

The program should report its version.

To install Rails, use the gem install command provided by RubyGems:

```bash
gem install rails
```

To verify that you have everything installed correctly, you should be able to run the following:

```bash
rails --version
```
