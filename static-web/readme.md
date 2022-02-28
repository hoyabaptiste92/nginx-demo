# Nginx Docker

## Hosting some simple static content

```console
docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx
```

Alternatively, a simple Dockerfile can be used to generate a new image that includes the necessary content (which is a much cleaner solution than the bind mount above):

```console
FROM nginx
COPY static-html-directory /usr/share/nginx/html
```

Place this file in the same directory as your directory of content ("static-html-directory"), run

```console
docker build -t static-web-nginx .
```

then start your container:

```console
docker run --name some-nginx -p 4000:80 -d static-web-nginx
```
