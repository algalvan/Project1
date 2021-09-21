## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Copy of Untitled Diagram drawio (1)](https://user-images.githubusercontent.com/80696161/134147758-1c1bea48-d343-450d-a7d1-177c044807bd.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook  file may be used to install only certain pieces of it, such as Filebeat.

  -[install_elk.yml](https://github.com/the-Coding-Boot-Camp-at-UT/UTA-VIRT-CYBER-PT-06-2021-U-LOL/blob/c72e1e84e94cd95c9b943d21debfdd53de518678/Week-13/Activities/Stu_Day_1/Solved/Resources/install-elk.yml)


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
-  What aspect of security do load balancers protect?  Load balancers defend against denial of service attacks. What is the advantage of a jump box? The advantage of a jump box is to provide restricted access to your network environment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- Filebeat monitors file logs, collects log events and forwards them for indexing.
- Metricbeat records metrics and statistics from an operating system and services running on a server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Server        | 10.0.0.5       |Linux               |
| Web-2    | Server       | 10.0.0.6           |  Linux                |
| ElkVM    |   Server      | 10.1.0.4           |   Linux          |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 69.221.217.250


Machines within the network can only be accessed by SSH
- The Jump Box was allowed access to the ELK VM. It's IP Address was 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 69.221.217.250   |
|     Web-1     | No                    | 10.0.0.4                     |
|     Web-2     | No                    |  10.0.0.4                    |
|     ElkVM     | No                    |  10.0.0.4, 69.221.217.250                    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automation simplifies complex tasks, not just making developers’ jobs easier but allowing them to focus attention on tasks that add value to an organization.

The playbook implements the following tasks:
- Install docker.io
- Install Python-pip
- Install docker container
- Launch docker container: elk


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img width="949" alt="docker ps" src="https://user-images.githubusercontent.com/80696161/134142467-d69d8b57-b457-4489-be0a-f0c9d9f6ccc6.PNG">

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5) and Web-2 (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect changes made it also allows us to determine when the changes were made.
- Metricbeat records metrics and statistics from an operating system and services running on a server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the host file to include the webservers and elk vm
- Run the playbook, and SSH into the elk vm, then run docker ps to check that the installation worked as expected.


- Playbook: elk_playbook2.yml Location:  /etc/ansible/roles/install_elk.yml/tasks
- You must update the etc/ansible/host file. I specify which machine to install the ELK server on versus which to install Filebeat on by using the playbook to specify which host group that the various systems belong to.
- Navigate to  http://[your.ELK-VM.External.IP]:5601/app/kibana to confirm ELK and kibana are running.

