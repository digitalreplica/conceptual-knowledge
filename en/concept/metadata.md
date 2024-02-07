---
aliases:
  - metadata
id: 44424ff5-e833-440c-8d6e-95ac977b8007
is:
  - "[[concept]]"
urls:
  - https://en.wikipedia.org/wiki/metadata
---
# Summary
Metadata is data that provides information about other data. In the context of a markdown document, metadata refers to information that describes the document's characteristics, such as its title, author, creation date, keywords, or categories. This data is typically placed at the beginning of a markdown file, within a section known as "frontmatter."

The frontmatter is a block of YAML (YAML Ain't Markup Language) code, usually enclosed by three dashes (```---```), which separates it from the main content of the markdown document. YAML is a human-readable format for storing data in a structured manner. Within the frontmatter, metadata is specified as key-value pairs, where each key represents a metadata field, and the value associated with it represents the actual data.

For example, consider the following markdown document with frontmatter:

```markdown
---
title: "My Markdown Article"
author: "John Doe"
date: "2023-02-20"
tags: [markdown, writing, tutorial]
category: "Blogging"
---

# Introduction
This is the content of my article...
```

In this example, the metadata includes:

1. **title**: The title of the document, "My Markdown Article."
2. **author**: The author's name, "John Doe."
3. **date**: The creation or publication date, "2023-02-20."
4. **tags**: A list of keywords or tags related to the content, here "markdown," "writing," and "tutorial."
5. **category**: The document's category, "Blogging."

This metadata can be useful in several ways:

- **Organization**: It helps to categorize and filter documents, especially when working with a large collection of markdown files.
- **Automation**: Tools and static site generators like Jekyll, Hugo, or Gatsby can utilize metadata to generate table of contents, generate feeds (like RSS), or create a sitemap.
- **Search**: Search engines or local search tools can use metadata to provide more relevant search results.
- **Presentation**: Metadata can be used to style or format the document, such as displaying the title as a heading or the author's name as a byline.

In summary, metadata in the frontmatter of a markdown document provides essential information about the content, enabling better organization, automation, search, and presentation of the document.
