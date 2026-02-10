# blog.podepod.be

## Start development server

```bash
hugo server --bind 65.108.82.132 --baseURL http://65.108.82.132 -D
```

## Import a new theme

```bash
git submodule add <theme-github-link> themes/<theme-name>
echo "theme = '<theme-name>'" >> hugo.toml
```


## Add content
```bash
hugo new content content/posts/<post-tittle>.md
```

After adding content the git repository should be updated

```bash
git add *
git commit -m "<commit message>"
git push -u origin main
```

## content header

```
+++
date = '2026-01-21T09:34:02Z'
draft = false
title = 'Hello Blog'
author = 'Podepod'
tldr = 'The first post of this blog, written over the span of a few days while I setup the website.'
tags = ['blog','research']
+++
```

## TODO

- [ ] Custom Theme maken -> ander git project -> import as module 
- [ ] make the new_post script (ask for a title, add empty author, tldr and tags field to the frontmatter)

## Images in posts

https://stackoverflow.com/questions/71501256/how-to-insert-an-image-in-my-post-on-hugo
