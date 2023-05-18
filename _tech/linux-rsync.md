---
layout: post
title:  "Linux rsync"
date:   2023-05-10 21:17:21 -0600
categories: tech linux
tags: tech linux rsync
author: Trevor Facer
---

## What is rsync?

> rsync - a fast, versatile, remote (and local) file-copying tool

## Options and Examples

* `rsync -r --info=progress2 /mnt/usb/switch/Nintendo ~/Downloads/backups` - Copy directory, with overall status to new destination. In example, result will be at `~/Downloads/backups/Nintendo`
