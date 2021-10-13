# ELK_PROJECT

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/Dornsbach/ELK_PROJECT/blob/6feb92fb3fa8df960eb4c4173cf34312e79cf371/Elk_Project%20.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to recreate the entire deployment pictured above. 

[Elk Install Playbook](https://github.com/Dornsbach/ELK_PROJECT/blob/4a799de3c7d8c1866743521b18de87015b9bcc73/Elk-Install)

[Filebeat Playbook](https://github.com/Dornsbach/ELK_PROJECT/blob/487a25e9ad8734d0cc48ce66447e44387b71747e/filebeat-playbook.txt)

[Metricbeat Playbook](https://github.com/Dornsbach/ELK_PROJECT/blob/487a25e9ad8734d0cc48ce66447e44387b71747e/metricbeat-playbook.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting DoS attacks to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system statistics.

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box and load balancer can accept connections from the Internet. Access these machines is only allowed from the following IP addresses:
- Local WorkStation #1 172.217.22.14

Machines within the network can only be accessed by the jump box.

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you are able to deploy many machines at once.

The playbook implements the following tasks:
- Installs Docker onto machines 
- Puts Filebeat and Metricbeat onto Webservers
- Downloads and launches the docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/Dornsbach/ELK_PROJECT/blob/dd15f123a19745be6c56535ad7989661f6754f09/Screen%20Shot%202021-10-13%20at%203.28.58%20PM.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.7

We have installed the following Beats on these machines:
- 10.0.0.5: Filebeat and Metricbeat
- 10.0.0.7: Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat lets us collect log files and events then forwards them to be indexed to be read easliy.
- Metricbeat lets us collect metrics and statistics from our OS and other services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured along with the Filebeat and Metricbeat congfig files updated. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the all the playbook files to your VM.
- Update the files to make sure you have your webservers and user information correct.
- Make sure to have both beat config files in this directory on the jumpbox ansible /etc/ansible/files. 
- Run the playbooks, and navigate to your LB IP to check that the installation worked as expected.


- Which file is the playbook? Any file containing "Playbook" Where do you copy it? These should be in /etc/ansible on the Jumpbox ansible. 
- Which file do you update to make Ansible run the playbook on a specific machine? The hosts file and all the config files need to be configed to your liking. 
How do I specify which machine to install the ELK server on versus which to install Filebeat on? The Elk server just needs to be on one machine all the rest hooked up to the network can have the beats installed.
- Which URL do you navigate to in order to check that the ELK server is running? Navigate to the IP of your loadbalancer. 
