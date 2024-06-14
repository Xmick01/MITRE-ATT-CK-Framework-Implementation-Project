# MITRE-Attack-Framework

## Objective

The MITRE ATT&CK Framework Project aimed systematically improve an organization’s threat detection, response, and overall cybersecurity defenses by leveraging the MITRE ATT&CK Framework to identify, understand, and mitigate adversary tactics and techniques.

### Skills Learned

- **Threat Intelligence Analysis**: Analyze and interpret data to understand adversary behavior, tactics, techinquesm and procedures (TTPs)
- **Incident Detection and Response**: Identifying security incidents and responding to them to mitigate damage and prevent future incidents.
- **Gap Analysis and Risk Assessment**: Evaluating current security measures, identify weaknesses, and assess the risk associated with these gaps.
- **Red Teaming and Purple Teaming**: Conducting simulated attacks to test the effectiveness of security measures and collaboration between offensive and defensive security operations.
- **Security Operations Center Management**: Management of SOC processes, tools, and personnel to ensure monitoring, detection, and response capabilities.

### Tools Used

- [VirtualBox](https://www.virtualbox.org/)
- [Splunk](https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html)
- [Atomic Redteam](https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam)
- [MITRE-ATT&CK](https://attack.mitre.org/) 


## Steps 1: Spin up Virtual Machine

* Download [VirtualBox](https://www.virtualbox.org/) and make sure at least 35 gb of space is allocated for the VM because on top of the space needed to run the VM and download apps, Splunk needs about 5000mb minimum in order to properly function.

![VM for MITRE](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/74509708-bb21-4842-be92-81e1d2baf71b)

## Steps 2: Download Splunk and Sysmon

* Download [Splunk](https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html) in the VM. Once again, Splunk requires takes up a bit of memory, so make sure there is space allocated ahead of time.

* When everything is downloaded, the landing page for Splunk Enterprise should look like this:
  
![splunk landing page](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/47f1639c-66b3-44ee-8753-b701aa201381)

* After logging in, click on "Add Data", scroll down and click "Monitor", click "Local Event Logs", then select "Application, Security, and System".

![splunk settings](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/c62fc613-06bc-4530-98d8-a3f68c1027ed)
