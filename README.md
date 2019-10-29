# [remarkablegames.github.io](https://b.remarkabl.org/games)

[Site](https://b.remarkabl.org/games) of [@remarkablegames](https://github.com/remarkablegames). Built with [Jekyll](https://jekyllrb.com) and hosted on [GitHub Pages](https://pages.github.com).

## Requirements

[Ruby](https://www.ruby-lang.org/en/downloads/) 2+:

```sh
$ ruby --version
```

[Bundler](http://bundler.io/):

```sh
# gem install bundler
$ bundler --version
```

## Installation

Clone the repository:

```sh
$ git clone https://github.com/remarkablegames/remarkablegames.github.io.git
$ cd remarkablegames.github.io
```

Then install gem dependencies:

```sh
$ bundle install
```

## Update

To update the gem dependencies:

```sh
# git checkout master
$ git pull
$ bundle update
```

## Run

### Development server

```sh
$ bundle exec jekyll serve --livereload # --incremental --limit_posts 1
```

The server will be running at http://127.0.0.1:4000/:

```sh
$ open http://127.0.0.1:4000
```

Press `CTRL-C` to stop the server.

### Production build

```sh
$ bundle exec jekyll build
```

The site will be generated at `./_site/`.

## Testing

Use [HTMLProofer](https://github.com/gjtorikian/html-proofer) to validate HTML output (see [post](https://remarkablemark.org/blog/2017/01/31/travis-github-pages/)):

```sh
$ bundle exec jekyll build
$ bundle exec htmlproofer _site
```

## License

Copyright © remarkablegames
