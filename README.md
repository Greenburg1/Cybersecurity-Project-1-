University of Utah Project 1 
Elk Stack Server 

Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 ![image](https://user-images.githubusercontent.com/70069874/109773620-a8250a80-7bbc-11eb-8363-006aebca1e8b.png)

 

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Azure Cloud Environment file may be used to install only certain pieces of it, such as Filebeat.

Filebeat Playbook
https://docs.google.com/document/d/1Nx32AKse0tlqdsjvI4tyrX8BpicQ_1qLAlAAXiAf258/edit?usp=sharing

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be exceptionally reliable, in addition to restricting access to the network.

Load Balancers help protect against DOS attacks that takes advantage of the jump box as it restricts access to the administrators. When you integrate an ELK server it allows the user to easily monitor vulnerable VM’s, that way they can make changes easily.  

Filebeat helps generate and organize log files then sends them to Logstash and Elasticsearch. More importantly it logs the information about the file system, which includes the files that have been changed. 
Metricbeat is a lightweight shipper that is installed on servers to collect information from the operating system and other services running on your server. Metricbeat takes the information that is collects and out puts the information where you specify. 



The configuration details of each machine may be found below.
 

 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

76.171.145.84 - my personal machine

Machines within the network can only be accessed by accessing the DVWA container in the jump box VM.

The only machine that can access the Elk server is 76.171.145.84 (Personal Computer) and the Jump Box VM (10.0.0.7).

A summary of the access policies in place can be found in the table below.

 


Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

There’s no need to install other software or firewall ports on the client systems if you want them automated or if you want to change the management structure. 


The playbook implements the following tasks:

Install Docker 

Download Image 

Configure container 

Create playbook and install the container with the docker, Filebeat, and Metricbeat

Run the playbook that launches the container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 


Target Machines & Beats

This ELK server is configured to monitor the following machines:

10.0.0.12 - Web-1
10.0.0.13 - Web-2
10.0.0.14 - Web-3




We have installed the following Beats on these machines:

Filebeat 

Metricbeat 


These Beats allow us to collect the following information from each machine:

Filebeat monitors logfiles or locations that specify, collects logs, and moves them to either Elasticsearch or Logstash for indexing. When Filebeat starts logging, it presents the data in a nice and easy dashboard making it easier to read. 

 



Metricbeat automatically collects data from the operating systems as well as other services running on the server. Metricbeat takes the metric and statics it collects and sends them to the output that you want. 

 



Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-playbook file to /etc/ansible/roles.
- Update the filebeat-config.ymlfile to include...
- Run the playbook and navigate tokibana page at [ELK public IP]/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook?

elk-playbook.yml - used to install ELK Server
https://docs.google.com/document/d/1sYFqKxUfNxH9-6lrh_X8_tncvFYUEVesUS5IaKhOAS8/edit?usp=sharing
filebeat-playbook.yml - Used to install and configure Filebeat on Elk Server and DVWA servers
https://docs.google.com/document/d/1Nx32AKse0tlqdsjvI4tyrX8BpicQ_1qLAlAAXiAf258/edit?usp=sharing
metricbeat-playbook.yml - Used to install and configure Metricbeat on Elk Server and DVWA servers

 Where do you copy it?

/etc/ansible/ 

Which file do you update to make Ansible run the playbook on a specific machine? 

/etc/ansible/hosts.cfg

How do I specify which machine to install the ELK server on versus which to install Filebeat on?

In /etc/ansible/hosts you can tell it where you want it to be installed. 


Which URL do you navigate to in order to check that the ELK server is running?

http://publicip(elkserver):5601

