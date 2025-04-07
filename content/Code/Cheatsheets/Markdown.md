---
tags: [markdown, cheatsheet, reference]
aliases: [Markdown Reference]
date: {{date}}
---

# Markdown Cheatsheet

## Headings

# H1

## H2

### H3

#### H4

##### H5

###### H6

**Bold**  →  **Bold**  
*Italic*  →  *Italic*  
~~Strikethrough~~  →  \~\~Strikethrough

- Item 1 
  - Sub-item 1 
    - Sub-sub-item
- Item 2

1. First
2. Second
3. Third

> This is a blockquote.
>
> > Nested blockquote.

`` `inline code` ``

```python
print("Hello, World!")
```

Tables

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Value 1  | Value 2  | Value 3  |
| Value 4  | Value 5  | Value 6  |

```|
|----------|----------|----------|
| Value 1  | Value 2  | Value 3  |
| Value 4  | Value 5  | Value 6  |
```

Checkboxes

- [ ] Task 1
- [x] Completed Task

---

Here's a reference[^1].

[^1]: Footnote text.

> [!NOTE]
> This is an Obsidian callout.

This note is **fully compatible** with Obsidian, including **callouts, internal links, and task lists**. Would you like me to add **custom Obsidian keyboard shortcuts** as well?

Links
[Obsidian Website](https://obsidian.md)

!\[\[IMG_6054.JPG\]\]

From a subfolder
`![[Images/my-image.png]]`

From an absolute path
`![Image](file:///home/user/Pictures/my-image.png)`
not recommended because Obsidian might not display external images properly

Just drag and drop or paste and Obsidian will do for you

### **Best Practice**

- Store images in an `Images/` subfolder inside your vault for organization.
- Use `![[filename]]` instead of `[![filename]](path)` for seamless embedding.
- Enable **"Automatically embed media"** in Obsidian settings for smooth previews