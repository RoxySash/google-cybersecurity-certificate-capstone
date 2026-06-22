# google-cybersecurity-certificate-capstone
My challenge was to examine the vulnerabilities in Google Cloud Security Command Centre, shut the old VM down and create a new VM before the malware infection. Afterwhich the cloud storage permissions were corrected and/or removed. Firewalls were implemented and a compliance report was generated.

# Executive summary
The security team detected unusual activity within the cloud environment. This was investigated, and it was confirmed that a compromise had occurred across the multiple cloud resources, which led to sensitive information being compromised for all users. An investigation was conducted to gather information about this breach.

This breach occurred because of vulnerabilities in firewall settings, buckets, and virtual machines VMs these vulnerabilities were exploited. 
The initial virtual machine instance was infected with malware. This machine had a default service account that had full access to APIs, and the bad actor was able to successfully compromise this service account, which granted them unauthorized access to the virtual machine.

Having gained access, they targeted BigQuery by leveraging compromised credentials, where they gained access to sensitive credit card information. After which, they used a storage bucket with public internet access enabled to exfiltrate the data. 

## Investigation
A comprehensive investigation was conducted to determine the nature and extent of the compromise. The following findings were identified:

1. **Malware infection:** Forensic analysis confirmed the presence of malware on the compromised VM. The specific type and variant of the malware were identified through in-depth analysis, providing insights into the attacker's techniques and potential motivations.
2. **Unauthorized access:** Evidence revealed that the attacker gained unauthorized access to the compromised VM by exploiting open RDP and SSH services. The access logs and network traffic analysis provided crucial insights into the attacker's entry point and their subsequent activities.
3. **Privilege escalation:** The forensic examination indicated that the attacker leveraged the compromised VM to escalate privileges and gain access to sensitive systems and resources. Through the exploitation of user and service account credentials, the attacker was able to move laterally within the network and target additional services; in particular gaining unauthorized access to BigQuery.
4. **Data exfiltration:** The forensic analysis confirmed the exfiltration of credit card information, including card numbers, user names, and associated locations. The attacker utilized a storage bucket with public internet access to initiate and facilitate the exfiltration, exporting the compromised data for later remote retrieval.

The findings provide valuable insights into the attack, enabling the incident response team to understand the attack vector, the attacker's actions, and the compromised data. These findings will serve as crucial evidence for further investigations, remediation efforts, and future cybersecurity enhancements.

## Response and remediation
To effectively remediate the incident, a series of actions was taken in alignment with industry best practices. The following outlines the containment, eradication, and recovery measures implemented:

## Containment and eradication measures
**Removed the public storage buckets:** Public access was removed from the storage bucket, and the permissions for the buckets were changed to uniform bucket-level access.<br>
**Isolate the compromised VM:** The VM cc-app-01 was identified as the infected VM. It was shut down and deleted. A new VM was created from an uninfected snapshot. A configuration to use a private IP address was set up, and secure boost was enabled.<br>
**RDP and SSH access were restricted:** The firewalls were adjusted to restrict SSH access to only a specific IP range, and firewall logging was enabled.

## Recovery measures
**Restore from trusted snapshots:** A prior snapshot was taken prior to this incident, and the new VM was restored from this previous snapshot.<br>
**Improved monitoring of all logging:** Strengthened the monitoring by implementing real-time log analysis, which enables us to identify unauthorized access or any suspicious activities.<br> 
**Security configurations were reviewed:** All misconfigurations and weaknesses were identified and remediated, including VMs, storage buckets, and network infrastructure.

By implementing these measures, the security team successfully mitigated the immediate risks, removed the attacker's presence, and restored affected systems to a secure and operational state.

## Recommendations
This incident provided valuable lessons that can inform future cybersecurity practices and help prevent similar incidents. The following are recommendations that we suggest be implemented to mitigate similar attacks from happening in the future:

**Regular risk assessment should be done:** Periodic risk assessment should be done by the organizations on the data assets, networks, systems, and applications. This will find out what the system's vulnerabilities are and how to mitigate them before a bad actor learns of these flaws.<br>
**Conduct a pen-test:** Before malicious actors can exploit vulnerabilities, penetration testing should be done periodically to identify vulnerabilities or security issues.<br>
**Multifactor authentication:** An additional layer of security should be added to all accounts in case the passwords are compromised.<br> 
**Permissions should be least privilege:** Privileges should be reviewed regularly, and unnecessary access should be removed if it's not necessary to perform their job.

### By SR Hedge
