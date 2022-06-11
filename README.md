# ELK-Stack-Project
Elk Stack Deployment
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below:

![image](https://user-images.githubusercontent.com/106046849/173168268-c9c7c377-2c54-4fdd-81d0-256c76049804.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook-file may be used to install only certain pieces of it, such as Filebeat.

[Ansible/ansible_config.yml](https://github.com/ShamanOxy/ELK-Stack-Project/blob/main/Ansible/ansible_config.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting demand to the network.
Load balancers prevent server overload and improve application availability and responsiveness.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance. Metricbeat takes the statistics and it ships them to either Elasticsearch or Logstash. Filebeat is a shipper for forwarding and centralizing log data.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 23.100.111.137  | Linux            |
| Web-1    | WebApp   | 10.0.0.5   | Linux            |
| Web-2    | WebApp   | 10.0.0.6   | Linux            |
| ELK-VM   | Elk-Stak | 20.213.243.25   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Personal Computer IP

Machines within the network can only be accessed by the Jump Box Machine.
-Public IP: 23.100.111.137
 Private IP : 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No              | Public PC IP   |
| Web-1         |            No         |      23.100.111.137                |
| Web-2         |            No         |      23.100.111.137                |
| ElkVM    |   No            | 10.0.0.5       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible can be run from the command line and will make sure everything runs identically anywhere.

The playbook implements the following tasks:
- Increase the memory of the machine
- Install python-pip
- Install Docker.io
- Install the docker python module
- Install and start a docker elk stack

Run (docker ps) to make sure he installation was succesful and that the status is Up.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6 

We have installed the following Beats on these machines:
- filebeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
- Filebeat collects and transfers file system log data from a machine to the ELK stack for further processing. This can be viewed through Kibana.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeatconfyg.yml file to /etc/ansible/files.
- Update the /etc/ansible/hosts file to include private IP's of the DVWA Machines.
- Run the playbook, and navigate to Kibana (http://"IPofELK":5601) to check that the installation worked as expected.


### Citations and References:

https://elk-docker.readthedocs.io/
https://www.elastic.co/guide/en/kibana/current/index.html
