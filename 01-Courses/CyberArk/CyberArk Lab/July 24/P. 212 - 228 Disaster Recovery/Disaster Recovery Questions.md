#cyberark-labs 


**Topic 1: Disaster Recovery Phases & Pre-Configurations**

- **What** are the two primary phases of testing Disaster Recovery (DR) procedures covered in the lab guide? _(From page 212)_
- **What** specific user account was manually created by the implementation team during initial deployment to support the failback sequence? _(From page 212)_
- **What** strict warning does the guide give regarding the password of the built-in _DR_ user, and **why** must it not be altered? _(From page 213)_
- **Why** was automatic failover initially disabled and the DR user deactivated during the first days of the course? _(From page 213)_

---

**Topic 2: Triggering and Monitoring Failover Replication**

- **How** do you enable the built-in _DR_ user profile inside the PVWA _User Provisioning_ interface? _(From page 213)_
- **How** do you access and edit the `padr.ini` file on the _drvault01_ server, and **what** value must you verify for the `EnableFailover` parameter? _(From page 214, 215)_
- **How** do you manually force a full data replication from the Primary Vault to the DR Vault by modifying lines inside `padr.ini`? _(From page 215)_
- **How** do you use the Windows Services tool and a localized PowerShell log script (`padr_log.ps1`) to watch the replication process happen in real time? _(From page 215, 216)_
- **What** precise informational codes and success statements display at the tail end of the log script if metadata replication ends successfully? _(From page 216)_

---

**Topic 3: Executing Automatic Failover Tests**

- **How** do you intentionally execute an automatic failover test using the Remote Control Client utility? _(From page 217)_
- **What** occurs under the hood regarding system logs and failed connectivity attempts before the DR Vault officially enters failover mode? _(From page 218)_
- **How** do you verify via the Windows Services applet on the DR server that the automatic failover completed and the local vault engine successfully woke up? _(From page 219)_
- **How** do you structurally configure a single `Vault.ini` file layout for services like PVWA and PSM so they can automatically jump vaults without human intervention? _(From page 220)_
- **What** component role inside CyberArk is explicitly **NOT** configured for automatic failover during this architecture process? _(From page 220)_

---

**Topic 4: The Failback Process (Data Sync back to Primary)**

- **What** historical operational data must be handled before you safely shift your production environment back to the original primary server (_vault01_)? _(From page 221)_
- **How** do you use the classic PrivateArk Client user management tools to locate and uncheck the disable box for the _DR_Failback_ account? _(From page 221)_
- **How** do you adjust the `FailoverMode` parameter and remove log/timestamp configurations on the _vault01_ text configuration file to prep it for data sync? _(From page 222)_
- **What** layout indicator changes occur inside the modern PVWA _System Health_ dashboard window when _vault01_ assumes its staging role? _(From page 223)_

---

**Topic 5: Finalizing Manual Failback and Returning to Baseline**

- **How** do you configure `ActivateManualFailover` inside the text properties on _vault01_ to initiate a manual vault failback override? _(From page 224)_
- **Why** is dropping back to the Primary Vault without first executing this explicit manual failover sequence highly critical, and **what** issue can it cause? _(From page 225)_
- **How** does the CyberArk Vault Disaster Recovery service behave dynamically upon startup when `ActivateManualFailover` is turned on? _(From page 225)_
- **How** do you return the _drvault01_ server back into its secondary resting DR mode after the primary vault is fully active again? _(From page 226, 227)_
- **What** clean-up security step must you execute on both the _DR_ and _DR_Failback_ user profiles once the entire exercise concludes, and **why**? _(From page 228)_


- What is PADR? How? Purpose?
- What is Enable Failover?