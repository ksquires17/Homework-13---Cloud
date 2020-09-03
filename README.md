## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ANSIBLE file may be used to install only certain pieces of it, such as Filebeat.

![install_ELK](install_ELK.txt)

![filebeat-playbook](filebeat-playbook.txt)
   

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly RESPONSIVE, in addition to restricting TRAFFIC to the network.
What aspect of security do load balancers protect? LOAD BALANCERS PROTECT APPLICATIONS FROM EMERGING THREATS, AUTHENTICATE USER ACCESS AND PROTECT FROM DDoS ATTACKS
What is the advantage of a jump box? A JUMP BOX PROTECTS VM'S FROM THE PUBLIC INTERNET

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the FILE SYSTEM and system METRICS.
What does Filebeat watch for? MONITORS THE LOG FILES/LOCATIONS SPECIFIED AND FORWARDS THEM TO ELASTICSEARCH FOR INDEXING
What does Metricbeat record? METRICS FROM THE SYSTEM AND SERVICES RUNNING ON THE SERVER

The configuration details of each machine may be found below.

| Name      | Function          | IP Address | Operating System |
|-----------|-------------------|------------|------------------|
| Jump Box  | Gateway           | 10.0.0.6   | Linux            |
| Web-1     | Network Interface | 10.0.0.4   | Linux            |
| Web-2     | Network Interface | 10.0.0.5   | Linux            |
| DVWA-VM2  | Network Interface | 10.0.0.7   | Linux            |
| ELKServer | Network Interface | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JUMP BOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
| Name          | IP Address     |
|---------------|----------------|
| Web-1         | 10.0.0.4       |
| Web-2         | 10.0.0.5       |
| DVWA-VM2      | 10.0.0.7       |
| ELKServer     | 10.2.0.4       |
| Local Machine | 69.169.155.235 |

Machines within the network can only be accessed by JUMP BOX.
Which machine did you allow to access your ELK VM? JUMP BOX 
What was its IP address? 10.0.0.6

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses                               |
|-----------|---------------------|----------------------------------------------------|
| Jump Box  | Yes                 | 69.169.155.235/10.0.0.4/10.0.0.5/10.0.0.7/10.2.0.4 |
| Web-1     | No                  | 10.0.0.6/10.0.0.5/10.0.0.7/10.2.0.4                |
| Web-2     | No                  | 10.0.0.6/10.0.0.4/10.0.0.7/10.2.0.4                |
| DVWA-VM2  | No                  | 10.0.0.6/10.0.0.5/10.0.0.4/10.2.0.4                |
| ELKServer | No                  | 10.0.0.6/10.0.0.5/10.0.0.7/10.0.0.4                |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because DECREASES TIME AND INCREASES EFFICIENCY
What is the main advantage of automating configuration with Ansible? PORTABLE/REPEATABLE

The playbook implements the following tasks:
- INSTALL DOCKER.IO
- INSTALL PYTHON MODULE
- LAUNCH CONTAINER

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker Image](docker ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name     | IP Address |
|----------|------------|
| Web-1    | 10.0.0.4   |
| Web-2    | 10.0.0.5   |
| DVWA-VM2 | 10.0.0.7   |
| Jump Box | 10.0.0.6   |

We have installed the following Beats on these machine: FILEBEATS - SYSTEM LOGS

These Beats allow us to collect the following information from each machine:
- Filebeats collects and forwards log data. Expect to see syslog for message logging which provides information on the originating process, timestamp and the hostname/IP of the device.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the SSH KEY file to JUMP BOX.
- Update the ANSIBLE HOST file to include ELK VM
- Run the playbook, and navigate to ELK CONTAINER to check that the installation worked as expected.

- Which file is the playbook? filebeat-7.4.0-amd64.deb
- Where do you copy it? https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.4.0-amd64.deb
- Which file do you update to make Ansible run the playbook on a specific machine? /etc/ansible/hosts
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? ELK server name is added to the ansible hosts file, the Filebeat is added to the filebeat config file with the IP address of the ELK machine.
- Which URL do you navigate to in order to check that the ELK server is running?  http://[your VM IP]:5601/app/kibana, for filebeats navigate to the filebeat installation page

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
