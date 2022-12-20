## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Topology](https://github.com/Lzythinker/Project-Elk/blob/main/IMG/Elk%20stack.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/ELK-install.yml
  - /etc/ansible/roles/filebeat-playbook.yml
  - /etc/ansible/roles/metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancers protect from DDOS attacks by distributing the traffic on a network to two different servers. The advantage of a Jumpbox is user access from a single node, and it will be secured.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Logs and system traffic.
- _TODO: What does Filebeat watch for?_
Filebeat watch for any information in the file system which has been changed and when.
Filebeat watch for log files/locations and collects logs data
- _TODO: What does Metricbeat record?_
metricbeat record metric and statistical data from the operating system

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name          | Function        | IP Address      | Operating System |
|---------------|-----------------|-----------------|------------------|
| Jump Box      |Gateway          | 10.0.0.8        |ubtntu 20.04      |
| Web-1         |Server           | 10.0.0.5        |ubtntu 20.04      |
| Web-2         |Server           | 10.0.0.10       |ubtntu 20.04      |
| Elk           |ELk-server       | 10.2.0.4        |ubtntu 20.04      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
Public IP of the JumpBOx:20.183.85.55

Machines within the network can only be accessed by SSH.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
We use the JumpBox to access the ELK VM, the Private IP is 10.0.0.8


A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible  | Allowed IP Addresses |
|----------  |----------------------|----------------------|
| Jump Box   | Yes                  | 20.183.85.55         |
| Web-1      | No                   |                      |
| Web-2      | No                   |                      |
| Elk        | Yes                  | 23.99.205.244        |

### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
The main advantage would be that it allows you to deploy to multiple servers using one playbook

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

Install docker.io
Install Python-pip
Install docker container
Launch docker container: elk
Command: sysctl -w vm.max_map_count=262144

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![Docker ps](https://github.com/Lzythinker/Project-Elk/blob/main/IMG/docker%20ps.PNG)


_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
The .yml file and you copy it to /etc/ansible directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
That would be the Hosts. (you need to add your VMS to your webserver and elk
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.ELK.VM.Private.IP]:5601/app/kibana


