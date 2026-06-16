# Angazenn.github.io

My personal blog powered by [Jekyll](https://jekyllrb.com/) and hosted on [GitHub Pages](https://pages.github.com/).

## Local Development

```bash
# Install dependencies
bundle install

# Start the development server
bundle exec jekyll serve

# Build for production
bundle exec jekyll build
```

Visit `http://localhost:4000` to preview the site locally.

## Writing a New Post

1. Create a new file in `_posts/` with the format `YYYY-MM-DD-title.md`
2. Add frontmatter:

```yaml
---
layout: post
title: "Your Post Title"
date: YYYY-MM-DD
categories: category-name
description: "A short description for SEO and previews"
---
```

3. Write your content in Markdown

## Structure

```
.
├── _config.yml        # Site configuration
├── _layouts/          # Page layouts
├── _includes/         # Reusable components
├── _posts/            # Blog posts
├── _sass/             # Sass partials (optional)
├── assets/            # CSS, JS, images
│   ├── css/
│   ├── js/
│   └── images/
├── index.html         # Homepage
├── about.md           # About page
└── 404.html           # Not found page
```
