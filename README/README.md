## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

~/Red_Cloud_Infrustructure/Diagram/Git_Dia.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - Elk.playbook:

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundent, in addition to restricting direct traffic to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to configurations  and monitor the system.
The beat suite integration allows us to log and focus on the data we really looking to monitor for suspicious changes, While
metricbeat collect the measuremnts of our machins uptime and CPU usage for example.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | VM DVWA  | 10.0.0.6   | Linux            |
| Web-2    | VM DVWA  | 10.0.0.7   | Linux            |
| Web-3    | VM DVWA  | 10.0.0.9   | Linux            |
| Elk      | Elk VM   | 10.1.0.4   | Linux
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:5.28.159.30


Machines within the network can only be accessed by the Jump-box internal IP.
The Elk server can be login via the Jump- Box 10.0.0.1_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes via specific I  | 5.28.159.30          |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4
| Web-3    | No                  | 10.0.0.4
| Elk      | No                  | 10.1.0.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the automated configuration can be deployed easily at any given time if neccesery, without the need to back step the operation manualy and trace back the configuration that was in use.

The playbook implements the following tasks:
- Install Docker
- Install Python-pip3
- Install Docker moudle
- Command to increase Virtual memory
- Download and launch Elk docker container image- sebp/elk:761
- List publishe ports
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.6
- 10.0.0.7
- 10.0.0.9

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat: collects data from our VM logs to monitor suspicious activity
- Metricbeat: collects data of our machine preformence such as Uptime and CPU usage to help us detect outstanding activity of the machine.
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Elk-playbook.yml file to /etc/ansible/roles.
- Update the host file to include elk server
- Run the playbook, and navigate to your elk VM via ssh to check that the installation worked as expected.


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
