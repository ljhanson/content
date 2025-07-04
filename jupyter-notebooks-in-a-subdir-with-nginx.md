---
title: Jupyter Notebooks in a subdir with nginx.
date: 2016-12-13
author: L.J. Hanson
tags:
    - Python
    - nginx
    - Jupyter
slug: jupyter-notebooks-in-a-subdir-with-nginx
draft: false
---
Nginx section for subdir:

```nginx
location ^~ /<subdir>/ {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header HOST $http_host;
            proxy_set_header X-NginX-Proxy true;
            proxy_pass http://127.0.0.1:8888;
            proxy_redirect off;
            proxy_http_version 1.1;
            proxy_set_header Upgrade "websocket";
            proxy_set_header Connection "Upgrade";
            proxy_read_timeout 86400;
        }
```

Configuration changes for Jupyter:

```python
c.NotebookApp.base_url = '/<subdir>/'
c.NotebookApp.open_browser = False
c.NotebookApp.password = '<password>'
c.NotebookApp.trust_xheaders = True
```
