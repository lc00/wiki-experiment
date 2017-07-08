## Commands

* `jekyll build` - Build site
* `jekyll serve` - Serve on localhost:4200
* `--drafts` - Include drafts

## Pages

Can either include it by name in the root, or as a folder with an index file. Using a folder will hide the extension.

## Posts

Name format = `yyyy-mm-dd-title.md`

## Start items with:

```yaml
---
layout: <layout>
title: <title>
date: <YYYY-MM-DD HH:MM:SS>
categories: <one two>
tags: <one two>
permalink: </permalink-goes-here>
---

Post content goes here
```

## Programming

* `{{variableNameHere}}`
* `{{site.variable_name}}`
    * `time`
    * `pages`
    * `posts`
    * `related_posts`
    * `static_files`
    * `html_pages`
    * `collections`
    * `data.<file_name>.<variable>`
    * `documents`
    * `categories.<category>`
    * `categories.<tag>`
    * `<custom` variable from _config.yml>
* `{{page.variable_name}}`
    * `content`
    * `title`
    * `excerpt`
    * `url`
    * `date`
    * `id`
    * `categories`
    * `tags`
    * `path`
    * `next`
    * `previous`
    * `<custom variable from header>`

## Other Helpers

* `{{content}}` - the content in a layout page
* `[link text here](/assets/something.png).
* `{% for post in site.posts %}.
* `{{post.excerpt}}`
* `{% endfor %}`
* `{% assign author = site.data.people[page.author] %}`

```
{% highlight javascript linenos %}
    <code goes here>
{% endhighlight %}
```

## Styles

SASS support is built-in. Main file needs to have the right extension and start with a pair of ---, imported files do not.

## `_config.yml` - Configuration data

```
source: <source folder>
destination: <build folder>
include: <any dot files>
timezone: America/Denver
excerpt_separator: <!--more-->
```
