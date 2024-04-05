## Microsoft Azure SOC and HoneyNet


<p align="center">
  
  ![image0](https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/7770e4ef-5d17-465e-921a-886233f00f43)

</p>



## Summary

For this project, I built a HoneyNet and SOC in Microsoft Azure. To accomplish this, I provisioned all of the resources necessary for a cloud infrastructure including virtual machines, flow logs for each VM, a log analytics workspace to ingest the log data, a key vault, a storage account, vnets, network security groups and a SIEM (Azure Sentinel). After provisioning, I left the resources exposed to the internet in order to gather attack data for 24 hours. The environment was then hardened and left on for another 24 hours. Finally, I gathered log data and created a spreadhseet to show the change in traffic patterns in the 24 hour period after the environment was hardened.
<br />
<br />


## Environments and Architecture Technologies Used

- Microsoft Azure (Cloud Platform)
  - Resource Groups
  - Azure Virtual Machines (2 Windows, 1 Linux)
  - Log Analytics Workspace
  - Azure Sentinel (SIEM)
  - Key Vault
  - Storage Account
  - Network Security Groups
  - Microsoft Defender for Cloud (Cloud-native Application Protection Platform (CNAPP))
  
 - Remote Desktop Protocol (Used for logging in to the VMs)
 - OSB Studio (For recording some my labs showcasing the procedures)
 
 ## Security Metrics Used for Queries in the Log Analytics Workspace
 
 - Syslog (For Linux Event Logs)
 - SecurityIncident (For Sentinel Created Incidents)
 - SecurityAlert (For Alerts Triggered in the Log Analytics Work Space)
 - AzureNetworkAnalytics_CL (For Malicious Events Triggered)
 - SecurityEvent (For Windows Event Logs)
 <br />
 <br />
 
 Click below for the exercise details:
 
 <details close>

<div>

</summary>
 
 
  ## Architecture Before Hardening
  
  Before hardening, all resources were exposed to the internet with public endpoints and the Network Security Group firewalls were wide open.
  <br />
  <br />
![image1](https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/4b8e489c-e5df-4922-9604-f2c72ddc14ec)

  <br />
  <br />
  
 ## Attack Maps Before Environment Hardening 
 These maps show malicious traffic attempting to penetrate the Azure environment before security controls were implemented. 
 
<img width="1000" alt="ghfxhfcdfjh" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/881d9df8-054c-4911-a72b-2e15ccb6fd05">

  <br />
  <br />
  
<img width="1000" alt="Capture" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/cc40080d-aca0-4e55-aadc-22fc4a2ec616">

  <br />
  <br />
 <img width="1000" alt="kkkk" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/84e4d1ff-c2dd-4744-93b0-8972e2e4bac2">

  <br />
  <br />
  
  ## Metrics Before Implementing Security Controls
  
  The below table displays the metrics that were measured while the environment was insecure for 24 hours:
  
<img width="517" alt="before" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/21f0937c-05fb-4c8d-8e81-41bf5a042d07">

  
  <br />
  <br />
  
  Click below to see the details of the environment after hardening:
  
  <details close>
  
  
  ## Architecture After Hardening
 
  
  After hardening, the VMs had their exposed ports (RDP/SSH) closed, the resources were all secured behind firewalls and a v-net with it's own network security group. Firewall rules were then set to only allow my workstation PC to access any of the resources in the environment for purposes of gathering log traffic data.
  <br />
  
![image2](https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/de12f7a3-7ca9-4cd7-871a-38c2388603a9)

  <br />
  <br />
  
   ## Metrics After Implementing Security Controls 
   
   The below table displays the metrics that were measured after the environment was hardened with security controls for 24 hours.
  
<img width="517" alt="after" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/3061cd13-aed8-410a-b8d7-3e3db4121df8">

  <br />
  <br />
  
 ## Rate of Change
 
 As can be seen in the below chart, the incidents dropped significantly when the environment was hardened. Had I ran the controls even longer no doubt the incidents would have decreased even more.
 
 <img width="517" alt="Change" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/a40c5e81-9b9b-4cdc-b472-d343a8695eec">

 <br />
 <br />
 
 ## NIST Utilization as a Guideline for Security Controls


<img width="446" alt="NIST" src="https://github.com/Pranavnathan23/Azure-SOC/assets/163876627/912ae6f3-35dc-45ba-a302-43c5f22fb99f">

 <br />
 <br />
 
 Utilizing the following steps, an organization handling any high priority incident can do so using the NIST 800-61 guide successfully:
 
 - Step 1: Preparation: (In this lab I prepared by setting up a log analytics workspace to log traffic coming into the HoneyNet, I configured Azure Sentinel (SIEM) and set up alerts to be triggered when incidents did occur.
 
 - Step 2: Assigning the incident to someone, setting the status (Low, Medium, High), inspecting the logs, investigating the incident to determine if it is a false positive or true positive and to determine the scope (it's affect on the environement or network).
 
 - Step 3: Using the Incident Response Playbook to catalog the details of the incident (basically the who, what, when, where, why and how) 
 
 - Step 4: Document the Findings and Close Out
 <br />
 <br />
 
 ## Cost Analysis
 
 ![Lab Cost](https://imgur.com/jN51Kle.png)
 <br />
 <br />
 
 My total cost for this excercise was about 30USD. Had I turned off my VMs nightly the cost would be less but the traffic would have stopped being ingested by the logs. The forecasted cost was $130USD had I left all of the resources running for one full month.
 <br />
 <br />
 
  ## Conclusion
  
  In this project I constructed a honeynet in Microsoft Azure with log sources that were integrated into a log analytics workspace. I also deployed Azure Sentinel in order to trigger alerts and incidents based on the log data from the log analytics workspace. There were metrics measured 24 hours after the creation of all insecure resources and then 24 hours after implementing security controls. As seen in the metric data tables there was a dramatic drop in incidents because security controls were put in place which illustrates their effectiveness.
  
 Please note: This project was done in a controlled environment so results will vary based on applied situation.  
  
  
