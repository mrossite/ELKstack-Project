## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<br>
<br>

![](diagrams/Maya%20Red%20Team%20Virtual%20Network.drawio.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml
  ![](images/filebeat-playbook.png)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

<br>
### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
-Load balancers distribute traffic amongst the servers, which will protect them from a denial of service attack. Additionally, use of the jump box protects the virtual machines from public exposure, creating redundancy within the system. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.

- Filebeat exports logs from the webservers to the ELK server so that they can be organized and reviewed via an accessed Kibana webpage.  


The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux Ubuntu     |
| DVWA-W1  | Webserver| 10.1.0.5   | Linux Ubuntu     |
| DVWA-W2  | Webserver| 10.1.0.6   | Linux Ubuntu     |
| ELKstack | ELKserver| 10.0.0.4   | Linux Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Red-Team Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed by designated IP addresses. 
- 
<br>
Machines within the network can only be accessed by Red-Team Jump-Box 20.25.56.130


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box | Yes                 | 10.1.0.4-6 10.0.0.4  |
| Web 1    | No                  | None                 |
| Web 2    | No                  | None                 |
| ELKserver| ELK page only       | None                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for seamless scalability. 


The playbook implements the following tasks:
- Installs docker.io
- Increases memory on VM
- Installs pip3 (python)
- Downloads and launches a docker ELK container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](images/sudo%20docker%20ps%20elk.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: 
Webserver 1 10.1.0.5
Webserver 2 10.1.0.6

We have installed the following Beats on these machines: Filebeat

This Beat allow us to collect the following information from each machine:
Filebeat monsters, collects, and exports log files for the designated web servers to a Cabana webpage for ease of presentation and review. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-playbook.yml file to ELK Virtual Machine.
- Update the hosts file to include the IP addresses of the VM's you wish to monitor.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

![](images/hosts%20.png)
