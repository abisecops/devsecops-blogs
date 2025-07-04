---
icon: magnifying-glass
---

# Basic Searching

Splunk uses its **Search Processing Language (SPL)** to query data stored in indexes. A basic search allows you to:

* Retrieve events from specific indexes.
* Filter results based on keywords or fields.
* Analyze data using commands and visualizations.

### Some important indexes for trouble shooting

#### Internal access index

```
index=_internal

```

Search Internal Logs by Component

* `source` or `sourcetype`

`Here we can define the source of the logs.`

**Search Logs**:

```
index=_internal source=*scheduler.log

```

**Indexer Logs**:

```
index=_internal source=*splunkd.log

```

<figure><img src="../../../.gitbook/assets/image (197).png" alt=""><figcaption></figcaption></figure>

**We can also define the search on our ondemanded time basis as well as realtime too.**

<figure><img src="../../../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>

