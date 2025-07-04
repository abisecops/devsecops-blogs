---
icon: hand-back-point-right
---

# Indexes in Splunk

**What is an Index in Splunk?**

* An **index** is a storage container in Splunk where data is stored.
* Splunk indexes raw data and its metadata (like timestamps, source, etc.) for efficient search and analysis.
* Examples: `main` (default), `audit`, `internal`, or custom indexes you create for specific data sources.

**Key Index Types**

1. **Events Index**: Stores log or event data (most common type).
2. **Metrics Index**: Optimized for numerical data (e.g., performance metrics).
3. **Summary Index**: Stores processed results of scheduled searches for faster reporting.

Understanding and efficiently managing indexes ensures optimal data handling within Splunk.

<figure><img src="../../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

**All these are default indexes in splunk which can't be deleted or disabled.**

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

Still issue on searching. Wait let's fix this first.&#x20;

Adjust Splunk's Minimum Free Space Requirement

```bash
sudo nano /opt/splunk/etc/system/local/server.conf

```

<pre class="language-bash"><code class="lang-bash"><strong># Add or modify:
</strong>
[diskUsage]
minFreeSpace = 500

Copy code

</code></pre>

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

```bash
# save and restart
sudo /opt/splunk/bin/splunk restart

```

It's should work now. Please wait for a while and try a sample search index.

```
index="_internal"
```



<figure><img src="../../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

Waah! It's working now. Cool, we can move forward to our Splunk learning.

