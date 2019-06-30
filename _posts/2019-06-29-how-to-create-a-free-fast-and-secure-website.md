---
layout: post
title: "How to Create a Free, Fast and Secure Website with Jekyll and GitHub Pages"
categories: web-design
---

A [static website](https://en.wikipedia.org/wiki/Static_web_page) has noteworthy [advantages](https://dzone.com/articles/6-reasons-why-you-should-go-for-a-static-website) over a dynamic one, like improved performance and security.

Here is a simple (and [opinionated]({{ site.baseurl }}{% post_url 2019-06-27-about-this-blog-disclaimer %})) way to build a static website, with [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://pages.github.com/).

# Step 1: Create the repository

Create a new repository named `username.github.io`, where username is your GitHub username, and clone it:

```shell
git clone https://github.com/username/username.github.io.git
```

# Step 2: Create the bare minimum website structure

You can create a Jekyll GitHub Pages website with just a simple text editor, without being necessary to install any additional software on your computer ([Ruby](https://www.ruby-lang.org/en/downloads/), [Jekyll](https://jekyllrb.com/), [Bundler](https://bundler.io/)).

Here is an example using the default Jekyll theme, [minima](https://github.com/jekyll/minima), which is also one for the [supported GitHub themes](https://pages.github.com/themes/). Note that the pages in this example are created in [Markdown](https://en.wikipedia.org/wiki/Markdown), with [front matter](https://jekyllrb.com/docs/front-matter/).

Create the files:

```shell
cd username.github.io
touch _config.yml index.md about.md
```

with the following content:

**_config.yml** - the Jekyll configuration file, in YAML format
```
theme: minima

title: Simple GitHub Pages website with Jekyll
author: your_name
description: >
  This is a simple GitHub Pages website with Jekyll

show_excerpts: false

minima:
  date_format: "%Y-%m-%d"

twitter_username: your_username
github_username: your_username
rss: rss

plugins:
 - jekyll-feed
 - jekyll-seo-tag
```

**index.md** - the homepage of your website
```
---
layout: home
---
```

**about.md** - the about page
```
---
layout: page
title: About
permalink: /about/
---

A simple GitHub Pages website with Jekyll.
```

# Step 3: Push the files to GitHub

Although is recommended to test on your local computer before pushing the changes to GitHub, if you're impatient (and followed the above steps), you can now push the newly created files and see your blog live at https://username.github.io

```shell
git add _config.yml index.md about.md
git commit
git push
```

# Step 4: Add the first blog post

Create the first blog post:

```shell
mkdir _posts
cd _posts
touch 2019-06-30-first-blog-post.md
```

with some content, like [the standard Lorem Ipsum passage, used since the 1500s](https://www.lipsum.com/):

```
---
layout: post
title: "First Blog Post"
categories: web
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore
eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt
in culpa qui officia deserunt mollit anim id est laborum.
```

# Step 5: Add more files

Here are some recommended files for any git repository:

[.gitignore](https://help.github.com/en/articles/ignoring-files) - customize it for your needs
```
# local bundle/gems install
.bundle

# gemfile - used for local testing
Gemfile
Gemfile.lock

# generated site
_site

# on macOS
.DS_Store
```

[.editorconfig](https://editorconfig.org/)
```
root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 2
indent_style = space
insert_final_newline = true
trim_trailing_whitespace = true
```

**README.md** - file that usually holds the description of the git repository content
```
Simple GitHub Pages site with Jekyll
====================================

A simple GitHub Pages site with Jekyll.
```

# Step 6: Customize the theme

With gem-based themes, some of the site’s directories (such as the assets, _layouts, _includes, and _sass directories) are stored in the theme’s gem, hidden from your immediate view. Yet all of the necessary directories will be read and processed during Jekyll’s build process.

You can [customize](https://jekyllrb.com/docs/themes/#overriding-theme-defaults) the default theme, [minima](https://github.com/jekyll/minima), but pay attention to the theme [version](https://github.com/jekyll/minima/releases):

```
open $(bundle show minima)
```

# Step 7: Test the website locally

You can set up a local version of your Jekyll GitHub Pages website by creating a Gemgile with the github-pages gem and test your website locally.

The Gemfile and Gemfile.lock files are used by Bundler to keep track of the required gems and gem versions you need to build your Jekyll website.

Install Jekyll and Bundler:

```shell
gem install --user-install bundler jekyll
```

Then, create the Gemfile:

```
touch Gemfile
echo "source 'https://rubygems.org'" >> Gemfile
echo "gem 'github-pages', group: :jekyll_plugins" >> Gemfile
bundle install --path .bundle
bundle exec jekyll serve
```

Now you can browse your website locally at http://127.0.0.1:4000

By the way, from time to time, make sure you have the updated version of the gems:

```shell
bundle update
```

That's all folks!

# Reference

- [GitHub Pages Basics](https://help.github.com/en/categories/github-pages-basics)
- [Further reading on GitHub Pages](https://help.github.com/en/articles/further-reading-on-github-pages)
- [Writing on GitHub](https://help.github.com/en/categories/writing-on-github)
- [Jekyll - GitHub Pages](https://jekyllrb.com/docs/github-pages/)
- [Jekyll - Themes](https://jekyllrb.com/docs/themes/)
- [Jekyll - Posts](https://jekyllrb.com/docs/posts/)
