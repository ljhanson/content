---
title: Nikola Setup Notes
date: 2021-03-23
author: L.J. Hanson
slug: nikola-setup-notes
draft: false
---
To get Pelican style metadata working in Nikola you must add the markdown
metadata extension to your config.

```python
MARKDOWN_EXTENSIONS = [
    "markdown.extensions.fenced_code",
    "markdown.extensions.codehilite",
    "markdown.extensions.extra",
    "markdown.extensions.meta",
]
```
