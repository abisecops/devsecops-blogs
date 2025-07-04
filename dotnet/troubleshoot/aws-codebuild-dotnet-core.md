---
description: Build and test code with elastic scaling. Pay only for the build time you use.
cover: >-
  https://d2908q01vomqb2.cloudfront.net/7719a1c782a1ba91c031a682a0a2f8658209adbf/2023/01/03/devops_2213_FIM-1120x630.png
coverY: 0
---

# AWS CodeBuild DotNet Core

AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy. With CodeBuild, you don’t need to provision, manage, and scale your own build servers. CodeBuild scales continuously and processes multiple builds concurrently, so your builds are not left waiting in a queue.

<figure><img src="../../.gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

Steps:&#x20;

## Create build project

<figure><img src="../../.gitbook/assets/image (152).png" alt=""><figcaption></figcaption></figure>



Project Name:

<figure><img src="../../.gitbook/assets/image (154).png" alt=""><figcaption></figcaption></figure>

Source:

[https://github.com/whoami-anoint/OnTopic-Library](https://github.com/whoami-anoint/OnTopic-Library)

<figure><img src="../../.gitbook/assets/image (155).png" alt=""><figcaption></figcaption></figure>

Environment:

<figure><img src="../../.gitbook/assets/image (156).png" alt=""><figcaption></figcaption></figure>

Buildspec:



<figure><img src="../../.gitbook/assets/image (158).png" alt=""><figcaption></figcaption></figure>

Yaml script:&#x20;

```yaml
version: 0.2

phases:
  install:
    commands:
      - curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin --channel STS 
  build:
    commands:
      - dotnet restore OnTopic.sln
      - dotnet build OnTopic.sln

```

Batch Configuration:

<figure><img src="../../.gitbook/assets/image (159).png" alt=""><figcaption></figcaption></figure>

Error found on:&#x20;

<figure><img src="../../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>
