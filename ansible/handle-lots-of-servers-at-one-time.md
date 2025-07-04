# Handle lots of servers at one time

As a devops engineer, I have to handle, config, and monitor different linux servers at the same time. While connecting the servers ssh, remembering all those pemfiles and hosted IP makes little bit awkward.&#x20;

So I have one master server where I manage all pemfiles and connect quickly and easily. I'll show how I perform such task easily today.&#x20;

First of all I should have pemfiles of child server, and master server.&#x20;

```
ssh-keygen -t rsa
ssh-copy-id -i ~/.ssh/id_rsa.pub badmin@192.168.2.58
```

Now time to add the host on ssh-config file:&#x20;

```
sudo nano ~/.ssh/config
```

```
Host master
  HostName 192.168.2.58
   User badmin

```

```
ssh badmin
```

Now you have successfully config for master server **badmin**:

After getting connected to master server. Time to config others too:&#x20;

```
Host autodeploy
    HostName 13.127.143.152
    User ubuntu
    IdentityFile ~/Documents/pemfiles/development/development.pem

Host portal
    HostName portal.in
    User ubuntu
    IdentityFile ~/Documents/pemfiles/portalapi/portal.pem

Host rnd
  HostName 192.168.2.87
   User uat

Host mobileapi
    HostName 3.111.219.167
    User ubuntu
    IdentityFile ~/Documents/pemfiles/mobileapi/mobileapi.pem

Host product
    HostName 3.109.136.192
    User ubuntu
    IdentityFile ~/Documents/pemfiles/product_server/product.pem

```

* Make sure you have given correct pemfiles, username and hostname properly. You can change hosts as per your requirements.

Now you can access servers without any burden.&#x20;

```bash
ssh autodeploy #autodeploy server
ssh portal #portal server
ssh rnd #uat server
ssh mobileapi #mobile api server
ssh product #productserver

```

The best part is that you don't need to connect ssh with hostname and pemfiles and this process also makes your task more smoothly.&#x20;

I personally suggest to use **tmux : terminal multiplex** for your daily tasks.&#x20;

```bash
tmux new -s autodeploy
ssh autodeploy
```

Now, ctrl + b then press d to Disattach the session from terminal.  But your tasks will run in background.

Then, you can also try again for another server:&#x20;

```
tmux new -s portal
ssh portal
```

Same as the autodeploy you can disattach the session.&#x20;

Later, if you want to attach the previous session, you can try this command:&#x20;

```
tmux attach -t autodeploy // to attach autodeploy server again
```

Disattach is same **ctrl + b then type d** .&#x20;

This is the way, you can handle lots of linux server at the same time. This is the easiest and simplest form too manager servers.&#x20;
