Title: Jupyter Notebooks in a subdir with nginx.
Date: 2016-12-13 03:00
Author: L.J. Hanson
Tags: Python, nginx, Jupyter Notebook
Slug: jupyter-notebooks-in-a-subdir-with-nginx

Nginx section for subdir:

</p>
         location ^~ /<subdir>/ {            proxy_set_header X-Real-IP $remote_addr;            proxy_set_header HOST $http_host;            proxy_set_header X-NginX-Proxy true;            proxy_pass http://127.0.0.1:8888;            proxy_redirect off;            proxy_http_version 1.1;            proxy_set_header Upgrade "websocket";            proxy_set_

</p>
