---
description: 'Documentation: https://prometheus.io/docs/introduction/first_steps/'
cover: https://i.ytimg.com/vi/NtPpeK0h_pI/maxresdefault.jpg
coverY: 0
---

# Prometheus Installation

Prometheus Download link: [https://github.com/prometheus/prometheus/releases/download/v2.49.0-rc.1/prometheus-2.49.0-rc.1.linux-amd64.tar.gz](https://github.com/prometheus/prometheus/releases/download/v2.49.0-rc.1/prometheus-2.49.0-rc.1.linux-amd64.tar.gz)

Steps:&#x20;

1\) Download from the given link:&#x20;

```bash
tar xvfz prometheus-*.tar.gz
cd prometheus-*
cat prometheus.yml
nano prometheus.yml

```

2\) Change the host IP in: `prometheus.yml`

3\) Config now: `./prometheus --config.file=prometheus.yml`

`Now we can access from given port. Default port is 9090.`

`Now download the Node Exporter from the given link` [https://github.com/prometheus/node\_exporter/releases/download/v1.7.0/node\_exporter-1.7.0.linux-amd64.tar.gz](https://github.com/prometheus/node_exporter/releases/download/v1.7.0/node_exporter-1.7.0.linux-amd64.tar.gz)

1\)&#x20;

```
wget https://github.com/prometheus/node_exporter/releases/download/v<VERSION>/node_exporter-<VERSION>.<OS>-<ARCH>.tar.gz
tar xvfz node_exporter-*.*-amd64.tar.gz
cd node_exporter-*.*-amd64
./node_exporter
```

`Now we can access from the port 9100.`



{% embed url="https://devopscube.com/install-configure-prometheus-linux/" %}



