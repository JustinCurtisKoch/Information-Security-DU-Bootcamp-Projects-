# Information-Security-DU-Bootcamp-Projects-
A collection of hands on learning milestones completed throughout the cohort. 
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

 https://github.com/JustinCurtisKoch/Information-Security-DU-Bootcamp-Projects-/blob/main/ANSIBLE/ansible_dockersetup.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
The load balancer quietly distributes traffic between the two servers, optimizing performance and adding additional security_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.
FILEBEAT: Log file shipper, transfering data to the ELK stack for further analysis.
METRICBEAT: Collects metrics from the OS and services, again transfering data to the ELK stack for further analysys.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| NAME     | FUNCTION   | IP       | OS    | DOCKER |
|----------|------------|----------|-------|--------|
| Jump Box | gateway    | 10.0.0.5 | LINUX | no     |
| Server 1 | web server | 10.0.0.6 | LINUX | yes    |
| Server 2 | web server | 10.0.0.7 | LINUX | yes    |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept ssh connections from the personal workstation. Access to this machine is only allowed from the IP addresses of that personal workstation.
This was accomplished by using the 'red team NSG' as a firewall to direct traffic. 


Machines within the network can only be accessed by ssh connection passed through the jump box.
The Elk stack (at 10.0.0.8) can be reached throught the jump box (10.0.0.5)


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Once the intial script was built and tested for correct configuration it was saved, allowing for a streamlined approach to building another stack with the same specs.


The playbook implements the following tasks:
-calls and installs docker.io
-calls and installs python3
-calls and launches a docker image
-enables the docker service


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.6 and 10.0.0.7

We have installed the following Beats on these machines:
Filebeat, Metricbeat, Packetbeat

These Beats allow us to collect the following information from each machine:
Filebeat: files logs
Metricbeat: system/service metrics
Packetbeat: packet flow

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible_dockersetup.txt (yaml file) file to the ansible container (directory /etc/ansible).
- Update the ansibel_dockersetup.txt file to include any changes to configuration, speifically the docker image.
- Run the playbook, and navigate to the new VM to check that the installation worked as expected.

*The ansible playbook is yaml file. It should be stored in the ansible container that will connect to the new machine.
*The yaml.config file should be updated with the ip address of the new machine.
*To check the ELK server is running by navigating to its ip. 
