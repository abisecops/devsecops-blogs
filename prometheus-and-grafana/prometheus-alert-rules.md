---
description: Set alert rules for prometheus
cover: ../.gitbook/assets/image (174).png
coverY: 0
---

# Prometheus alert rules

Steps:&#x20;

1. Go to the path:&#x20;

```bash
cd /etc/prometheus
sudo nano prometheus
```

```yaml
global:
  scrape_interval: 10s

scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['0.0.0.0:9090']
rule_files:
  - alert.rules.yml
  - less.rules.yml
```

2. Make a yml file for high memory alerts: **alert.rules.yml**

```bash
ubuntu@ip-172-31-23-4:/etc/prometheus$ cat alert.rules.yml
groups:
  - name: memory_alerts
    rules:
      - alert: HighMemoryUsage
        expr: (process_resident_memory_bytes / process_virtual_memory_max_bytes) * 100 > 70
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "High Memory Usage Detected"
          description: "Memory usage is over 70%: {{ $value }}"

```

3. Make a yml file for less  memory alerts: **less.rules.yml**

```bash
ubuntu@ip-172-31-23-4:/etc/prometheus$ cat less.rules.yml
groups:
  - name: memory_alerts_less
    rules:
      - alert: LowMemoryUsage
        expr: (process_resident_memory_bytes / process_virtual_memory_max_bytes) * 100 < 70
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "Low Memory Usage Detected"
          description: "Memory usage is less than 70%: {{ $value }}"
ubuntu@ip-172-31-23-4:/etc/prometheus$
```

4. **Verify the Configuration**

```bash
promtool check config prometheus.yml
```

5. Restart the Prometheus service:&#x20;

```bash
sudo systemctl restart prometheus
```

6. Now check on your prometheusip:9090. (Default port of prometheus is 9090).&#x20;

* Check on alerts you can get alerts which alerts rule is firing.&#x20;

<figure><img src="../.gitbook/assets/image (174).png" alt=""><figcaption></figcaption></figure>
