---
description: 'Add microsoft package source:'
---

# Unable to locate package dotnet-sdk-8.0

```bash
wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
```

Now you can run commands to install the new dotnet-host (on dotnet 8) and dotnet-sdk

```bash
sudo apt-get update
sudo apt-get install -y dotnet-host
sudo apt-get install -y dotnet-sdk-8.0
```

If you get any conflicts on install with existing installed packages, you have to uninstall those packages first.

First I saw a conflict againest "netstandard-targeting-pack-2.1-7.0" I wrote down this: sudo apt-get remove netstandard-targeting-pack-2.1-7.0

Then run again all these:

```bash
sudo apt-get update 
sudo apt-get install -f -y dotnet-host 
sudo apt-get install -f -y dotnet-sdk-8.0
```

Error found:&#x20;

dpkg: error processing archive /var/cache/apt/archives/dotnet-sdk-8.0\_8.0.101-1\_amd64.deb (--unpack): cannot copy extracted data for './usr/share/dotnet/templates/8.0.1/microsoft.dotnet.web.projecttemplates.8.0.8.0.1.nupkg' to '/usr/share/dotnet/templates/8.0.1/microsoft.dotnet.web.projecttemplates.8.0.8.0.1.nupkg.dpkg-new': failed to write (No space left on device) No apport report written because the error message indicates a disk full error Errors were encountered while processing: /var/cache/apt/archives/dotnet-sdk-8.0\_8.0.101-1\_amd64.deb E: Sub-process /usr/bin/dpkg returned an error code (1)

{% embed url="https://stackoverflow.com/questions/69741113/increase-the-root-volume-hard-disk-of-ec2-linux-running-instance-without-resta" %}

