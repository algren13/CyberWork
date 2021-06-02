## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
 

[Network Diagram](Images/CloudNetwork.io.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  install-elk.yml
  installer-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers protect availability by always making sure there will be a web server available to process requests.  Load balancers also shield servers from requests on other ports.
 The jump box is small server configured only for SSH connections and is used to configure the network while shielding those servers from public con nections

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system files.


The configuration details of each machine may be found below.


Name	    Function	     IP Address	Operating System
-----	    -----	         -----	    -----
Jump Box	Administrative   10.0.0.7   Ubuntu Linux
Web-1		WebServer        10.0.0.11	Ubuntu Linux
Web-2		WebServer        10.0.0.9	Ubuntu Linux
Web-3		WebServer        10.0.0.12	Ubuntu Linux
ElkStack	Elk Server       10.2.0.4	Ubuntu Linux

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Machine machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresse:
- 74.110.144.160

Machines within the network can only be accessed by the jump box internal address of 10.0.0.7.


A summary of the access policies in place can be found in the table below.

Name	    Publicly Accessible	        Allowed IP Addresses
-----	            -----	                -----
Jump Box	        Yes	                    20.42.98.33
Load Balancer	    Yes	                    104.51.129.248
Web-1	            No	                    10.0.0.11
Web-2	            No	                    10.0.0.9
Web-3	            No	                    10.0.0.12
ElkStack	        No	                    10.2.0.4
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for uniform installations and 
reduces the possibility of human error through manual installations, making servers easier to deploy and troubleshoot.


The playbook implements the following tasks:
- Installs Docker with Apt
-Installs Python3 & Docker Python 3 module
-Adjusts Virtual Memory
-Downloads and installers Docker Elk Container and configures the ports
-Enables Docker Service upon system startup


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
(Images/DockerPS.jpg)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.11
- Web-2 10.0.0.9
- Web-3 10.0.0.12

We have installed the following Beats on these machines:
- FileBeat
- MetricBeat

These Beats allow us to collect the following information from each machine:
- Filebeat is a lightweight shipper for system logs
- Metricbeat is a lightweight shipper for metric data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the home directory.
- Update the host file to include the IP address under Web Servers
- Run the playbook, and ssh to the new server to check that the installation worked as expected.


