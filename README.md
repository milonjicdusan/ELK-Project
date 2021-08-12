## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  -ELK-Stack-Project/Ansible/
  
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available for customers, in addition to restricting attacks to the network. If a server goes down, or needs to be updated, services will still continue.
-The advantage of using a jump box is that only the jump box can access the Virutal network via ssh. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat monitors the log files or locations specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is an extremely easy-to-use, efficient and reliable metric shipper for monitoring your system and the processes running on it. 
The configuration details of each machine may be found below.

| Name       | Function   | IP Address                                | Operating System |
|------------|------------|-----------------------------------------  |------------------|
| Jump-Box   | Gateway    | Public: 20.106.166.233 Private: 10.2.0.4  | Linux            |
| Web-1      | Server     | Public: N/A          Private: 10.0.0.7    | Linux            |
| Web-2      | Server     | Public: N/A          Private: 10.0.0.6    | Linux            |
| ELK-Server | Monitoring | Public: 104.209.242.228 Private: 10.1.0.4 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 5061 Kibana port

Machines within the network can only be accessed by the Jump-Box-Provisioner.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible  | Allowed IP Address |
|------------|----------------------|--------------------|
| Jump Box   | yes/no               | Personal IP        |
| Web-1      | no                   | 10.0.0.4           |
| Web-2      | no                   | 10.0.0.4           |
| ELK-Server | no                   | 10.0.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it was easy to do and prevented any easily overloook vulnerablities. 

The playbook implements the following tasks:

- Configures the machine with Docker
- Install docker.io and pip3
- Install python3-pip
- Downloads and configures ELK docker container
- Activates ports 5601, 9200, 5044  

### Target Machines & Beats

This ELK server is configured to monitor the following machines:
1.	Web-1 10.0.0.6
2.	Web-2 10.0.0.5

We have installed the following Beats on these machines:

1.	Filebeat
2.	Metricbeat

These Beats allow us to collect the following information from each machine:

1.	Filebeat watches for log files/locations and collects events related to those files and locations.
2.	Metricbeat records metrics and statistical data from the operating system and services that are running on the server.
 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook (.yml) file to Ansible directory.
- Update the host file to include webserver and ELK. 

