# Project-1
Creating a new GitHub repository. Syncing a local repository. Creating a README file. Markdown The following commands:  git pull git add git commit -m git push origin --set-upstream &lt;-branch->
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

13-Elk-Stack-Project/Images/NetworkDiagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

  - _filebeat-playbook.yml_
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure by adding layers of security, in addition to restricting unauthorized access to the network.
- Load Balancers protect the public IP of the network by masking it with the load balancer address before allowing access. Having a jumpbox allows the system admin easier access to update multiple servers all at once with containers and playbooks attached. It saves a lot of time and money not having to manually update each individual server. Having redundancy allows for higher availability. 

Integrating an ELK server allows users to easily monitor the potentially vulnerable VMs for changes to the files and system configurations.
- _Filebeat monitors the status of each file_
- _Metricbeat monitors various metrics such as running services on the server._

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK-VM     | Virtual Machine         |    10.2.0.5        | Linux                 |
| Web-1    | Redundancy         | 10.1.0.6   |        Linux          |
| Web-2     | Redundancy         |        10.1.0.8    |             Linux    |
| Web-3     | Redundancy         |        10.1.0.9    |             Linux    | 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpboxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _40.78.69.122_

Machines within the network can only be accessed by ssh publickey.
- _Jumpbox IP 40.78.69.122 using the Jumpbox publicKey from id_rsa.pub_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 45.17.155.48    |
| ELK         | No                    | 40.78.69.122                     |
|     Web-1     | No                    | 45.17.155.48                     |
| Web-2 | No | 45.17.155.48 |
| Web-3 | No | 45.17.155.48 |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _Having the configuration automated speeds up the process when having multiple servers._

The playbook implements the following tasks:
- Download docker.io
- Download pip3
- download filebeat & metricbeat
- setup and enable filebeat & metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

~/Project-1/Images/docker_ps-a.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _10.1.0.6, 10.1.0.8, and 10.1.0.9 (Web-1, Web-2, and Web-3)_

We have installed the following Beats on these machines:
- _metricbeat & filebeat_

These Beats allow us to collect the following information from each machine:
- _Metricbeat monitors current metrics of server performance such as CPU, memory, and load. Filebeat monitors current file status to ensure availability. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook.yml file to your ansible container. 
- Update the playbook config and hosts file to include your hosts. 
- Run the playbook, and navigate to Ansible to check that the installation worked as expected. 

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? playbook.yml copy to Ansible directory. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? hosts and ansible.config need to be updated to specify which machine to install. 
- _Which URL do you navigate to in order to check that the ELK server is running? 168.62.217.95 (current ELK public IP)


