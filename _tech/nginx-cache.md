---
layout: post
title:  "Nginx Testing"
date:   2022-10-24 14:07:21 -0600
categories: tech nginx cache
tags: tech nginx testing
author: Trevor Facer
---

## Cache

* Docs for `proxy_cache_path` [here](https://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_cache_path)

### Directives

* `use_temp_path` - Use a temporary path for cached files, before calculating md5sum filename
