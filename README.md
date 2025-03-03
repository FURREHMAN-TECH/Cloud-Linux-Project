# Cloud-Linux-Project (Linux)



 

# Introduction:

As part of my journey to becoming proficient in cloud engineering, I focused on strengthening my foundational skills in version control, Linux, and essential development tools. This project was designed to provide hands-on experience with Git, GitHub, and the command line, while also gaining familiarity with markdown for documentation. I utilized resources like the Learn to Cloud platform to structure my learning and built practical knowledge through key actions, such as setting up my development environment with Visual Studio Code (VS Code), Azure and working with version-controlled repositories. By applying these tools and techniques, I gained the necessary skills to efficiently collaborate in cloud development projects and prepare for future cloud certifications.

 

# Project:

# Cloud Infrastructure Setup and Configuration for CTF Challenge

**Virtual Machine Setup (Ubuntu Linux) on VirtualBox**

- Provisioned a Linux-based virtual machine using an Ubuntu ISO on Oracle VirtualBox.
- Installed Visual Studio Code (VS Code) on the VM using the following commands:
- sudo apt update
- sudo apt install code
- code

# Directory Setup for CTF Lab Repository

**Created a directory named 12c using the mkdir command:**
- mkdir 12c
- Cloned the required CTF repository into the 12c folder from GitHub:
- git clone https://github.com/learntocloud/linux-ctfs

# Provisioning Azure VM for Lab Environment

- Logged into the Azure portal and created a new Virtual Machine, "SSH-LAB-VM", with an Ubuntu 24.04 operating system.

 # Terraform Installation and Setup on Local Machine

**Installed Terraform on the local VM using Snap:**
- sudo snap install terraform

  
# Cloning the LTC Linux Challenge Repository

**Cloned the Azure-specific configuration repository from GitHub:**
- git clone https://github.com/learntocloud/ltc-linux-challenge
- Navigated to the azure folder within the repository:
- cd ltc-linux-challenge/azure

# Azure CLI Authentication

**Logged into the Azure portal using Azure CLI:**
- az login

# Terraform Initialization

**Initialized the Terraform configuration to prepare for infrastructure provisioning:**
-- Ran terraform init

# Infrastructure Deployment with Terraform

**Applied the Terraform configuration to deploy resources in Azure, with the appropriate region and subscription ID variables:**
- terraform apply -var az_region="MY_AZURE_REGION" -var subscription_id="MY_AZURE_SUBSCRIPTION_ID"
- Upon successful execution, retrieved the public IP address of the provisioned virtual machine.

# SSH Connection to Azure VM

**Using the VS Code command palette, established an SSH connection to the Azure VM using the following SSH command:**
- ssh CTF_USER@IP_ADDRESS
- Entered the password to securely log into the CTF VM and proceeded with the lab tasks.
 

 

# Challenge 1: Find and Read a Hidden File in the ctf_challenges Directory

**Skills: Basic file listing, hidden files concept**
**Hint: Hidden files in Linux begin with a special character (.)**
![image](https://github.com/user-attachments/assets/c62cf2c5-23bb-4a8d-9bde-171a13c1caa3)

- Navigated to the ctf_challenges directory:
- cd ctf_challenges
- Listed all files, including hidden ones, using the -a flag with the ls command:
- ls -a
- Located and viewed the contents of the hidden file .hidden_flag:
- cat .hidden_flag

#  Challenge 2: The Secret File

**Skills: File searching, directory navigation**
**Hint: Use tools that allow you to search through directory structures**

- Searched for files containing the word "secret" in their name under the home directory using the find command:
- find ~ -name "*secret*"

# Challenge 3: The Largest Log

**Skills: File size analysis, sorting, log navigation**
**Hint: Identify a very large file by inspecting file details, and view it partially to avoid overwhelming the terminal.**

- Navigated to the /var/log directory:
- cd /var/log
- Listed the files with detailed information (including size) using ls -lh:
- ls -lh
- Identified the unusually large file and used the head and tail commands to view its contents partially:
- head -n 10 filename
- tail -n 10 filename

# Challenge 4: The User Detective

**Skills: User management, system files, permissions**
**Hint: Determine which user the UID corresponds to and check their configuration files.**

- Accessed the root account to investigate user configurations:
- sudo -s
- Navigated to the user's home directory:
- cd /home/flag_user
- Checked the user's configuration file .profile:
- cat .profile
- Used getent to retrieve information about the user with UID 1002:
- getent passwd 1002

# Challenge 5: The Permissive File

**Skills: Permission understanding, file searching
Hint: Look for files with unusually permissive permissions and ownership.**

- Navigated to the /opt directory and listed all files:
- cd /opt
- ls -a
- Reviewed the permissions of files within the directory using ls -l:
- ls -l
- Identified the system.conf file with wide-open permissions.
- Entered the root account using sudo -s and amended the file's permissions to restrict access:
- sudo -s
- chmod 600 system.conf
  
# Challenge 6: The Hidden Service

**Skills: Process management, networking tools, service inspection
Hint: Consider the type of service running on port 8080 and how to interact with it.**

- Retrieved the IP address of the host using ip addr show:
- ip addr show
- Connected to the service running on port 8080 using telnet:
- telnet 10.0.1.4 80
- 80

# Challenge 7: The Encoded Secret

**Skills: Base64 encoding/decoding, command piping
Hint: Notice that the flag has been processed twice by an encoding algorithm; think about how to reverse this in sequence.**

- Used base64 decoding twice in sequence to decode the encoded flag:
- base64 -d <(base64 -d encoded_flag.txt)

# Challenge 8: SSH Key Authentication

**Skills: SSH configuration, key management, security practices
Hint: Inspect the SSH directory structure and verify file permissions to uncover hidden files.**

- Navigated through the directories and used ls -lh to view the file permissions of SSH-related files:
- ls -lh ~/.ssh
- Accessed the contents of the authorized_keys file to configure SSH key authentication:
- cat ~/.ssh/authorized_keys

# Challenge 9: DNS Troubleshooting


**Skills: DNS troubleshooting, file editing
Hint: Compare the current DNS configuration with its backup to understand what has changed.**

- Entered the /etc directory and listed all files:
- cd /etc
- ls -a
- Compared the current DNS configuration (resolv.conf) with its backup (resolv.conf.bak) using diff:
- diff /etc/resolv.conf /etc/resolv.conf.bak
- Used vimdiff to view the differences side by side:
- vimdiff /etc/resolv.conf /etc/resolv.conf.bak
