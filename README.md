#  Wazuh Deployment with File Integrity Monitoring (FIM) Implementation

<img width="1499" alt="Screenshot 2024-10-22 at 11 25 09" src="https://github.com/user-attachments/assets/531df2c3-8d41-4e94-bb9c-86abc502ae16">
<img width="1260" alt="Screenshot 2024-10-22 at 11 24 06" src="https://github.com/user-attachments/assets/92c9728a-eca9-45a3-9348-36116c10b339">


## Wazuh Deployment with File Integrity Monitoring (FIM) Implementation
In this project I will install wazuh on my Ubuntu desktop, focusing on implementing the File Integrity Monitoring (FIM) module. FIM is crucial in detecting unauthorized modifications to critical files, helping to prevent malicious activities. Everything was done in my virtual lab using VMware.

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
Once the assistant finishes the installation, it  shows the access credentials and a message confirming that the installation was successful.




Then I used the Wazuh dashboard using the IP address of the host machine  https://<wazuh-dashboard-ip> and inpp credentials:

Username: admin

Password: <ADMIN_PASSWORD>






### Step 2: Setting up Cloud Infrastructure
- Deployed the infrastructure on **Vultr**, with all virtual machines (VMs) connected within a **Virtual Private Cloud (VPC)**.
  - Used a **private IP range** of `172.31.x.x/24` for secure server connections.
  - Added an **internet gateway** to facilitate traffic routing between the internet and the VPC.

### Step 3: Connecting Components
- Configured connections between servers to define data flow:
  - Logs from the Windows and Ubuntu servers are forwarded to the ELK stack through the **Fleet Server**.
  - Security alerts from the ELK stack are sent to the **OS Ticket Server**.
  - Simulated attack scenarios with roles for **SOC Analyst Laptop** and **Attacker Machine**.

### Key Technologies:
- **Cloud Provider**: Vultr (for VM deployment).
- **Elastic & Kibana**: For log aggregation and visualization.
- **Fleet Server**: Manages Elastic agents.
- **Sysmon**: Installed on the Windows server for detailed log generation.
- **Command & Control Server**: Using Mythic for attack simulations.

## Diagram
Here’s the network architecture diagram illustrating the  setup and their connections:

![network-architecture](https://github.com/user-attachments/assets/1ba85fda-137a-43e2-94ee-059245a4751d)


![network-architecture2](https://github.com/user-attachments/assets/c70fee67-0536-4acd-b7cf-93fe1f45826e)








## Outcome
- Successfully designed and documented the network architecture, laying the groundwork for the ELK Stack setup and subsequent security monitoring.

## Next Steps
- Implement the ELK Stack and begin the process of log ingestion from the Ubuntu and Windows servers on Day 2.

## Challenges Faced
- Determined the optimal network architecture layout and ensured seamless integration of all components within the VPC.

