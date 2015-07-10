# dokku-docker-reset-mtime

Simply resets the mtime (modified time) metadata on your source files to a set
datetime before building the image with docker. I made this to work around
docker's caching system taking into account the modified time when checking if
a file has changed or not. If the mtime changed, even if the file is exactly
the same, the cache will be invalidated. This is annoying because git
inherently modifies the mtime of all the files when you clone, pull, etc.

This plugin shouldn't be needed when version 1.8.0 of docker gets released and
dokku makes the switch, but for now, here we go.

The solution is based off [this StackOverflow question](http://stackoverflow.com/questions/26531108/docker-add-cache-when-git-checkout-same-file/26612694#26612694).

Here's the relevant [Docker PR](https://github.com/docker/docker/pull/12031)
on the issue.

## Installation

```bash
git clone https://github.com/mixxorz/dokku-docker-reset-mtime.git /var/lib/dokku/plugins/reset-mtime
```

That's all folks.
