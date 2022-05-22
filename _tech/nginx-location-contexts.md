---
layout: post
title:  "Nginx Location Contexts"
date:   2022-05-21 14:07:21 -0600
categories: tech nginx
tags: tech nginx
author: Trevor Facer
---

## Location Pattern Matching

See official docs [here](https://nginx.org/en/docs/http/ngx_http_core_module.html#location).

* `location =`

```nginx
location = /something {
  # matches the URI exactly
  # search stops after this is matched
}
```

* `location /`

```nginx
location / {
  # matches everything
  # continues checking other regex location contexts
}
```

* `location /something`

```nginx
location /something {
  # matches everything prefixed with /something
  # continues checking other regex location contexts
}
```

* `location ^~ /something`

```nginx
location ^~ /something {
  # matches everything prefixed with /something
  # stops search, so regex location contexts will not be checked
}
```

* `location ~* \.(gif|jpg|jpeg)$`

```nginx
location ~* \.(gif|jpg|jpeg)$ {
  # case-insensitive regex matching
  # matches anything ending in .gif, .jpg, or .jpeg
}
```

* `location ~ \.(gif|jpg|jpeg)$`

```nginx
location ~ \.(gif|jpg|jpeg)$ {
  # case-sensitive regex matching
  # matches anything ending in .GIF, .JpG, .jpeg, etc.
  # /images/something.GIF would match
  # /something/image.GIF would not, it would be picked up by `^~ /something`
}
```

## Docker Example

* See demo Docker container [here](https://tdfacer.github.io/tech/nginx-docker).

### Test Cases

Create docker container using `start.sh` script from above in `Docker Example`

| Method    | URL    | Result    |
|---------------- | --------------- | --------------- |
| GET    | localhost    | hello from = /    |
| GET    | localhost/   | hello from = /    |
| GET    | localhost/something    | hello from = /something    |
| GET   | localhost/something/else   | hello from ^~ /something   |
| GET   | localhost/images   | hello from ^~ /images   |
| GET   | localhost/images/   | hello from ^~ /images   |
| GET   | localhost/images/arbitrary   | hello from ^~ /images   |
| GET   | localhost/arbitrary   | hello from /   |
| GET   | localhost/images/image.gif   | hello from ^~ /images   |
| GET   | localhost/arbitrary/image.gif   | hello from ~* .(gif\|jpg\|jpeg)   |
| GET   | localhost/arbitrary/image.GiF   | hello from ~* .(gif\|jpg\|jpeg)   |
| GET   | localhost/arbitrary/image.JPEG   | hello from ~* .(gif\|jpg\|jpeg)   |
