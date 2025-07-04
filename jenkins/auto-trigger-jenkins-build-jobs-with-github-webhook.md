---
description: We're going to do github integration with jenkins using github webhook.
cover: ../.gitbook/assets/image (115).png
coverY: 0
---

# Auto Trigger Jenkins Build /Jobs with github webhook

#### Steps:&#x20;

1. You should have jenkins server hosted on public IP accessible remotely.&#x20;

{% embed url="http://103.60.176.158:8080" %}

2. If you have localhost, you can also port your ip with any public IP. Ngrok is also a another option you can try.&#x20;
3. To set webhook on the repo. Follow the path as given :&#x20;

{% embed url="https://github.com/your_username/github_repo/settings/hooks/" %}

In my case, [https://github.com/whoami-anoint/Hitop/settings/hooks/](https://github.com/whoami-anoint/Hitop/settings/hooks/)&#x20;

#### While adding webhook:&#x20;

* Payload URL : [http://103.60.176.158:8080](http://103.60.176.158:8080)/github-webhook/
* Content type: **application/json**
* Secret : blank
* Which events would you like to trigger this webhook?&#x20;
* Then make webhook **active**.

#### You may found some error. To avoid error from jenkins:&#x20;

* Make sure the payload url should end with **/**. (To fix: 302 error)
* Content type be application/json . ( To fix : 502 error)
* Make sure you are getting 200 response.

<figure><img src="../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

&#x20;Webhook is finally added on github repo.&#x20;

<figure><img src="../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

5. Now, time to make pipeline on jenkins with the github repo:&#x20;

* Add new item -> Pipeline&#x20;
* Give any pipeline name. (Repo name is preferred to reference.)
* Source Code Management -> Repository URL and credentials (if private repo)
* Branches to build -> \*/main (your branch)
* Build Triggers -> :white\_check\_mark: GitHub hook trigger for GITScm polling

6. Make any changes on github repo.

<figure><img src="../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

7. Let's check on jenkins:&#x20;

<figure><img src="../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

Also check on jenkins console:&#x20;

* Started by GitHub push by whoami-anoint

<figure><img src="../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

:tada: We have successfully auto triggered the jenkins build using github webhook. Whenever, we made any changes on our github repo, that will be auto merge and auto build in jenkins.&#x20;
