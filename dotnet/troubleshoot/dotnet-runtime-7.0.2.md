---
description: Today I have to install and config dotnet runtime 7.0.2 in ubuntu server
cover: ../../.gitbook/assets/image (170).png
coverY: 0
---

# Dotnet runtime:  7.0.2

**NET is made up of the runtime and the SDK. The runtime is used to run a .NET app and might be included with the app. The SDK is used to create .NET apps and libraries. The .NET runtime is always installed with the SDK.**

Download link **Dotnet runtime 7.0.2**:&#x20;

{% embed url="https://download.visualstudio.microsoft.com/download/pr/83524cc2-60fb-4e49-8769-e9ecb1af8e46/a28b17808ffe21483b2f719091a0544f/dotnet-runtime-7.0.2-linux-x64.tar.gz" %}

Download link sdk:&#x20;

{% embed url="https://download.visualstudio.microsoft.com/download/pr/c646b288-5d5b-4c9c-a95b-e1fad1c0d95d/e13d71d48b629fe3a85f5676deb09e2d/dotnet-sdk-7.0.102-linux-x64.tar.gz" %}

Extract both files.&#x20;

For sdk:

```
cd dotnet-sdk-7.0.102-linux-x64
sudo mv dotnet /usr/local/

```

For runtime:

```bash
cd dotnet-runtime-7.0.2-linux-x64
sudo mv Microsoft.NETCore.App /usr/lib/dotnet/shared/
```

```bash
echo 'export PATH=$PATH:/usr/local/dotnet' >> ~/.bashrc
source ~/.bashrc
```

Check dotnet version:&#x20;

```
dotnet --version
```



To check dotnet runtimes:

```
dotnet --list-runtimes
```

<figure><img src="../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

Check dotnet information

```
dotnet --info
```

<figure><img src="../../.gitbook/assets/image (165).png" alt=""><figcaption></figcaption></figure>
