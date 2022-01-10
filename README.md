# ELK-Stack## 
Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


![My diagram](https://user-images.githubusercontent.com/85968507/148706634-14467004-b89f-435c-94e8-e6a23e7eaa0a.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbook file may be used to install only certain pieces of it, such as Filebeat.
- Elk Playbook.yml
-  Metricbeat.yml
- Filebeatplaybook.yml
- Myplaybook.ym

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

### What aspect of security do load balancers protect? What is the advantage of a jump box?_

- Load balancing plays an important security role as IT increasingly moves  to the cloud. Load balancer offloading protects organizations against Distributed Denial of Service (DDoS) attacks. It does this by forwarding attack traffic from the company's servers to a public cloud provider. Thereby providing availability of the organization to its customer and user

- A jump box is a secure computer that all administrators log on first before starting administrative tasks, or use as a starting point for logging into servers or other untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffics.

### What does Filebeat watch for?
- Filebeat monitors changes in the system's structure. It acts as a logging agent that generates  log files, monitors it, transmits data for indexing

### What does Metricbeat record?
- Metricbeats collects  metrics and statistics for the operating system and  services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
|Web-1     |DWVA Host          |    10.0.0.7        |   Linux               |
Web-2      |DWVA Host          |     10.0.0.8       |   Linux               |
| ELK     | DWVA Host         |    10.0.0.4         |  Linux                |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box-provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses 104.45.195.180 which is the public IP address

Note: Machines within the network can only be accessed by Jump-box-provisioner virtual machine.

### Which machine did you allow to access your ELK VM?
 Jump-Box-Provisioner
### What was its IP address?
104.45.195.180

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| Web-1	         |     No                |          Local Vnet            |
|  Web-2        |      No               |  Local Vnet                    |
| Elk         | No                  | 104.45.195.180 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows multiple machines to configure repeatable changes at the same time which can speeds up the deployment process. Besides that, the codes is always updating when the enviorment needs to create new or update it.

### What is the main advantage of automating configuration with Ansible?
- Ansible automation helps considerably with the representation of Infrastructure as Code (IAC). IAC involves provisioning and management of computing infrastructure and related configuration through machine-processable definition files.
### The playbook implements the following tasks:
Download/Install Docker on the ELK server
Download/Install/Start ELK on a docker container on hosted on the ELK server
Download/Install/Start filebeat on the docker container running on each web server, forwarding logs to the ELK server
Download/Install/Start metricbeat on the docker container running on each web server, forwarding metrics to the ELK server

![image](https://user-images.githubusercontent.com/85968507/148709139-8d7b6d93-81f3-4611-a161-444c4557fe1c.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
|  Name     |    Function   |    IP Address   |    Operating System   |
|-------|-------|-------|-------|
|   Web-1    |   DVWA    |   10.0.0.5    |    Local Vnet   |
|Web-2  | DVWA  |10.0.0.6|   Local Vnet |


We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat : Monitor file changes on the system
-Metricbeat : Monitor system metriv like CPU usage, Ram etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
* Copy the Ansible/Elk playbook.yml to /etc/files.
* Update the /etc/ansible/hosts file to include group of machines you're trying to run the playbook.
* Run the playbook, and navigate <public_ip_of_elk_machine> :5601/app/kibana to check that the install worked as expected
