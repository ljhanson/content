---
title: Snippets in VSCode
date: 2022-12-28
author: L.J. Hanson
tags:
- vscode
- blog
slug: snippets-in-vscode
description: "Using Snippets in VSCode"
draft: true
---

You can create snippets to add content to files in VSCode to put in boilerplate.  In this example I'm using a snippet to create the frontmatter for a blogpost.

```json
{
	"Markdown FrontMatter": {
	"prefix": "eventFrontMatter",
	"body": [
	  "---",
	  "title: $1",
	  "date: $2",
	  "author: L.J. Hanson",
	  "tags: [$3]",
	  "slug: $4",
	  "description: $5",
	  "draft: true",
	  "---",
	  ""
	],
	"description": "Markdown FrontMatter"
  }
}
```
