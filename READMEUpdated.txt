## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly Available, in addition to restricting Inbound access to the network.
- _TODO: What aspect of security do load balancers protect? The load balancer ensures that work to process incoming traffic will be shared by both vulnerable web servers
 What is the advantage of a jump box? Access controls will ensure that only authorized users will be able to connect in the first place.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the File System and system Metrics.
- _TODO: What does Filebeat watch for? 
- _TODO: What does Metricbeat record? CPU Usage/ Attempted SSH Logins etc.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| Web 1    | Webserver | 10.0.0.2   | Linux            |
| Web 2    | Webserver | 10.0.0.3   | Linux            |
| ELK      | Monitoring| 10.0.0.4   | Linux            |

### Access Policies
The machines on the internal network are NOT exposed to the public Internet. 

Only the **jump box** machine can accept connections from the Internet. Access to this machine is only allowed from the IP address `64.72.118.76`
Only the **jump box** machine can accept connections from the Internet. Access to this machine is only allowed from the IP address `104.40.2.245`
The machines on the internal network are not exposed to the public Internet. 

Only the JUMPBOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.
| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 64.72.118.76         |
| Web 1    | No                  | 10.0.0.1-254         |
| Web 2    | No                  | 10.0.0.1-254         |
| ELK      | No                  | 10.0.0.1-254         |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? A quick and robust way to set up an standardized configuration on, potentially, multiple machines.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Docker and Ansible on Jumpbox
- Elk ELK VM to host 
- Run Playbook

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
ELKserver
---------
![DockerPS](/Diagrams/Images/Docker_PS_Output/docker_ps_output_ELKserver.PNG "ELKserver")
Jump-Box-Provisioner
--------------------
![DockerPS](/Diagrams/Images/Docker_PS_Output/docker_ps_output_Jump-Box-Provisioner.PNG "Jump-Box-Provisioner")
Web-1
-----
![DockerPS](/Diagrams/Images/Docker_PS_Output/docker_ps_output_Web-1.PNG "Web-1")
Web-2
-----
![DockerPS](/Diagrams/Images/Docker_PS_Output/docker_ps_output_Web-2.PNG "Web-2")
DVWA-VM3
--------
![DockerPS](/Diagrams/Images/Docker_PS_Output/docker_ps_output_DVWA-VM3.PNG "DVWA-VM3")
![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
  - Web-1: 10.1.0.5
  - Web-2: 10.1.0.6
  - DVWA-VM3: 10.1.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat will be used to collect log files from very specific files such as Apache, Microsft Azure tools and web servers, MySQL databases.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?__/etc/ansible/_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
I have specified two separate groups in the etc/ansible/hosts file. One of the group will be webservers which has the IPs of the 3 VMs that I will install Filebeat to. The other group is named ELKserver which will have the IP of the VM I will install ELK to.
- _Which URL do you navigate to in order to check that the ELK server is running?
_http://20.84.136.248:5601//app/kibana_

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._