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

Load balancing ensures that the application will be highly _accessible, in addition to restricting _____traffic to the network.
- _TODO: What aspect of security do load balancers protect? Acessibility. What is the advantage of a jump box?_It gives the ability to access and manage devices in a security zone.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _ applications____ and system _logs____.
- _TODO: What does Filebeat watch for?_It monitors logs and locations specified.
- _TODO: What does Metricbeat record?_Metrics and stats to help you monitor servers.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web 1    | VM      | 10.1.05     | Linux            |
| Web 2    |    VM    | 10.1.0.6   | Linux            |
| Elk Server|   VM    | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _Jump Box____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_68.52.247.107

Machines within the network can only be accessed by ___Jump Box__SSH.
- _TODO: Which machine did you allow to access your ELK VM? Jump Box What was its IP address?_40.91.97.97

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 40.91.97.97          |
| Web 1    | No                  | 10.1.0.5             |
| Web 2    | No                  | 10.1.0.6             |
| Web 3    | No                  | 10.1.0.7             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_You only have to change to change one change and it will feed to all machines. 

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- (1) Create a new vNet in Azure, preferably in a different region because of resource allocation, but within the same resource group; create a peer-to-peer network connection between their vNets; create a new VM in the new vNet with 2vCPUs and a minimum of 4DiB of memory; add new VM to Ansible's hosts file in the provisioner VM.
  (3) Create a Anisble playbook that installs Docker and configures an ELK container.
  (4) Run the playbook to launch the container.
  (5) Restrict access to the ELK VM.
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_10.1.0.5; 10.1.0.6; 10.1.0.7

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_filebeats and metric beats

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._Collects metrics and statistics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _ansible host file__ file to /etc/ansible_____.
- Update the __host__ file to include internal IP addressess of your web servers and ELK server.
- Run the playbook, and navigate to Kibana____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Roles. Where do you copy it?_To your Web VMs
- _Which file do you update to make Ansible run the playbook on a specific machine? Config file. How do I specify which machine to install the ELK server on versus which to install Filebeat on?_This is specified in the config file.
- _Which URL do you navigate to in order to check that the ELK server is running? Navigate to the Filebeat installation page on the ELK server GUI.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._ $ ansible-playbook filebeat-playbook.yml