---
title: "secret create"
description: "The secret create command description and usage"
keywords: ["secret, create"]
---

<!-- This file is maintained within the docker/docker Github
     repository at https://github.com/docker/docker/. Make all
     pull requests against that repo. If you see this file in
     another repository, consider it read-only there, as it will
     periodically be overwritten by the definitive file. Pull
     requests which include edits to this file in other repositories
     will be rejected.
-->

# secret create

```Markdown
Usage:  docker secret create [NAME]

Create a secret using stdin as content
Options:
      --help         Print usage
  -l, --label list   Secret labels (default [])
```

Creates a secret using standard input for the secret content. You must run this
command on a manager node.

## Examples

### Create a secret

```bash
$ cat secret.json | docker secret create secret.json
mhv17xfe3gh6xc4rij5orpfds

$ docker secret ls
ID                          NAME                    CREATED                                   UPDATED                                   SIZE
mhv17xfe3gh6xc4rij5orpfds   secret.json             2016-10-27 23:25:43.909181089 +0000 UTC   2016-10-27 23:25:43.909181089 +0000 UTC   1679
```

### Create a secret with labels

```bash
$ cat secret.json | docker secret create secret.json --label env=dev --label rev=20161102
jtn7g6aukl5ky7nr9gvwafoxh

$ docker secret inspect secret.json
[
    {
        "ID": "jtn7g6aukl5ky7nr9gvwafoxh",
        "Version": {
            "Index": 541
        },
        "CreatedAt": "2016-11-03T20:54:12.924766548Z",
        "UpdatedAt": "2016-11-03T20:54:12.924766548Z",
        "Spec": {
            "Name": "secret.json",
            "Labels": {
                "env": "dev",
                "rev": "20161102"
            },
            "Data": null
        },
        "Digest": "sha256:4212a44b14e94154359569333d3fc6a80f6b9959dfdaff26412f4b2796b1f387",
        "SecretSize": 1679
    }
]

```


## Related information

* [secret inspect](secret_inspect.md)
* [secret ls](secret_ls.md)
* [secret rm](secret_rm.md)

<style>table tr > td:first-child { white-space: nowrap;}</style>
