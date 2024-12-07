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


### Step 2: Setting up Cloud Infrastructure








## Outcome
- Successfully designed and documented the network architecture, laying the groundwork for the ELK Stack setup and subsequent security monitoring.

## Next Steps
- Implement the ELK Stack and begin the process of log ingestion from the Ubuntu and Windows servers on Day 2.

## Challenges Faced
- Determined the optimal network architecture layout and ensured seamless integration of all components within the VPC.

