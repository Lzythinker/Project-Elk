## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/ELK-install.yml

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


![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/Lzythinker/Project-Elk/blob/main/IMG/docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web-1(10.0.0.5), Web-2(10.0.0.10)
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines: Filebeat, Metricbeat
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat monitors log files or locations you specify and collects log events.
Metricbeat collects metrics from the operating system and from services running on the server.



### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update both config files to include the ELK VM Private IP address(10.2.0.4) 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
The .yml file and you copy it to /etc/ansible directory
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
That would be the Hosts. (you need to add your VMS to your webserver and elk
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[your.ELK.VM.Private.IP]:5601/app/kibana


