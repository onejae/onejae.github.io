---
title: "Gitlab runner failed  a message 'Cannot connect to the Docker daemon at unix:///var/run/docker.sock.'"

categories:
  - Notes
tags:
  - [시작]

permalink: /categories/notes/2

toc: true
toc_sticky: true

date: 2023-09-25
last_modified_at: 2023-09-25
---

I encountered an error message while testing a GitLab CI/CD pipeline locally.

![img](/assets/images/posts_img/runnerfailed.png)

I resolved the issue by configuring the DOCKER_HOST environment variable with the correct host location.

```sh
export DOCKER_HOST=unix:///Users/onejae/.docker/run/docker.sock

```

![img](/assets/images/posts_img/runner.png)
