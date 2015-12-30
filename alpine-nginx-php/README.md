# alpine-nginx-php
Minimal Docker image for a php (nginx) server based on alpine linux


## Usage
Run a new server, note that /path/to/content is the parent of htdocs (so, the actual content exists on /path/to/content/htdocs)
    docker run -d --name some_server -v /path/to/content:/DATA:ro -p 80:80 ktcagency/alpine-nginx-php