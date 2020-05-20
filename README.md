# Azure-Project-1: ELK Stack

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/open?id=1hbgz8O3T6lNzfooXRStp7nXOaPHBQc_J

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK Stack Project files may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook-yml.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
The load balancer prevents a direct access to individual machines within the network from the outside/internet, thus reducing the attack surface. Similarly, the jumpbox prevents the network machines from being exposed to the public/internet. It serves as the gateway router to the network, protecting the other network machines from exposure to the public internet, and controls access to the other machines by allowing certain connections, based on IP addresses, destination ports, protocols, etc.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system logs.
- Filebeat collects data about the file system.
- Metric beat records machine metrics, such as the uptime.

The configuration details of each machine may be found below.

| Name       | Function         | IP Address    | Operating System |
|------------|------------------|---------------|------------------|
| Jump Box   | Gateway          | 10.0.0.4      | Linux            |
| VM1        | Emulates PC      | 10.0.0.15     | Docker           |
| VM2        | Emulates PC      | [not created] | Docker           |
| ELK Server | VM data analysis | 10.0.0.20     | Docker           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 76.116.62.133 [local workstation]

Machines within the network can only be accessed by SSH.
- Only the Jump Box [10.0.0.4] was allowed access to the ELK VM. 

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | Yes                 | 76.116.62.133        |
| VMs        | No                  | 10.0.0.4             |
| ELK-Server | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage of automating configuration with Ansible is the speed by which you can deploy the ELK Server.

The playbook implements the following tasks:
- Install Docker
- Install Python-PIP
- Install Docker Python Module
- Increase Virtual Memory
- Download and Launch A Docker Elk Container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://drive.google.com/open?id=1IKGsbAQ9nQIvvv55wgA4katQnXzF9CMn

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- VM1 [10.0.0.15]
- VM2 [not created]

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that we specify, collects log events, and then forwards them to Elasticsearch of Logstash for indexing. Examples would be syslog events events by hostnames and processes.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the /etc/ansible/files/filebeat-configuration.yml file to /etc/filebeat/filebeat.yml
- Update the /etc/ansible/hosts file to include [elkservers] and its ip address (private)
- Run the playbook, and navigate to /etc/ansible/roles/ to check that the installation worked as expected.

https://drive.google.com/open?id=1Qouc0onlpBk30-FQ7PFE_GnNPHdFJiNM
