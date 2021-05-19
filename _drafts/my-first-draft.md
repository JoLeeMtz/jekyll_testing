---
layout: post
title: "Draft jekyll tests"
categories: jekyll new-cat
permalink: /:categories
---
## Quick tips Jekyll

Draft file, not posted.

* * *

### Launching web application

- Install jekyll and bundler gems:

```bash
gem install jekyll bundler
```

- Create a new jekyll site at ./myblog

```bash
jekyll new myblog
```

- Change into your new directory:

```bash
cd myblog
```

- Build the site and make it available on a local server:

```bash
bundle exec jekyll serve
```

- Original application exec (first time executing it):

```bash
bundle exec jekyll serve
```

- Original application exec:

```bash
jekyll serve
```

Pass the `--livereload` option to `serve` to automatically refresh the page with each change you make to the source files:

```bash
bundle exec jekyll serve --livereload
```

- To see drafts:

```bash
jekyll serve --draft
```

* * *

### Set URL for pages

Set permalink with variables:

```yaml
permalink: /:categories/:year/:month/:day/:title
```

* * *

### Themes

To change theme we need to go on:

[RubyGems](https://www.rubygems.org/){:target="_blank"}

- Type `jekyll-theme`, in the search input.
- Click on the theme wanted.
- Look for the `LINKS` section.
  - And click on `Homepage`.
- Look for `Add this line to your Jekyll site's Gemfile:`, where we can find the name of the theme we want to use.
  - Example : `gem "jekyll-cv-theme"`.
  - Important to stop server and do `bundle install` to install the theme.
  - `bundle update`, if needed.
- Look for `add this line to your Jekyll site's _config.yml`, where we can find the name of the theme we want to use.
  - Example : `theme: jekyll-cv-theme`.
- Set the theme in `_config.yml`.

* * *

### Layouts

The folder `layouts` contains the html we want to use on a layout call.

- Example if we create a file named `superman.html` (usually it's html files in the `_layouts`).
  - We can use that layout, just by adding on the top section:

   ```yaml
   layout: superman
   ```

* * *

### Variables

- To access a variable of a **layout**, it needs to start with `layout`, dot the variable you want to access, you can find it in `layout.html` or `layout.md`:

```html
<h2>{ { layout.stuff } }</h2>
```

- To access a variable of a **page**, it needs to start with `page`, dot the variable you want to access, you can find it in `page.html` or `page.md`:

```html
<h1>{ { page.title } }</h1>
```

- To access a variable of the **site**, it needs to start with `site`, dot the variable you want to access, you can find it in `_config.yml`:

```html
<h1>{ { site.title } }</h1>
```

[jekyll-docs-variables](https://jekyllrb.com/docs/variables/){:target="_blank"}

* * *

### Includes

Needs a file named `_includes`, where we can add files that we want to include in other files.\

- To include the file in a another file we can call it by adding into our .html or .md file:

```html
{ % include header.html % }
```

- To include a variable, we just add it after:

```html
{ % include header.html color="blue" % }
```

- And to be able to use that variable, we call:

```html
<h1 style="color:{ { include.color } }"></h1>
```

* * *

### Looping Through posts

Example in `_layouts/loopPosts.html`, link `http://127.0.0.1:4000/jekyll/update/2021/05/18/show_all.html`.

* * *

### Data files

Example in `_data/person.yml` and in `_layouts/dataBaseTests.html`, link `http://127.0.0.1:4000/2021/05/18/data_base_tests.html`.\
Can be written in:

- YAML
- JSON
- CSV

Added infos in `_config.yml`:

```yaml
defaults:
  - scope:
      path: "assets/img"
    values:
      image: true
```

* * *

### Github Pages
Need to go on `_config.yml` and change the value of `baseurl`.\
Need to set the repository created in GitHub, in this case `jekyll_testing`.

Commands to do after:

- `git init`
- `git checkout -b gh-pages`
- `git status`, a lot of files will not be up to date.
- `git add .`
- `git commit -m "initial commit"`
- `git remote add origin https://github.com/JoLeeMtz/jekyll_testing.git`
- `git push origin gh-pages`
