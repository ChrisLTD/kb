---
description: Setting Up Cloud 9 Server using Amazon Linux
---

# AWS Cloud 9

When creating your instance if you see this error:&#x20;

> The following resource(s) failed to create: \[Instance]&#x20;

It’s because you have a legacy account. Setting up a new server now requires you to explicitly pick a subnet in the advanced settings.

## Setting up SSH Keys

```
$ ssh-keygen -t rsa -b 4096 -C "your@email.com"
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
$ cat ~/.ssh/id_rsa.pub
```

Copy output to Github or Bitbucket where you're pushing and pulling your code from.

## Setting up Docker Compose

Instructions for installing docker compose [https://docs.docker.com/compose/install/#install-compose](https://docs.docker.com/compose/install/#install-compose)

```
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
$ sudo chmod +x /usr/local/bin/docker-compose
```

## Resize Cloud9 instance

Check space usage:

```
$ df -h
```

Follow these instructions: [https://docs.aws.amazon.com/cloud9/latest/user-guide/move-environment.html#move-environment-resize](https://docs.aws.amazon.com/cloud9/latest/user-guide/move-environment.html#move-environment-resize)
