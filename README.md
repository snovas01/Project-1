# Project-1
Elk-Stack-Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Elk-Stack-Project.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

-What aspect of security do load balancers protect?
Load balancers protect the availability of server resources at Layers 4 and/or 7 of the OSI model.


-What is the advantage of a jump box?
Acting as a stepping stone for administrators to access devices in a separate security zone, it allows for separation of the workstations with no physical access so security controls can't be circumvented.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-What does Filebeat watch for?
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch/Logstash for indexing. The Filebeat Elasticsearch module can handle audit logs, deprecation logs, gc logs, server logs, and slow logs.

-What does Metricbeat record?
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch/Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as Apache.

The configuration details of each machine may be found below.

| Name     | Function         | IP Address   | Operating System |
|----------|------------------|--------------|------------------|
| Jump Box | Gateway          | 10.0.0.4     | Linux            |
| Web-1    | Docker Server    | 10.0.0.5     | Linux            |
| Web-2    | Docker Server    | 10.0.0.7     | Linux            |
| 814VM    | ELK Server       | 10.2.0.4     | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the administrator's private IPv4 address.
- 10.0.0.4

Machines within the network can only be accessed by Jump Box via SSH.
- 814VM 10.2.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Personal IP          |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| 814VM    | No                  | 10.0.0.4 Personal IP |        

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because because it saves time, provides an easy to execute automation, and it is easily repeatable across multiple machines.

The playbook implements the following tasks:
- Installs Docker Application
- Installs Python3 translator
- Installs Elk Docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/sudo docker ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
  Web-2 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
Filebeat monitors the log files or locations that you specify for the machine. It then collects log events, and sends them over to Elasticsearch or Logstash for representation.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/files directory.
- Update the /etc/ansible/hosts file to include ELK category that contains the IP of the ELK machine.
- Run the playbook, and navigate to http://elk_IP:5601/app/kibana to check that the installation worked as expected.


