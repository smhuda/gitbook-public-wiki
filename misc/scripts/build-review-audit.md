---
description: >-
  This script checks for various security settings / controls / policies applied
  on the host machine.
---

# Build Review Audit

### References:

* [https://github.com/Sikkandar-Sha/SEC-AUDIT](https://github.com/Sikkandar-Sha/SEC-AUDIT)

## **Security Audit**

**PowerShell Script for Windows Server Compliance / Security Configuration Audit**

This script checks for various security settings, controls, policies applied on the host machine. The script also tells what the recommended value of a setting, control, policy should be according to known security standards. This script comes in handy in situations where running automated configuration audit tools like Nipper or Nessus \(with configuration audit policy configured\) is not allowed.

To see a sample output of what the script will generate, see the sample\_output.txt file.

### **Usage**:

1. Open PowerShell with Administrator privileges.
2. Before executing the script ensure that the PowerShell Script Execution Policy is set to Unrestricted.
3. This can be done by running the command "Set-ExecutionPolicy Unrestricted -Force" in PowerShell.
4. Navigate to the script directory and run the script. \(.\build-review-audit.ps1\).
5. Once the script execution is complete, the output can be found in the script directory itself.

### Script:

{% embed url="https://gist.github.com/smhuda/e0e26d6358d24af89c051b4335d5f2f4" %}



