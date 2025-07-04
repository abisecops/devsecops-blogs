# Unexpected Absence of .NET Core Runtime

Dotnet framework is missing unexpectedly in Ubuntu server.&#x20;

```bash
cat syslog.2 | grep "dotnet"
```

```bash
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounting Mount unit for dotnet-runtime-80, revision 12...
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounting Mount unit for dotnet-runtime-80, revision 13...
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounting Mount unit for dotnet-sdk, revision 232...
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounting Mount unit for dotnet-sdk, revision 235...
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounted Mount unit for dotnet-runtime-80, revision 12.
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounted Mount unit for dotnet-runtime-80, revision 13.
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounted Mount unit for dotnet-sdk, revision 232.
Feb 15 05:15:02 ip-172-31-31-240 systemd[1]: Mounted Mount unit for dotnet-sdk, revision 235.
Feb 15 05:15:02 ip-172-31-31-240 snapd-apparmor[278]: main.go:124: Loading profiles [/var/lib/snapd/apparmor/profiles/snap-confine.snapd.20290 /var/lib/snapd/apparmor/profiles/snap-confine.snapd.20671 /var/lib/snapd/apparmor/profiles/snap-update-ns.amazon-ssm-agent /var/lib/snapd/apparmor/profiles/snap-update-ns.dotnet-runtime-80 /var/lib/snapd/apparmor/profiles/snap-update-ns.dotnet-sdk /var/lib/snapd/apparmor/profiles/snap-update-ns.lxd /var/lib/snapd/apparmor/profiles/snap.amazon-ssm-agent.amazon-ssm-agent /var/lib/snapd/apparmor/profiles/snap.amazon-ssm-agent.ssm-cli /var/lib/snapd/apparmor/profiles/snap.dotnet-runtime-80.dotnet /var/lib/snapd/apparmor/profiles/snap.dotnet-sdk.dotnet /var/lib/snapd/apparmor/profiles/snap.lxd.activate /var/lib/snapd/apparmor/profiles/snap.lxd.benchmark /var/lib/snapd/apparmor/profiles/snap.lxd.buginfo /var/lib/snapd/apparmor/profiles/snap.lxd.check-kernel /var/lib/snapd/apparmor/profiles/snap.lxd.daemon /var/lib/snapd/apparmor/profiles/snap.lxd.hook.configure /var/lib/snapd/apparmor/profiles/snap.lxd.hook.install /var/lib/snapd/apparmor/profiles/snap.lxd.hook.remove /var/lib/snapd/apparmor/profiles/snap.lxd.lxc /var/lib/snapd/apparmor/profiles/snap.lxd.lxc-to-lxd /var/lib/snapd/apparmor/profiles/snap.lxd.lxd /var/lib/snapd/apparmor/profiles/snap.lxd.migrate /var/lib/snapd/apparmor/profiles/snap.lxd.user-daemon]
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: App: /var/www/hicare_sc_sfdctosqs/HiCare.Run.SC.SalesforceToSQS.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[390]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: App: /var/www/hicare_sc_sqstorun/HiCare.Run.SC.SQSToRUN.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[391]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: App: /var/www/hicare_resource_sfdctosqs/HiCare.Run.Resource.SalesforceToSQS.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[387]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: App: /var/www/hicare_resource_sqstorun/HiCare.Run.Resource.SQSToRun.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[389]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: App: /var/www/hicare_task_sfdctosqs/HiCare.Run.Task.SalesforceToSQS.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[393]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: App: /var/www/hicare_task_runtosqs_reverse/HiCare.Run.Task.RUNToSQSReverseSync.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[392]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: You must install or update .NET to run this application.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: App: /var/www/hicare_task_sqstorun/HiCare.Run.Task.SQSToRUN.dll
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: Architecture: x64
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: Framework: 'Microsoft.NETCore.App', version '8.0.0' (x64)
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: .NET location: /usr/share/dotnet/
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: No frameworks were found.
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: Learn more:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: https://aka.ms/dotnet/app-launch-failed
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: To install missing framework, download:
Feb 15 05:15:02 ip-172-31-31-240 dotnet[394]: https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=8.0.0&arch=x64&rid=linux-x64&os=ubuntu.22.04
```

#### Reason behind the issue is: `snapd-apparmor.`

&#x20;**This component is part of the snapd system and is responsible for generating and managing AppArmor profiles for snap packages. Each snap package typically has its own AppArmor profile, which restricts its access to resources based on the confinement rules defined in the profile.**

**There are different affect of snapd-apparmor on the system:**&#x20;

* **In some cases, conflicts or compatibility issues may arise between AppArmor profiles and certain snap packages. These issues can lead to unexpected behavior, application failures, or security vulnerabilities if not properly addressed.**&#x20;
* **While this overhead is generally minimal, it can become noticeable on systems with limited resources or under heavy load.**

#### Solution:

The best solution to fix such issue is: reinstall dotnet framework, packages properly using apt  instead of snap.

#### For reference:&#x20;

[deploy-apis-on-nginx-webserver-in-ubuntu.md](../../nginx/deploy-apis-on-nginx-webserver-in-ubuntu.md "mention")
