## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/will-ahern/wta_azure/blob/main/Diagrams/Boot%20Project%201%20diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/will-ahern/wta_azure/blob/main/Ansible/elk.yml
https://github.com/will-ahern/wta_azure/blob/main/Ansible/filebeat-config.yml
https://github.com/will-ahern/wta_azure/blob/main/Ansible/filebeat-playbook.yml
https://github.com/will-ahern/wta_azure/blob/main/Ansible/metricbeat-config.yml
https://github.com/will-ahern/wta_azure/blob/main/Ansible/metricbeat-playbook.yml
https://github.com/will-ahern/wta_azure/blob/main/Ansible/pentest.yml
			

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

Load balancers protect against DDoS attacks by shifting attack traffic from the corporate server to a public cloud provider. The advantage of a jumpbox is it lets admins quickly access other points of the network with less restrictions. They can also be in a different security zone. It also reduces the attack surface to a single VM.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and other system data.
Filebeat watches for Log Data.
Metricbeat records metric data (system info for indexing).

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| ELK VM   | Server   | 10.2.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.6   | Linux            |
| Web-2    | Server   | 10.0.0.7   | Linux            |
| Web-3    | Server   | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
144.118.76.209

Machines within the network can only be accessed by SSH.
Jumpbox 52.152.160.61

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 13.82.145.33         |
| Web-1    | No                  | 13.82.145.33         |
| Web-2    | No                  | 13.82.145.33         |
| Web-3    | No                  | 13.82.145.33         |
| ELK      | No                  | 13.82.145.33         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
The primary advantage of Ansible is that it allows you to automatically configure a virtual machine or container quickly and easily.

The playbook implements the following tasks:
- Configure ELK with Docker
- Install Docker.io
- Install pip3
- Download and launch Docker in ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/will-ahern/wta_azure/blob/main/docker_ps.JPG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1	10.0.0.6
Web-2	10.0.0.7
Web-3	10.0.0.8


We have installed the following Beats on these machines:
filebeat-playbook
metricbeat-playbook

These Beats allow us to collect the following information from each machine:
Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
Metricbeat takes the system metrics and statistics that it collects and sends them to a specified output, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the yml file to /etc/ansible/ansible.cfg
- Update the /etc/ansible/hosts file to include hosts group, private IP addresses, and ansible_python_interpreter=usr/bin/python3
- Run the playbook, and navigate to http://[your.VM.IP]:5601/app/kibana to check that the installation worked as expected.
