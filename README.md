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
