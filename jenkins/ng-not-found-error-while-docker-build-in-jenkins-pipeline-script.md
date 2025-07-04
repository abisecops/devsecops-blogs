---
description: 'Issue found on npm while docker build:  hicare_omdashboard_prod'
---

# ng not found error while docker build in jenkins pipeline (script)

#### The issue is simple, `npm` doesn't know about `ng.`

`I got the following issue while docker build:`&#x20;

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

From the logs shell script, I found:&#x20;

```bash
> store-web@0.0.0 build /App
> ng build

[91msh: 1: ng: not found
[0m[91mnpm ERR! code[0m[91m ELIFECYCLE
[0m[91mnpm[0m[91m ERR! syscall spawn
npm[0m[91m ERR! file sh
[0m[91mnpm ERR! [0m[91merrno ENOENT
[0m[91mnpm ERR! store-web@0.0.0 build: `ng build`
npm[0m[91m ERR! spawn ENOENT
npm [0m[91mERR! 
npm ERR! Failed at the store-web@0.0.0 build script.
npm[0m[91m [0m[91mERR! This is probably not a problem with npm. There is likely additional logging output above.
[0m[91m
npm ERR! A complete log of this run can be found in:
[0m[91mnpm ERR![0m[91m     /root/.npm/_logs/2024-02-27T09_13_42_130Z-debug.log
[0mThe command '/bin/sh -c npm run build --prod' returned a non-zero code: 1
```

1. Then, I looking for **Dockerfile**.&#x20;

* Status -> Workspace -> given link

#### In my case,&#x20;

## Workspaces for OM Dashboard Angular Pipeline(S3 Prod) Docker-ECR #95

* [`/var/lib/jenkins/workspace/OM Dashboard Angular Pipeline(S3 Prod) Docker-ECR`](http://103.60.176.158:8080/job/OM%20Dashboard%20Angular%20Pipeline\(S3%20Prod\)%20Docker-ECR/95/execution/node/3/ws/) on built-in

2. Check the Dockerfile.

* [http://103.60.176.158:8080/job/OM%20Dashboard%20Angular%20Pipeline(S3%20Prod)%20Docker-ECR/95/execution/node/3/ws/HiCare.Dashboard.Portal/OMStoreWeb/Dockerfile/\*view\*/](http://103.60.176.158:8080/job/OM%20Dashboard%20Angular%20Pipeline\(S3%20Prod\)%20Docker-ECR/95/execution/node/3/ws/HiCare.Dashboard.Portal/OMStoreWeb/Dockerfile/*view*/)

I found:&#x20;

<pre class="language-docker"><code class="lang-docker"><strong>FROM node:14.16.1 as source
</strong>WORKDIR /App
COPY /package.json .
RUN npm install
COPY /. .
RUN npm run build --prod

FROM nginx:alpine
COPY --from=source /App/dist/StoreWeb /usr/share/nginx/html
EXPOSE 80
</code></pre>

Then, I tried to install angular/cli with dockerfile. But I ask for version 18.0.2.&#x20;

<pre class="language-docker"><code class="lang-docker"><strong>FROM node:14.16.1 as source
</strong>WORKDIR /App
<strong>COPY /package.json .
</strong>
RUN npm install -g @angular/cli@latest
RUN npm install
COPY /. .
RUN npm run build --prod

FROM nginx:alpine
COPY --from=source /App/dist/StoreWeb /usr/share/nginx/html
EXPOSE 80
</code></pre>

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

Later, I installed the **angular/cli**  in cli instead of dockerfile: \
&#x20;Install in the jenkins server cli:&#x20;

```
npm install -g @angular/cli@latest
```

<figure><img src="../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

Issue is finally solved.  :tada:
