# Source code for my little online presence

The site is built with jekyll and served by Github pages at
[alvyjudy.github.io](https://alvyjudy.github.io)

It has two pages, home and portfolio, whose files located in the root directory
(`index.html` and `portfolio.html`).

Posts are inside `_posts`.

## Development

To start, make sure `bundler` and `ruby` are installed.

Then, run `bundle update`, which will install the dependency from `Gemfile`.

Afterwards, run `bundle exec jekyll serve --livereload` to spin up the
development server. Or push the master branch to github, which will build
the site and serve it.

To preview draft, run `bundle exec jekyll serve --livereload --drafts`

## Blogging

Each post need the following key value pair in the front matter
```
layout: post
title: 
teaser: |
  optionally
  multi
  paragraph
  text
```