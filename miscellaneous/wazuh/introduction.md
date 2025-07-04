# Introduction

&#x20;**Wazuh** is a free and open source security platform that unifies XDR and SIEM protection for endpoints and cloud workloads.

#### Use Cases of Wazuh

Wazuh can be used in various scenarios to enhance security across different environments:

1. **Intrusion Detection:** Monitor system activity and detect malicious behavior with real-time alerts.
2. **Log Data Analysis:** Collect, aggregate, and analyze log data from different sources to uncover potential threats.
3. **Vulnerability Detection:** Identify security vulnerabilities in systems and applications to take corrective actions.
4. **Compliance Monitoring:** Ensure adherence to compliance standards like GDPR, PCI DSS, and HIPAA by tracking file integrity and configuration changes.
5. **Incident Response:** Facilitate faster and more efficient incident response with comprehensive visibility and automated incident handling.
6. **Cloud Security:** Safeguard cloud workloads by implementing security controls tailored for cloud environments.
7. **Configuration Assessment:** Evaluate and enforce security configurations across different assets to maintain a secure posture.

#### Short Notes on Wazuh

* **Open Source:** Wazuh is a free and open source solution, accessible to a wide range of users.
* **Versatile Security:** It combines XDR and SIEM capabilities for comprehensive threat detection and management.
* **Multi-Environment Support:** Wazuh covers on-premises, cloud, and hybrid environments.
* **Real-Time Monitoring:** Provides real-time security monitoring and alerting.
* **User Community:** Benefit from a strong community for support and collaboration.

#### Components of Wazuh server&#x20;

* Wazuh Manager -> /var/ossec/etc/ossec.conf
* Filebeat OSS -> /etc/filebeat/filebeat.yml
* Wazuh Indexer -> etc/ wazuh-indexer/opensearch.yml
* Wazuh Dashboard

&#x20;-> /etc/wazuh-dashboard/opensearch-dashboards.yml

-> /usr/share/wazuh-dashboard/data/wazuh/config/wazuh.yml
