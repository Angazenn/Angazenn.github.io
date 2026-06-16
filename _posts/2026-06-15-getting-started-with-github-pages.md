---
layout: post
title: "Getting Started with GitHub Pages"
date: 2026-06-15 11:00:00 +0700
categories: tutorial
description: "A step-by-step guide to setting up your own GitHub Pages site with Jekyll."
---

GitHub Pages is one of the easiest ways to host a website for free. Here's how to get started.

## Step 1: Create the Repository

Create a new repository named `<username>.github.io`. It must be public (unless you have GitHub Pro). This repo name becomes your site URL.

```bash
# Example
git init myblog
cd myblog
```

## Step 2: Add Jekyll

Jekyll is a static site generator built into GitHub Pages. You write content in Markdown, and Jekyll generates the HTML.

Create a `Gemfile`:

```ruby
source "https://rubygems.org"
gem "jekyll", "~> 4.3"
```

Then install:

```bash
bundle install
```

## Step 3: Configure Your Site

Create a `_config.yml`:

```yaml
title: My Awesome Blog
description: A blog about things
url: https://username.github.io
```

## Step 4: Write a Post

Posts go in the `_posts/` directory with the naming format `YYYY-MM-DD-title.md`. Each post needs frontmatter:

```yaml
---
layout: post
title: "My First Post"
date: 2026-06-15
---
```

## Step 5: Build and Serve Locally

```bash
bundle exec jekyll serve
```

Visit `http://localhost:4000` to see your site.

## Step 6: Deploy

Just push to GitHub:

```bash
git add .
git commit -m "Add blog"
git push origin main
```

GitHub automatically builds and deploys your site. You'll find it at `https://username.github.io`.

---

That's it! Six steps to get from nothing to a live blog. Now all that's left is to keep writing.
