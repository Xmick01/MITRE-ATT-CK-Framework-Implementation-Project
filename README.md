# MITRE-Attack-Framework

## Objective

The MITRE ATT&CK Framework Project aimed systematically improve an organization’s threat detection, response, and overall cybersecurity defenses by leveraging the MITRE ATT&CK Framework to identify, understand, and mitigate adversary tactics and techniques.

### Skills Learned

- **Threat Intelligence Analysis**: Analyze and interpret data to understand adversary behavior, tactics, techinques and procedures (TTPs)
- **Incident Detection and Response**: Identifying security incidents and responding to them to mitigate damage and prevent future incidents.
- **Gap Analysis and Risk Assessment**: Evaluating current security measures, identify weaknesses, and assess the risk associated with these gaps.
- **Red Teaming**: Conducting simulated attacks to test the effectiveness of security measures.
- **Security Operations Center Management**: Management of SOC processes, tools, and personnel to ensure monitoring, detection, and response capabilities.

### Tools Used

- [VirtualBox](https://www.virtualbox.org/)
- [Splunk](https://www.splunk.com/en_us/download/splunk-enterprise/thank-you-enterprise.html)
- [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) and the [Sysmon config](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml)
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

* Download [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) and the [Sysmon config](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml)
* Go into powershell as admin and change the directory to where the Sysmon and its config file are.
  ![sysmon](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/cb4e39b8-1f80-42b4-9620-ac0c25825bfa)

* Next, run the config file and a license agreement should pop up.

  ![sysmon user agree](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/7e226939-01cf-43ba-ab88-3b05f6cbbb4d)

* After agreeing to the license agreement, double-check to make sure sysmon is on the system. Do this by going to Services and scrolling until you see sysmon.
  
  ![double check sysmon ](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/0e5b2fd5-1640-4aef-9fef-c4d2c0d61426)

## Steps 3: Download Atomic RedTeam 

* First, open up Powershell and set execution policy for the current user. This way, powershell will be able to run scripts.

  ![Bypass execution policy](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/aa6d9850-24f1-4969-bfba-adf58ca5bf6c)
  
* Then, copy and paste the [Atomic Redteam](https://github.com/redcanaryco/invoke-atomicredteam/wiki/Installing-Invoke-AtomicRedTeam)

  IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing);
Install-AtomicRedTeam

![install atomic redteam](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/f70d7b14-404e-4354-96c4-9be792ee8a11)

* Windows Defender might trigger because of this, so navigate to Windows Defender and set an exclusion for Atomic RedTeam.

![atomic red team exclusion](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/35de3bd8-c80a-46db-ab7f-628df4cc9b5d)

* After that is done, go back to the Powershell and force install Atomic RedTeam using Install-AtomicRedTeam -getAtomics -Force

![force install atomic red team](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/9292f4c8-d592-46fb-904c-209091caf8af)

* Using Invoke_AtomicTest ALL -ShowDetailsBrief to get a list of technique IDs

 ![Technique ID list](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/921becd4-770d-4dc1-be92-6a5ca1536597)
   
   * **Mimikatz was the malware used in my [SOC-Automation-project!](https://github.com/Xmick01/SOC-Automation-Project-)**
 
## Steps 3: Use MITRE ATT&CK to ID TTPs

* Go to [MITRE ATT&CK](https://attack.mitre.org) and see which applicable technique IDs you want to analyze.

![mitre attck matrix](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/807c9686-099f-46de-9b94-84c184a24861)

* For this project, bits will be the technique used to get telemetry in Splunk.

![bits ID](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/3efae903-413d-42b9-bc74-c965581935e2)

* Go to Powershell and run the script Invoke-AtomicTest T1197 to run the malware on the VM.

![bits ID script](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/7ce00b57-e12c-46af-b0cd-675615a3f1d4)

* Switch to Splunk and see if any telemetry was generated

![splunk telemetry](https://github.com/Xmick01/MITRE-ATT-CK-Framework-Implementation-Project/assets/130627895/1c098a9f-e1e8-4cce-88a2-82db913b72a3)

