---
description: Using Amazon Lightsail for ASP.NET Core
---

# Amazon Lightsail for ASP.NET Core



<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption><p>Instance running for lightsail </p></figcaption></figure>

Steps I did after creating instance

```bash
# Providing permission
chmod 400 pemfile.pem
ssh -i  #pem_path user@ip

#after connected to the server
sudo su
root# passwd
New Password: 
root# sudo passwd user
New Password: 
root# sudo su user
user # cd /etc/ssh/
sudo nano sshd_config

# change no to yes here
PermitRootLogin yes

# change no probitted to yes
PasswordAuthentication yes

#saved
systemctl status ssh
systemctl restart ssh

#now you can connect your instance with any machine:
ssh user@ip
passwd
```

Now let's install nginx on the system after connecting instance.

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

```
sudo apt-get update
sudo apt-get install nginx
```

**Now time to install asp.net core**

```
sudo apt-get install -y dotnet-sdk-8.0
sudo wget -q https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

**Install the .NET Core Runtime**

```
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-2.1
```

&#x20;~~I got a error:~~&#x20;

```bash
$ sudo apt-get install aspnetcore-runtime-2.1
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 dotnet-runtime-deps-5.0 : Depends: libssl1.0.0 but it is not installable or
                                    libssl1.0.2 but it is not installable or
                                    libssl1.1 but it is not installable
 dotnet-sdk-5.0 : Depends: netstandard-targeting-pack-2.1 (>= 2.1.0) but it is not installable
                  Depends: dotnet-targeting-pack-5.0 (>= 5.0.0) but it is not installable
                  Depends: aspnetcore-targeting-pack-5.0 (>= 5.0.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

Ubuntu 22.04 has upgraded libssl to 3 and does not propose libssl1.1

You can force the installation of libssl1.1 by adding the ubuntu 20.04 source:

```
echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list

sudo apt-get update
sudo apt-get install libssl1.1
```



Problem is fixed.&#x20;



This time I got next error.&#x20;

```
dotnet --info
```

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

**Solution**:

```bash
sudo rm /etc/apt/sources.list.d/microsoft-prod.list
sudo apt update
sudo apt install dotnet-sdk-7.0
```

<pre><code><strong>git clone https://githubprojectlink
</strong><strong>cd project
</strong><strong>dotnet publish -c Release -r linux-x64 --self-contained true
</strong></code></pre>

This also not worked:&#x20;

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption><p>Sucked here</p></figcaption></figure>

Tried with azure documentation for ec2 cli:&#x20;

```
dotnet new webapp -n myfirstdotnetapp --framework net7.0
cd myfirstdotnetapp
dotnet run --urls=https://hostip:5001/
```

1\) It took so much time, so I tried to ctrl + c to exit and I got the error 1.

Error 1: error MSB6006

```
dotnet build --no-restore
```

2\)  It took too much time, after exiting from the command. I got the error 2.

Error 2: error MSB6006

