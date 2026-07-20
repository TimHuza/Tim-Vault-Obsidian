The CACPM073E timeout error means ==the Central Policy Manager (CPM) failed to communicate with the target database or apply the password change within the allotted 30 seconds==. Resolve this by verifying network connectivity to `acme-123.acme.corp`, checking database listener ports, and increasing timeout thresholds in the platform policy. [[1](https://community.cyberark.com/s/article/00002629), [2](https://cybersecuritylearning.net/cyberark-cpm-cacpm073e/)]

Step-by-Step Troubleshooting

- **Verify Connectivity and Credentials:** Ensure the CPM server can reach the target host (`acme-123.acme.corp`), and verify that the Oracle listener port (typically 1521) is open and not blocked by a firewall. [[1](https://community.cyberark.com/s/article/00002629), [2](https://cybersecuritylearning.net/cyberark-cpm-cacpm073e/)]

- **Increase Timeout Settings:** Database password changes can take longer than 30 seconds. In the CyberArk Password Vault Web Access (PVWA), navigate to **Administration > Platform Management**, edit the target platform (Oracle), and adjust the following parameters in _Automatic Password Management_ > _Privileged Access Manager_:
    - **Timeout:** Increase from `30` to `60` or `90` seconds.
    - **PromptTimeout:** Adjust to `20` or `30` seconds. [[1](https://www.reddit.com/r/CyberARk/comments/1cj2way/password_verification_issue/), [2](https://community.cyberark.com/s/article/00002629)]

- **Verify Reconcile Account:** If the process involves a reconcile account, ensure the reconcile credentials used by the CPM are valid and have sufficient privileges to alter the `Database-OraDba30-acme-123` account. [[1](https://community.cyberark.com/s/article/Troubleshooting-CPM-Password-Reconciliation-Failure-Error-Code-CACPM406E), [2](https://www.reddit.com/r/CyberARk/comments/1h0cgpt/issue_in_reconciliation_of_the_linux_systems/)]

- **Restart CPM Service:** After saving platform changes, restart the **CyberArk Central Policy Manager Service** on the CPM server so the new timeout values take effect immediately. [[1](https://www.reddit.com/r/CyberARk/comments/1cj2way/password_verification_issue/), [2](https://community.cyberark.com/s/article/00002629)]