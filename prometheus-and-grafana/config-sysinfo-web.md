---
description: Lightweight web based process viewer built on top of sysinfo
cover: ../.gitbook/assets/image (175).png
coverY: 0
---

# Config sysinfo-web

#### Prerequisites:

a) Linux

b) Rust (installed)&#x20;

1. #### Visit the given link for details:

{% embed url="https://crates.io/crates/sysinfo-web" %}
Crates packages on Rust
{% endembed %}

```bash
cargo install --git https://github.com/onur/sysinfo-web
cd /home/ubuntu/.cargo/bin
./sysinfo-web 0.0.0.0:3200 # 3000 is the default port of this service
```

2. #### Now, you can access the service on your port 3200. Make sure 3200 port be open on your instance.

{% embed url="http://dashboardapi.hicare.in:3200/" %}

<figure><img src="../.gitbook/assets/image (175).png" alt=""><figcaption><p>dashboardapi.hicare.in:3200</p></figcaption></figure>
