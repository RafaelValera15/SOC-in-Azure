# SOC-in-Azure
Building a SOC &amp; Honeynet in Azure


# Building a Honeynet + SOC in Azure (Live Traffic)

![image](https://github.com/user-attachments/assets/cccb7ae1-177d-4ef8-aed2-db85c920e3d2)


## Azure Architecture for Lab

### Introduction

In this project, I built a Honeynet and a Security Operations Center (SOC) within the Microsoft Azure cloud environment. The goal was to simulate an insecure cloud environment, expose it to the public internet, and monitor real-time attacks. I followed the NIST SP 800-61 guidelines for Incident Response and applied security controls to measure the impact on the environment's security posture.

### Here's what I did in this project:

1. **Create a Honeynet**:  
   I started by setting up a decoy network within Azure and exposing it to the public internet. This setup enticed real hackers to attack my resources.

2. **Build a Cloud Security Operations Center (SOC)**:  
   I built a monitoring and response center to observe and analyze threat actors targeting my honeynet resources.

3. **Apply the Incident Response Lifecycle**:  
   As the honeynet generated security alerts, I followed NIST SP 800-61 guidelines to address them and improve my response.

4. **Implement Security Controls**:  
   I applied security controls based on NIST's guidelines to bolster my honeynet's security posture and measure the effectiveness of those changes.

5. **Metrics Collection**:  
   I ran the insecure honeynet for 24 hours and collected metrics to understand its security posture. After implementing security controls, I waited another 24 hours and collected metrics again to observe how these changes impacted the security of the honeynet.

---

### Architecture Before and After Hardening / Security Controls

#### **Before Hardening (Insecure Honeynet)**
![Screenshot 2024-06-08 151051](https://github.com/user-attachments/assets/a4ba1f6a-40ee-43be-809c-caafa4ae7cf2)



In the insecure environment, the architecture consisted of the following components:

- Virtual Network (VNet)
- Network Security Groups (NSGs)
- Virtual Machines (2 Windows, 1 Linux)
- Log Analytics Workspace
- Azure Key Vault
- Azure Storage Account
- Microsoft Sentinel (SIEM)

**Technologies and Components Used**:
- Security Operations Center (SOC)
- Microsoft Defender for Cloud (MDC)
- NIST SP 800-53 Revision 5
- NIST SP 800-61 Revision 2
- Windows Event Viewer
- Kusto Query Language (KQL)
- Windows Remote Desktop for Remote Access
- Command Line Interface (CLI) for System Management
- PowerShell for Automation and Configuration Management

#### **After Hardening (Secured Honeynet)**
![image](https://github.com/user-attachments/assets/b71d3b2d-7713-476c-b199-25967b524c2f)


After applying security controls, the following changes were made:
- Network Security Groups (NSGs) were configured to block all traffic except from the admin workstation.
- NSGs were applied at the subnet level for additional protection.
- Windows built-in firewall was enabled.
- Private endpoints were implemented for Azure resources such as Key Vault and Blob Storage Account.

---

  ### Metrics Collected (Before Hardening / Security Controls)

| Metric                                | Count   |
|---------------------------------------|---------|
| **SecurityEvent**                     | 42,754  |
| **Syslog**                            | 3,636   |
| **SecurityIncident**                  | 117     |
| **AzureNetworkAnalytics_CL**          | 35,805  |

---

### Attack Maps (Before Security Controls)

- **Failed Windows RDP Logon Attempts**  
![image](https://github.com/user-attachments/assets/0e4fd2f1-0ce3-403f-ae1f-28960e3bb7fc)

- **Failed Linux Logon Attempts**  
![image](https://github.com/user-attachments/assets/5b83a8ab-2369-499f-a15a-5108b38877d0)

- **External Traffic Allowed into the Network by NSGs**  
![image](https://github.com/user-attachments/assets/71357be9-2eee-46ad-9a73-05cf095840d7)

- **Microsoft SQL Server Logon Attempts**  
![image](https://github.com/user-attachments/assets/3d243603-ccdf-4339-b8b6-0cd6060ff705)

---

### Attack Maps (After Security Controls)

After hardening, no instances of malicious activity were observed. Therefore, all map queries returned no results.

---

### Metrics Collected (After Hardening / Security Controls)

| Metric                                | Count   |
|---------------------------------------|---------|
| **SecurityEvent**                     | 12,159  |
| **Syslog**                            | 1       |
| **SecurityIncident**                  | 0       |
| **AzureNetworkAnalytics_CL**          | 0       |

---

### Impact of Security Controls

| Metric                                | Percentage Change  |
|---------------------------------------|--------------------|
| **SecurityEvent**                     | -71.56%            |
| **Syslog**                            | -99.97%            |
| **SecurityIncident**                  | -100%              |
| **AzureNetworkAnalytics_CL**          | -100%              |

---

### Conclusion

This project allowed me to build a Honeynet and a Cloud SOC in Azure, simulating real-world attacks and responding according to the NIST guidelines. I learned how to enhance security by hardening a cloud environment and reducing attack surface. The metrics clearly show that implementing security controls drastically improved the environment's security posture.

This project not only deepened my incident response skills but also provided a hands-on experience with Azure cloud security.

---

### How to Run This Lab

If you want to replicate this project, follow the steps below:

1. **Create Azure Resources**: Set up a Virtual Network, NSGs, Virtual Machines (Windows & Linux), Key Vault, Storage Account, and Microsoft Sentinel.
2. **Expose Resources to the Internet**: Initially, do not configure any security rules to simulate an insecure environment.
3. **Monitor Traffic**: Use Azure Network Analytics and Sentinel to monitor network traffic and collect logs.
4. **Implement Security Controls**: Follow the steps in the project to apply NSG rules, enable firewalls, and implement private endpoints.
5. **Compare Metrics**: After hardening, compare the security metrics to observe the impact of your changes.

---


