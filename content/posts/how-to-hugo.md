---
title: "How to Hugo"
date: 2023-10-21T17:15:08-07:00
description: A meta post about Hugo basics and how I used Hugo to create this website.
image: 
tags: ["hugo", "blogging"]
---
# Overview of Hugo site folder structure

```
my-site/
├── archetypes/   <-- templates for new content
│   └── default.md
├── assets/
├── content/
│   └── posts/
│      └── _index.md
│      └── first-post.md
│   └── quotes/
├── data/        <-- data files e.g. JSON
├── i18n/
├── layouts/
├── public/       <-- created when you build your site
├── resources/    <-- created when you build your site
├── static/
|── themes/       <-- downloaded prebuild templates (git submodule)
└── hugo.toml     <-- hugo site settings
```

### Themes

- I'm using [Hugo Winston](https://themes.gohugo.io/hugo-winston-theme/) theme

### Content

- directory structure under this folder creates the site's url pathing
- the directory structure matters and should model the organization of the site

# Types of content

There are two main content page types:

1. **List pages** lists other available pages (rendered via list.html templates)
   - Home page is a list page, because it lists other pages on the site
   - Section pages list other pages in the same section
2. **Single pages** display information about a topic (rendered via single.html templates)

```
├── content/
│   └── posts/   <----- top level section
│      |── _index.md
│      └── first-post.md
│   └── quotes/
│      | 
│      └── favorite-quote.md

```

## Special files and folders

- A **section** is a top-level content directory, or any content directory with an _index.md file.
- [_index.md](https://gohugo.io/content-management/organization/#index-pages-_indexmd): is a list page where you can define parameters and configurations in the front matter for an entire _section_
  - not meant to render content
  - note that a list page is automatically created for top-level sections (`/content/quots`), but adding a `_index.md` file allows you to override and inject more custom content and configurations
  - Hugo recommends creating an `_index.md` file for every section, too
- not to be confused with `index.md`, which is a content "landing" page for a section which can tell a user what the section is about

There are functional differences between sections and non-sections (content sub-directories without an _index.md):

| | Section | Non-section |
| --- | --- | --- |
|Directory names become URL segments| ✔️| ✔️|
|Have logical ancestors and descendants|✔️| ❌|
|Have list pages|✔️| ❌|

# Archetypes

- effectively "templates" for front matter
- can create archetypes specific to a content directory by naming archetype file the same name as the directory
- `archetypes/posts.md` is the front matter template for new pages in `/posts/` directory

# Short codes

- Shortcodes are reusable snippets of HTML and are often used for embedding youtube videos, twitter posts, etc.
- you can create your own shortcodes

```
# example shortcode
{{< youtube id_of_youtube_video >}}
```

- See Hugo predefined shortcodes [here](https://gohugo.io/content-management/shortcodes/#use-hugos-built-in-shortcodes)

# Taxonomies

There are two default taxonomies: tags and categories

- you can add categories or tags to a markdown file by adding the tag or category in a markdown file's front matter
- Hugo automatically creates a taxonomy list page for each tag and category (rendered as a list template)

### Custom taxonomy

- you can create a custom taxonomy by adding it to front matter of any markdown file

```yaml
---
title: i feel good
mood: ["happy"]
---
```

- Hugo will **not** automatically create a page for custom taxonomies
  - trying to navigate to `/content/moods/happy` will return a 404 not found unless you add the custom taxonomy to the `hugo.toml`

```toml
# add all taxonomies, including the default ones. Use singular = "plural" format.
[taxonomies]
  tag = "tags"
  category = "categories"
  mood = "moods"
```
