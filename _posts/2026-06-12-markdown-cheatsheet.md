---
layout: post
title: "A Quick Markdown Cheatsheet for Blogging"
date: 2026-06-12 14:30:00 +0700
categories: writing
description: "A handy reference for Markdown syntax you'll use when writing blog posts with Jekyll."
---

Writing in Markdown is great. Here's a quick reference of the most useful syntax for blogging.

## Text Formatting

| Style | Syntax | Output |
|-------|--------|--------|
| Bold | `**bold**` | **bold** |
| Italic | `*italic*` | *italic* |
| Strikethrough | `~~strikethrough~~` | ~~strikethrough~~ |
| Inline code | `` `code` `` | `code` |

## Headings

Use `#` for headings — more hashes, smaller headings:

```
# H1 - Post titles use these
## H2 - Section headings
### H3 - Sub-sections
```

## Code Blocks

Use triple backticks with a language name for syntax highlighting:

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("World"))
```

## Links and Images

```markdown
[Link text](https://example.com)
![Alt text](/path/to/image.png)
```

## Blockquotes

```markdown
> This is a blockquote. Great for highlighting quotes or callouts.
```

> This is a blockquote. Great for highlighting quotes or callouts.

## Lists

**Unordered:**
```markdown
- Item one
- Item two
  - Nested item
```

**Ordered:**
```markdown
1. First step
2. Second step
3. Third step
```

## Horizontal Rule

Use three dashes for a separator:

```markdown
---
```

---

That covers 90% of what you'll need. Happy writing!
