# Day 1: Linux User Setup with Non-Interactive Shell

## Table of Contents

* Background
* Tasks
* Steps

### Background

To accommodate the backup agent tool's specifications, the system admin team at **xFusionCorp Industries** requires the creation of a user account with a **non-interactive shell**. This ensures the account can be used by the backup agent while preventing interactive logins.

### Tasks

Create a user named **john** with a **non-interactive shell** on **App Server 1**.

### Steps

1. Log in to **App Server 1** with administrative privileges.
2.  Create the user **john** with a non-interactive shell:

    ```bash
    sudo useradd -s /usr/sbin/nologin john
    ```
    <img width="642" height="292" alt="image" src="https://github.com/user-attachments/assets/8f29a361-53cf-4ebd-9023-eb5735da002f" />


    > If `/usr/sbin/nologin` is not available on the server, use `/sbin/nologin` instead.
3.  Verify that the user has been created successfully:

    ```bash
    id john
    ```
    
4.  Confirm that the assigned shell is non-interactive:

    ```bash
    grep '^john:' /etc/passwd
    ```
5. Verify that the shell is set to `/usr/sbin/nologin` (or `/sbin/nologin`).
   <img width="647" height="366" alt="image" src="https://github.com/user-attachments/assets/2311bbd5-5912-4e59-8322-6210e860d9d7" />


The user **john** has now been created with a non-interactive shell on **App Server 1**.

\#happylearning\
\#linux\
\#usermanagement\
\#systemadministration\
\#nologin\
\#backupagent\
\#xfusioncorp
