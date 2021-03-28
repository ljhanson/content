Title: Nikola Setup Notes
Date: 2021-03-23 22:47
Author: L.J. Hanson
Slug: nikola-setup-notes

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
