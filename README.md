#  Wazuh Deployment with File Integrity Monitoring (FIM) Implementation

<img width="1499" alt="Screenshot 2024-10-22 at 11 25 09" src="https://github.com/user-attachments/assets/531df2c3-8d41-4e94-bb9c-86abc502ae16">
<img width="1260" alt="Screenshot 2024-10-22 at 11 24 06" src="https://github.com/user-attachments/assets/92c9728a-eca9-45a3-9348-36116c10b339">


## Wazuh Deployment with File Integrity Monitoring (FIM) Implementation
In this project I will install wazuh on my Ubuntu desktop, focusing on implementing the File Integrity Monitoring (FIM) module. FIM is crucial in detecting unauthorized modifications to critical files, helping to prevent malicious activities. Everything was done in my virtual lab using Virtual Box.

The steps include:
- Installing Wazuh using the Install guide on the wazuh website.
- Configuring the Wazuh manager
- Installing an agent on a Windows 10 machine
- Implementing and fine-tuning the File Integrity Monitoring module
- Monitoring specific directories and files for changes


## What is wazuh and why is it important
Wazuh is a free, open-source security platform that unifies XDR and SIEM capabilities. It protects workloads across on-premises, virtualized, containerized, and cloud-based environments.
Wazuh helps organizations and individuals to protect their data assets against security threats. It is widely used by thousands of organizations worldwide, from small businesses to large enterprises. In simple terms, wazuh helps an organisation monitor their endpoints and implement security policies, if you’d like to read more on what wazuh is you can check out their web page (Search on Google)

## Steps Taken

### Step 1: Installing Wazuh

First, I downloaded and ran the Wazuh installation assistant using the commands on the wazuh web page

"curl -sO https://packages.wazuh.com/4.9/wazuh-install.sh && sudo bash ./wazuh-install.sh -a"

Once the assistant finishes the installation, it shows the access credentials and a message confirming that the installation was successful.
<img width="934" alt="wazuh installation" src="https://github.com/user-attachments/assets/c1db0daa-7ff4-48c0-a15f-c6a41e76916f">



Then I accessed the Wazuh dashboard using the IP address of the host machine  https://<wazuh-dashboard-ip> and inpp credentials:

Username: admin

Password: <ADMIN_PASSWORD>


I also deployed the wazuh agent on a Windows 10 machine

<img width="1680" alt="agent" src="https://github.com/user-attachments/assets/6e227d4a-1bf4-4b41-8a95-b80ddffea85b">

<img width="1680" alt="wazuh home" src="https://github.com/user-attachments/assets/86295337-bbe7-4b23-b96e-615bf08fda7b">


### Step 2: Editing the Ossec.conf file on the agent

To get the File Integrity Monitoring (FIM) running on Windows 10, I had to modify the ossec.conf file, which is the configuration file for the Wazuh agent. Before editing the ossec.conf file, I created a backup copy of it.
### Reason: This is a best practice when working with configuration files. It allows you to revert to the original configuration if the changes cause issues.

To fine-tune the File Integrity Monitoring (FIM) settings, I updated the scan frequency in the ossec.conf file from 12 hours (default) to 10 seconds. This ensures more frequent checks for file modifications, allowing logs to be generated every 10 seconds for any changes.
<img width="1025" alt="Screenshot 2024-12-07 at 11 58 57" src="https://github.com/user-attachments/assets/12951cb5-b1f9-4f46-9de4-bcea1cb942b6">

I also Included the "C:\Users\Public" directory in the monitored directories of the File Integrity Monitoring (FIM) to ensures that any changes to files in this shared location are logged. 
<img width="1022" alt="Screenshot 2024-12-07 at 12 26 20" src="https://github.com/user-attachments/assets/8447649b-cc8c-4349-b910-feffd41c4d57">


I saved the file and restarted the service.
<img width="1021" alt="Screenshot 2024-12-07 at 12 06 18" src="https://github.com/user-attachments/assets/d4dda85d-2100-46d0-b607-7fef6038340d">


For this experiment, I will create a text file named "Evil malware" in the "C:\Users\Public\Download" Directory and see if wazuh was able to detect it

<img width="1680" alt="Screenshot 2024-12-07 at 12 29 12" src="https://github.com/user-attachments/assets/669967e2-fb15-4d43-9a60-a774fa0f467b">
<br><br>
<img width="1676" alt="Screenshot 2024-12-07 at 12 32 47" src="https://github.com/user-attachments/assets/e2bcd792-b9cd-425d-b05b-3445ee48840f">
<br><br>
<img width="1680" alt="Screenshot 2024-12-07 at 12 36 41" src="https://github.com/user-attachments/assets/490afef2-b636-4ffb-b9ca-d44da1ecbf25">

#### As expected Wazuh was able to detect file creation 
Wazuh can also generate file hashes, which is a powerful feature for file integrity verification. By cross-referencing these hashes on platforms like VirusTotal, we can determine if a file is malicious. This feature enhances incident detection and supports quicker remediation by linking potential threats to known malware signatures.

I also modified the Evil malware file and then deleted it both actions were logged by wazuh 
<img width="1680" alt="Screenshot 2024-12-08 at 07 43 51" src="https://github.com/user-attachments/assets/3fac7c93-fddb-4db9-b90f-02e663ce9523">
<img width="1679" alt="Screenshot 2024-12-08 at 07 47 19" src="https://github.com/user-attachments/assets/515313aa-c31e-43eb-825b-8c4ac6f053eb">


## Conclusion 
File Integrity Monitoring (FIM) is a critical security tool that monitors files and directories for changes, additions, or deletions. Below are the key benefits:

1. Detects Unauthorized Changes
Identifies suspicious file modifications that could indicate a breach or malware activity, such as unauthorized access or tampering with critical system files.
2. Enhances Threat Detection
Detects malicious activities like ransomware encrypting files or unauthorized backdoor installations in real-time, helping to mitigate risks quickly.
3. Supports Compliance
Assists organizations in meeting regulatory requirements like PCI DSS, HIPAA, and GDPR, which mandate monitoring and logging of file changes.
4. Aids Incident Response
Provides detailed logs of file changes, helping security teams analyze and respond to incidents more effectively.
5. Increases Operational Visibility
Monitors critical files and directories, offering insights into system and application behaviours that might otherwise go unnoticed.


