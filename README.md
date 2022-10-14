# [remarkablegames.github.io](https://b.remarkabl.org/games)

[![build](https://github.com/remarkablegames/remarkablegames.github.io/actions/workflows/build.yml/badge.svg)](https://github.com/remarkablegames/remarkablegames.github.io/actions/workflows/build.yml)

[Site](https://b.remarkabl.org/games) of [@remarkablegames](https://github.com/remarkablegames). Built with [Jekyll](https://jekyllrb.com) and hosted on [GitHub Pages](https://pages.github.com).

## Prerequisites

[Ruby](https://www.ruby-lang.org/en/downloads/) 2.7.4:

```sh
ruby --version
```

If your version is behind, you can either install ruby with [rbenv](https://github.com/rbenv/rbenv) or [RVM](https://rvm.io/).

### rbenv

Install and set up rbenv on macOS:

```sh
brew install rbenv
rbenv init
```

Reload or open a new shell:

```sh
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-doctor | bash
rbenv install
rbenv local
```

[Bundler](https://bundler.io/):

```sh
gem install bundler
bundler --version
```

Update bundler:

```sh
bundle update --bundler
```

## Installation

Clone repository:

```sh
git clone https://github.com/remarkablegames/remarkablegames.github.io.git
cd remarkablegames.github.io
```

Install the dependencies:

```sh
bundle install
```

## Update

Update dependencies:

```sh
git checkout master
git pull
bundle update
```

## Run

### Development Server

```sh
bundle exec jekyll serve --livereload # --incremental --limit_posts 1
```

The server will be running at http://127.0.0.1:4000/:

```sh
open http://127.0.0.1:4000/
```

Press `CTRL-C` to stop the server.

### Production Build

```sh
bundle exec jekyll build
```

The site will be generated at `./_site/`.

## Testing

Use [HTMLProofer](https://github.com/gjtorikian/html-proofer) to validate HTML output (see [post](https://remarkablemark.org/blog/2017/01/31/travis-github-pages/)):

```sh
bundle exec jekyll build
bundle exec htmlproofer _site
```

## License

Copyright © remarkablegames
