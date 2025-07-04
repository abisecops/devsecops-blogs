---
description: AWS System Manager (Patch Manager)
---

# Patch Manager

Today we are going to learn on  Patch Manager on AWS.

This era is the era of automation, as we believe: "There is no place like 127.0.0.1" . But after all, you can give some effect to secure the system. As all infra are being switched to cloud. We're going to secure the AWS system from Patch Manager. It's included as part of the AWS Systems Manager suite of services.

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

Patch Manager:&#x20;

Patch Manager is a feature of AWS Systems Manager which automates the patching process for managed nodes with both security and other types of updates for operating systems and applications.

[Supported Systems: ](https://docs.aws.amazon.com/systems-manager/latest/userguide/patch-manager-prerequisites.html)

* **Linux**
  * AlmaLinux 8.3–8.7, 9.0–9.2
  * Amazon Linux 2012.03–2018.03
  * Amazon Linux 2 version 2.0 and all later versions
  * Amazon Linux 2022
  * Amazon Linux 2023
  * CentOS 6.5–7.9, 8.0–8.5
  * CentOS Stream 8
  * Debian Server 8.x, 9.x, 10.x, 11.x, and 12.x
  * Oracle Linux 7.5–8.7, 9.0 - 9.2
  * Raspberry Pi OS (formerly Raspbian) 9 (Stretch)
  * Red Hat Enterprise Linux (RHEL) 6.5–8.9, 9.0–9.3
  * Rocky Linux 8.4–8.7, 9.0–9.2
  * SUSE Linux Enterprise Server (SLES) 12.0 and later 12.x versions; 15.0 - 15.5
  * Ubuntu Server 14.04 LTS, 16.04 LTS, 18.04 LTS, 20.04 LTS, 20.10 STR, 22.04 LTS, and 23.04
* **macOS**
  * 11.3.1; 11.4–11.7 (Big Sur)
  * 12.0–12.6 (Monterey)
  * 13.0–13.5 (Ventura)
  * 14.0 (Sonoma)
  * macOS OS updates: Patch Manager doesn't support OS updates or upgrades for macOS. Use Apple's built-in OS upgrade mechanisms.
  * Homebrew support: Discontinued for macOS 10.14.x (Mojave) and 10.15.x (Catalina).
  * Region support: Not supported in all AWS Regions.
  * macOS edge devices: SSM Agent for AWS IoT Greengrass core devices is not supported.
* **Windows**
  * Windows Server 2008 through Windows Server 2022, including R2 versions.
  * Windows 10: SSM Agent for AWS IoT Greengrass core devices not supported.
  * Windows Server 2008: No longer supported for feature or security updates from Microsoft.
  * Windows Server 2012 and 2012 R2: Reached end of support on October 10, 2023. Recommended to use Extended Security Updates (ESUs) from Microsoft.

Patch Manager pricing is based on the number of managed instances and the number of patches installed on those instances. AWS Systems Manager Patch Manager is offered at no additional charge beyond the standard pricing for AWS Systems Manager.This means you can automate patch management without worrying about extra fees, helping you maintain the security of your AWS infrastructure efficiently and affordably.

