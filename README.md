# Project-1-
University of Denver Cyber Security Project 1 ELK Stack Deployment

The files in this respository were used to configure the cloud network.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment in my Network Diagram. Alternatively, select portions of the Filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

- filebeat-playbook.yml,install-elk.yml

This document contains the following details:

- Description of the Topology
- Access Policies
- ELK Configuration
- Beats in Use
- Machines Being Monitored
- How to Use the Ansible Build

- Description of the Topology:

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA (i.e Web-1, Web-2) the Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Load balancing will protect from the denial of service attack as it will help to divert the traffic and to distribute the load.
Moreover, It helps with the intrusion prevention by restricting access to the servers holding the application.
A jump box provides a controlled access to the servers/VMs holding the applications and helps with the management of these hosts.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.

Filebeat watches for the changes in the files in the locations that we specify or the log files and then collects and send the data to logstash/elasticsearch.

The configuration details of each machine are found below.

Jump-Box-Provisioner Ansible
Gateway with ansible container
52.183.75.90
Ubuntu 18.04 Server LTS

ELK
hosts Elk stack container
52.177.126.132(Public) 10.1.0.4(Private)
Ubuntu 18.04 Server LTS

Web-1
Hosts DVWA Container Contains Filebeat
10.0.0.7
Ubuntu 18.04 Server LTS

Web-2
Hosts DVWA Container(backup for DVWA)
10.0.0.8
Ubuntu 18.04 Server LTS

- Access Policies:

The machines on the internal network are not exposed to the public Internet.
Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

10.0.0.0/16

Machines within the network can only be accessed by Jumpbox

Jumpbox with the IP address 52.183.75.90 with the ansible container can access the Elk server

A summary of the access policies in place can be found below.

Jump-Box-Provisioner
Publicly Accessible: Yes
Allowed Ip address 10.0.0.0/16

ELK
Publicly Accessible: No

Web-1
Publicly Accessible: No

Web-2
Publicly Accessible: No

- Elk Configuration:

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because we need to configure more machines, we can just run the ansible playbook instead of going to every machine and configuring individually.

The playbook implements the following tasks:

- Install docker.io
- Install PIP
- Install docker python module
- Download and Install a Docker elk container
- run command to increase the memory

- Target Machines & Beats:

This ELK server is configured to monitor the following machines:

- Web-1 (10.0.0.7)

We have installed the following Beats on these machines:

- Filebeat

These Beats allow us to collect the following information from each machine:

Filebeat watches for the changes in the files in the locations that we specify or the log files and then collects and send the data to logstash/elasticsearch for example the modifications in a file.

- Using the Playbook:

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

- Copy the filebeat-playbook.yml files to /etc/ansible/roles.
- Update the /etc/ansible/hosts file to include the ip address of the machine under webservers
- Run the playbook, and navigate to http://40.74.253.71:5601/ to check that the installation worked as expected.
