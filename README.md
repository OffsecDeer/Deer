# Deer

Deer is a customized version of the [Crab](https://github.com/thomasheller/crab) theme for the [Hugo](https://gohugo.io) static
site generator.

It was modified to satisfy my needs for my own blog and is not part of the official list of Hugo's themes (not yet, maybe when I've completed it). If you want a preview you can take a look at my [blog](https://offsecdeer.gitlab.io) or use the example website provided in the repo, which is a direct copy from the example website included in the original Crab theme.

## Features
All the original features from Crab are supported:
- responsive
- nested menus
- two-column
- tag support
- blog articles

New features (more to be added in the future):
- better looking table of contents
- code highlighting with [Prism.js](https://prismjs.com/)
- do the relaxing dark colors count?
- description property in the front matter of posts for arbitrary content in list pages
- includes built-in disqus partial layout

## Installation

Install Hugo:

```sh
$ mkdir $HOME/src
$ cd $HOME/src
$ git clone https://github.com/gohugoio/hugo.git
$ cd hugo
$ go install
```

Create a new site:

```sh
$ hugo new site
$ cd path/to/your/site
```

Clone the theme:

```sh
$ git clone https://github.com/OffsecDeer/Deer themes/deer
```

Or add it as a git submodule if your site is already a git repository:

```sh
$ git submodule add https://github.com/OffsecDeer/Deer themes/deer
```

Set the theme from your config.toml file:

```
theme = "deer"
```

Test it out:

```
$ hugo server
```

To update the theme to the latest version, simply pull in the changes:

```sh
$ git -C themes/deer pull
```

To remove the theme follow these steps:

```sh
$ git submodule deinit -f -- themes/deer
$ rm -rf .git/modules/themes/deer
$ git rm -f a/submodule

```

## Menus

- Use the `weight` attribute to specify the order of menu items.
  Menu items with smaller numbers appear before those with bigger
  numbers.
- For every menu, specify an `identifier` if you intend the menu to
  have sub-items. In each sub-item, make sure the `parent` attribute
  matches the value of the `identifier` used for the parent menu.
- Choose a unique `name` for each item in the same menu.

## Two-column layout

Look at the `exampleSite/content/home.md` file for a sidebar example.
If you put a shortcode like this at the beginning of your content
file, the summary will appear in the right column:

```md
{{% summary %}}
This appears in the sidebar. *Markdown* is supported and so are images!
{{% /summary %}}
```

## Tags

Tags are supported as [taxonomies described in the Hugo
manual](https://gohugo.io/taxonomies/usage/). Make sure your config
file contains a proper `taxonomies` declaration, like in the
`exampleSite/config.toml`. You can then put tags in the front matter
as usual:

```
+++
title = "A Page With Tags"
tags = [ "Hugo", "theme", "Deer" ]
...
```

Tags will appear both on regular (fixed, static) pages as well as for
blog posts, although they are probably more commonly used with blog
posts.

## Blog

Blog posts are intended to be created in the special directory
`/blog/`. The main difference about blog articles is that the layout
includes the timestamp when they were published (fixed pages don't
show a timestamp by default) and that they appear in the list of blog
articles.

The `exampleSites/config.toml` shows the kind of `permalinks`
declaration required to generate blog posts in the correct place.

## Logo

To change the default logo to your own customised image,
add `logoimage` to `config.toml`, where `logoimage` is the
path inside your site's `static` directory.

