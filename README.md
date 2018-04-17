# Nginx with brotli

The newest nginx and [eustas's ngx_brotli fork](https://github.com/eustas/ngx_brotli).

This image does not contain default site config.

You must provide your `conf.d` and your contents to be served.

## Examples

conf.d/site.conf
```
brotli on;
brotli_comp_level 11;
brotli_min_length 2048;
brotli_static on;
brotli_types
  application/atom+xml
  application/javascript
  application/json
  application/rss+xml
  application/x-javascript
  application/x-json
  application/xhtml+xml
  application/xml
  image/svg+xml
  text/css
  text/json
  text/javascript
  text/plain
  text/x-javascript
  text/x-json
  text/xml;

server {
  listen 80;
  root /site;
}
```

```sh
$ docker run \
  -v /path/to/conf.d:/etc/nginx/conf.d \
  -v /path/to/public:/site \
  ...
```
