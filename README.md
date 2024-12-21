
# Capstone Project: WordPress Site on AWS

## Project Scenario and Overview

The **Capstone Project: WordPress Site on AWS** involves designing and deploying a scalable, secure, and high-performance WordPress-based website for **DigitalBoost**, a digital marketing agency. The agency seeks a cost-effective solution that can handle increasing traffic while seamlessly integrating with their existing infrastructure. 

This project allowed me to apply and reinforce my DevOps knowledge, particularly in leveraging AWS services to deploy a production-ready application. The tasks completed during this project highlight my ability to design and implement robust cloud architectures.

### Why Am I Doing This?

This project serves the following purposes:

1. **Practical Experience**: To gain hands-on experience in building secure and scalable cloud environments.
2. **Problem-Solving Skills**: To apply concepts of networking, databases, and load balancing in a real-world scenario.
3. **Cloud Expertise**: To enhance my proficiency in AWS services and implement best practices for cloud deployments.

By successfully completing this project, I aim to demonstrate my capability to design reliable cloud-based solutions, further establishing my path to becoming a skilled DevOps engineer.

### Tasks Completed

To achieve the project goals, I completed the following tasks:

1. **VPC Setup**:
   - Configured a Virtual Private Cloud (VPC) to isolate the project infrastructure securely.

2. **Public and Private Subnet Configuration with NAT Gateway Setup**:
   - Designed and implemented a network architecture with public and private subnets for better security and scalability.
   - Configured a NAT Gateway for secure internet access.

3. **AWS MySQL RDS Setup**:
   - Created a managed database using Amazon RDS with MySQL to ensure data availability and reliability.

4. **Setting up Amazon EFS for WordPress**:
   - Configured Amazon Elastic File System (EFS) for scalable, shared file storage.

5. **Application Load Balancer Setup**:
   - Deployed an Application Load Balancer to distribute traffic evenly across instances and improve fault tolerance.

6. **Auto Scaling Group**:
   - Configured an Auto Scaling Group to dynamically handle traffic spikes and ensure high availability.

### Resources Used

#### AWS Services
- **Amazon EC2**: Hosting the WordPress application.
- **Amazon RDS**: Managing the MySQL database.
- **Amazon EFS**: Providing scalable file storage for WordPress.
- **Amazon VPC**: Ensuring network security and isolation.
- **Application Load Balancer**: Distributing traffic and improving fault tolerance.
- **Auto Scaling Group**: Maintaining high availability during traffic spikes.
- **NAT Gateway**: Enabling secure internet access for private subnets.

### WordPress Platform
- **Content Management System (CMS)**: Used to manage and build the WordPress-based website.

### Scripts and Tools

#### Automation Scripts
- CloudFormation templates for provisioning AWS infrastructure.
- Shell scripts for configuring and deploying WordPress components.

#### Tools
- **Visual Studio Code (VS Code)**: Used for writing, editing, and managing scripts and configuration files efficiently.
- **AWS Management Console**: For managing and monitoring AWS resources.
- **Command Line Interface (CLI)**: To execute commands and manage AWS services programmatically.
- **Git**: For version control of scripts and templates.

These tools and scripts streamlined the project's development and deployment process, ensuring automation and reproducibility.

### Pre-requisite Knowledge
- Concepts from **TechOps Essentials** and foundational DevOps projects.

### Conclusion

This project has been instrumental in demonstrating my ability to design and deploy a scalable, secure, and cost-effective WordPress site on AWS. It underscores my proficiency in utilizing AWS services and applying industry best practices to deliver reliable cloud-based solutions.

### Project Deliverables

#### Documentation:
- **Detailed Documentation**: Comprehensive documentation for each component setup, including configurations and implementation steps.
- **Security Measures**: Clear explanation of the security measures implemented to ensure the safety and reliability of the WordPress site.

#### Demonstration:
- **Live Demonstration**: A working demonstration of the WordPress site hosted on AWS, showcasing its functionality and performance.
- **Auto-Scaling Showcase**: Simulation of increased traffic to demonstrate the functionality of auto-scaling and load balancing.

**Project Overview:**

**Screenshot:** 

![Projct_overview](./Images/2.Project_view.png)

### Task 1: Development on Local Workstation

#### Step 1: Implement Version Control with Git

- Initialize Git Repository
- To begin, create the project directory named __WordPress-based__, navigate into it, and initialize it as a Git repository.

__Note__: For this project, I am using __Git Bash__ on a Windows workstation to execute these shell commands, as it provides a Unix-like command-line experience.

__Commands:__
```bash
mkdir WordPress-based
cd WordPress-based
git init
```

### Evaluation Report for the Capstone Project: WordPress Site on AWS

### Task 2: VPC Setup

#### VPC ARCHITECTURE

**Screenshot:** 

![VPC ARCHITECTURE](./Images/3.VPC_architecture.png)

The **Virtual Private Cloud (VPC) Setup** is a critical component of the project, ensuring a secure and scalable environment for hosting the WordPress site. The following steps were performed:

#### Step 2.1: IP Address Range Definition
- Defined the CIDR block for the VPC to allocate private and public IP ranges.
- Ensured the CIDR block supports scalability and future growth needs.

**Screenshots:** 

![VPC_CDIR](./Images/4.CDIR_range.png)

- Showing VPC Name, VPC ID, IPv4 CIDR

![VPC_created](./Images/4b.CDIR_Result.png)

#### Step 2.2: VPC Public and Private Subnet Creation
- Created the VPC with both public and private subnets to host resources securely.
- Configured the VPC for high availability and fault tolerance.

##### Public Subnets
1. **WordPress-Based-Public-subnet-1a**:
   - **CIDR Block**: `10.0.0.0/24`
   - **Availability Zone**: `us-east-1a`
   
   ![Public Subnet 1](./Images/5.Subnet-Public-1a.png)

2. **WordPress-Based-Public-subnet-1c**:
   - **CIDR Block**: `10.0.1.0/24`
   - **Availability Zone**: `us-east-1c`

**Screenshot:**  

![Public Subnet 2](./Images/5b.Public-subnet-1b.png)

##### Private Subnets
1. **WordPress-Based-Private-subnet-1a**:
   - **CIDR Block**: `10.0.2.0/24`
   - **Availability Zone**: `us-east-1a`
   
   ![Private Subnet 1](./Images/6.WordPress-Based-Private-subnet-1a.png)

2. **WordPress-Based-Private-subnet-1c**:
   - **CIDR Block**: `10.0.3.0/24`
   - **Availability Zone**: `us-east-1c`

**Screenshot:**  

![Private Subnet 2](./Images/6.WordPress-Based-Private-subnet-1b.png)

##### Notes

- Each subnet is designed to fit within the same VPC for seamless communication.
- Public subnets are configured to handle traffic from the internet, while private subnets are isolated for backend services.

#### Step 2.3: Internet Gateway and Route Table Configuration

To enable external connectivity for the public subnets, an Internet Gateway was created and attached to the VPC.

##### Internet Gateway Configuration
1. **Internet Gateway Name**: `WordPress-based-IGW`

![Create Internet Gateway](./Images/7.Create_wordpress-IGW.png)

2. **VPC**: `WordPress-based-VPC`

##### Internet Gateway Attachment

After creating the Internet Gateway, it was successfully attached to the VPC `WordPress-based-VPC`.

Below is a screenshot showing the attachment of the Internet Gateway to the VPC:

**Screenshot:**  

![Internet Gateway Attached to VPC](./Images/7b.IGW_create_and_Attached_VPC.png)

#### Route Table Configuration

With the Internet Gateway attached, route tables were configured for public and private subnets.

####  Public Subnet Route Table
##### Screenshot: WordPress-based Subnet Route Table
Below is screenshot of the public route table configurations:

**Public Subnet Route Table Name**: `WordPress-based-Public-RT`

![Public Subnet Route Table](./Images/8.RT-WordPress-Public.png)

- **Destination**: `0.0.0.0/0`
- **Target**: `WordPress-based-IGW`

**Screenshot:**  

![Destination and Target](./Images/9.Add_public_route.png)

- **Associated Subnets**:
  - `Public Subnet 1a`
  - `Public Subnet 1c`

**Screenshot:**  

![Public 1a and Public 1c subnets](./Images/9b.Add_public.subnet_associations.png)

#### Private Subnet Route Table
#### Screenshot: WordPress-based Subnet Route Table
Below is screenshot of the private route table configurations:

**Private Subnet Route Table Name**: `WordPress-based-Private-RT`

**Screenshot:**  

![Private Subnet Route Table](./Images/8b.RT-WordPress-Private.png)

- Default configuration with no internet route.
- **Associated Subnets**:
  - `Private Subnet 1a`
  - `Private Subnet 1c`

**Screenshot:**  

![Private 1a and Private 1c subnets](./Images/9c.Add_private_subnet_associations.png)

### Task 3: Public and Private Subnet Configuration with NAT Gateway Setup

#### NAT GATEWAY ARCHITECTURE

**Screenshot:**  

![NAT GATEWAY ARCHITECTURE](./Images/10.NAT%20Gateway%20Architecture.png)

#### 3.1: Public Subnet Setup
Proper setup of the public subnet for resources accessible from the Internet.  
- **Public Subnets**:
  - `Public-Subnet-1a (10.0.0.0/24)`
  - `Public-Subnet-1c (10.0.1.0/24)`

**Screenshot:** 

![Public Subnet Setup](./Images/11c.Public_subnets.png)

- **Internet Gateway**: 
  - Name: `WordPress-based-IGW`
  - Attached to: `WordPress-based-VPC`
  
**Screenshot:**  

![Public Subnet Setup](./Images/7b.IGW_create_and_Attached_VPC.png)

- **Route Table Configuration**:
 - **Routes**:
   - `Destination`: `0.0.0.0/0`
   - **Target**: `WordPress-based-IGW`

**Screenshot:**  

![Public Subnet Setup](./Images/9.Add_public_route.png)

#### Step 3.2: Private Subnet Setup 
Successful creation of the private subnet for resources with no direct Internet access.  
- **Private Subnets**:
  - `Private-Subnet-1a (10.0.2.0/24)`
  - `Private-Subnet-1c (10.0.3.0/24)`
  
**Screenshot:**  

![Private Subnet Setup](./Images/9c.Add_private_subnet_associations.png)

- **Route Table Configuration**:
  - No direct route to the Internet.
  - Communication is through the NAT Gateway.

**Screenshot:** 

![Private Subnet Setup](./Images/11.NAT_gateway_Configuration.png)

#### Step 3.3: NAT Gateway Configuration (10 Points):
Correct configuration of a NAT Gateway for private subnet Internet access.  
- **NAT Gateway Name**: `WordPress-based-NAT`
- **Public Subnet Used**: `Public-Subnet-1a (10.0.0.0/24)`
- **Elastic IP**: Allocated to NAT Gateway.

**Screenshots:** 

![NAT Gateway Configuration](./Images/10b.NAT%20Gateway_creation.png)

  - Showing NAT Gateway Name, NAT Gateway ID, NAT Gateway State.
![NAT Gateway Configuration](./Images/10c.NAT%20Gateway_details.png)

### Task 4: AWS MySQL RDS Setup

#### Step 4.1: RDS Instance Creation
Proper creation of an Amazon RDS instance with the MySQL engine. Below is the screenshot of the created RDS instance.

**Screenshot:**  

![RDS Instance Creation](./Images/13.RDS_creation.png)

#### 4.2: Security Group Configuration
Correct configuration of security groups for the RDS instance, ensuring proper inbound and outbound rules are set. Below is the screenshot of the security group configuration.

- Inbound rule configuration 

**Screenshots:**  

![Security Group Configuration](./Images/13c.RDS_Security_group_outbound.png)

- Outbound rule configuration 

![Security Group Configuration](./Images/13c.RDS_Security_group_outbound.png)

#### Step 4.3: WordPress-RDS Connection
Successful connection of WordPress to the RDS database, enabling seamless database interactions. Below is the screenshot of the connection setup.

**Screenshot:**  

![WordPress-RDS Connection](./Images/13d.RDS_connection_successful.png)

### Task 5: Setting up Amazon EFS for WordPress

This guide outlines the steps to create and mount an Amazon EFS (Elastic File System) to be shared across WordPress instances. It also details how to configure WordPress to use the shared file system.

#### Step 5.1: Create an Amazon EFS File System

1. Navigate to the **Amazon EFS Console**.
2. Click on **Create File System**.
3. Configure the file system:
   - **Name**: `WordPress-based`
   - **VPC**: Select the VPC where your WordPress instances are running.
4. Leave the default options for performance and throughput.
5. Click **Create** to finish.

**Screenshots:**  

![EFS Creation](./Images/14.EFS_creation.png)

- Security Group Inbound rule

![Security Group](./Images/14.EFS_creation-SG.png)

#### Step 5.2: Mount the EFS File System on WordPress Instances

- #### Install NFS Utilities
On each WordPress instance, install the required utilities for mounting the EFS file system:

__Commands:__
```bash
sudo yum update -y
sudo yum install -y amazon-efs-utils
```

**Screenshot:**  

![Install Amazon EFS](./Images/14b.install_amazon_efs.png)

- #### Create a Mount Point
Create a directory to serve as the mount point for the EFS:

__Command:__
```bash
sudo mkdir -p /mnt/efs
```

**Screenshot:**  

![Create directory](./Images/14c.EFS_created-directory-1.png)

- #### Mount the EFS File System
Mount the EFS file system using its DNS name (replace `<EFS-ID>` with your actual EFS ID):

__Command:__
```bash
sudo mount -t efs -o tls fs-0a50bb60595fc972d /mnt/efs
```

**Screenshot:**  

![Mount efs](./Images/14d1.mount-efs.png)

- #### Verify the Mount
To ensure the EFS file system is mounted, run:

__Command:__
```bash
df -h
```

You should see the EFS file system in the output.

**Screenshot:**  

![EFS file system](./Images/14d.check.png)

- #### Persist the Mount on Reboots
Add the EFS entry to the `/etc/fstab` file:

__Commands:__
```bash
echo "fs-0a50bb60595fc972d /mnt/efs efs defaults,_netdev 0 0" | sudo tee -a /etc/fstab
```

**Screenshot:**  

![create /etc/fstab file](./Images/14e.EFS_add_etc_fstab.png)

### Step 5.3: Configure WordPress to Use the Shared File System

### Move WordPress Files to EFS

1. Stop the Apache web server:

__Command:__
```bash
sudo systemctl stop httpd
```

1. Copy the WordPress files to the EFS mount:

__Command:__
```bash
sudo cp -r /var/www/html/* /mnt/efs/
```

2. Update the `/var/www/html` directory to point to the EFS mount:

__Commands:__
```bash
sudo rm -rf /var/www/html
sudo ln -s /mnt/efs /var/www/html
```

3. Restart the Apache web server:

__Commands:__
```bash
sudo systemctl start httpd
```

**Screenshot:**  

![Configure WordPress](./Images/14f.EFS_shared.png)

#### Verify the Setup

Visit your WordPress site in the browser to ensure it is functioning correctly. All WordPress instances will now share the same EFS storage.

**Screenshot:**  

![Website of WordPress](./Images/16d.WordPress.png)

### Task 6: Application Load Balancer Setup

#### Objective
Set up an Application Load Balancer to distribute incoming traffic among multiple instances, ensuring high availability and fault tolerance.

#### Step 6.1 : Create an Application Load Balancer
- Navigate to the EC2 dashboard.
- Under **Load Balancers**, click on **Create Load Balancer**.
- Choose **Application Load Balancer**.
- Configure:
  - **Name**: `WordPress-based`
  - **Scheme**: `Internet-facing`
  - **IP address type**: `IPv4`
  - Select **VPC** and **Subnets** for high availability.
- Add listeners (HTTP/HTTPS).
- Click **Next** to proceed to security groups.
- Add security group rules to allow inbound traffic (HTTP: 80, HTTPS: 443).

**Screenshots:**  

![Step 1 - Create Load Balancer](./Images/15.Load-balancer-Creation.png)

- Security Group Inbound rule
  
![Security Group](./Images/15b.ALB-SG.png)

#### Step 6.2 : Configure Listener Rules
- In the **Listeners** tab, define routing rules.
- Create a target group:
  - **Target Group Name**: `WordPress-based-TG`
  - **Target type**: `Instance`
  - **Protocol**: `HTTP` or `HTTPS`
  - **VPC**: `WordPress-based-VPC`
- Register EC2 instances (e.g., public/private) with the target group.
- Test routing to ensure traffic reaches the appropriate instance.

**Screenshot:**  

![Step 2 - Configure Listener Rules](./Images/15c.Target-Group.png)

#### Step 6.3 : Integrate Load Balancer with Auto Scaling Group
- Navigate to the **Auto Scaling Groups** section in EC2.
- Create a new Auto Scaling Group or modify an existing one.
- Associate the Application Load Balancer’s target group with the Auto Scaling Group.
- Configure scaling policies based on load or performance metrics.
- Review and save the configuration.

**Screenshot:**  

![Step 3 - Integrate with Auto Scaling Group](./Images/16b.Integrate-loadbalancer.png)

#### Testing the Load Balancer
- Access the Load Balancer DNS name (available in the EC2 dashboard under Load Balancers).
- Verify traffic distribution across instances by refreshing the browser or using tools like **curl**.

**Screenshot 1:** 

- Access the Load Balancer DNS name 

![Testing Load Balancer](./Images/16d.WordPress.png)

**Screenshot 2:** 

![Testing Load Balancer](./Images/16f.WordPress.png)

**Screenshot 3:** 

![Testing Load Balancer](./Images/16g.WordPress.png)

- Curl localhost
![Curl localhost](./Images/17.Showing_connection_Curl.png)

### Task 7 : Auto Scaling Group

#### Objective
Implement Auto Scaling to automatically adjust the number of instances based on traffic load.

#### Step 7.1: Create an Auto Scaling Group
   - Navigate to **EC2 Dashboard** > **Auto Scaling Groups** > **Create Auto Scaling Group**.
   - Name your Auto Scaling Group : `WordPress-based-ASG`
   - Select the **Launch Template** or **Launch Configuration** for your instances.

**Screenshot:**  

![Auto Scaling Group](./Images/16.Auto_scaling_group.png)

#### Step 7.2: Define Scaling Policies
   - Set the following capacities:
    - **Desired Capacity**: The number of instances you want running under normal conditions.
    - **Minimum Capacity**: The lowest number of instances to maintain.
    - **Maximum Capacity**: The maximum number of instances to scale up to.

**Screenshot:**  

![Scaling Policies](./Images/16c.Group_size_and_Scaling.png)

#### Step 7.3: Configure Load Balancer Integration
   - Under **Load Balancing**, attach the previously created **Target Group**.
   - Ensure the Auto Scaling Group routes traffic to the **Application Load Balancer (ALB)**.

![Integrate Load Balancer](./Images/16b.Integrate-loadbalancer.png)

 **Test the Auto Scaling Group**:

   - Simulate traffic load on the ALB to trigger Auto Scaling.
   - Verify the creation or termination of instances based on the defined scaling policies.

**Screenshots:**

![Instances based Scaling Policies](./Images/17b.Instances_ASG.png)

![Simulate traffic](./Images/16e.Minitoring_loadbalancer.png)

### Task 8: Project Documentation: Staging, Committing, and Pushing Code to GitHub

#### Step 8:1 Stage and Commit the Template to Git

In this step, I will add the website files to the Git repository, configure my global Git settings, and make an initial commit with a descriptive message.

- Add Files: Add all website files to the staging area.

- Configure Git User Information: Set up global configuration with my actual git username and email address.

- Commit Changes: Commit the changes with a clear and descriptive message.

__Commands:__
```bash
git add .
git config --global user.name "YourUsername"
git config --global user.email "youremail@example.com"
git commit -m "Initial commit: Add WordPress site template files"
```

**Screenshot:**

![Git Stage and Commit WordPress Site](./Images/18.WordPress_git_add_commit.png)

#### Step 8.2: Push the code to your Github repository

After initializing your Git repository and adding your WordPress site template, the next step is to push your code to a remote repository on GitHub. This step is crucial for version control and collaboration.

- Create a Remote Repository on GitHub: Log into your GitHub account and create a new repository named __WordPress-based__. Leave the repository empty without initializing it with a README, .gitignore, or license.

**Screenshots:**

![Create New Repository Name on Github](./Images/19a.Github_New_Repository.png)

![Push to New Repository](./Images/19b.Github_New_Repository.png)

- Link Your Local Repository to GitHub: In your terminal, within your project directory, add the remote repository URL to your local repository configuration.

- Push Your Code: Upload Your Local Repository Content to GitHub Once you have linked your local repository to GitHub, use the following command to push your commits from your local main branch to the remote repository. This enables you to store your project in the cloud and share it with others.

__Commands:__
```bash
git remote add origin https://github.com/Holuphilix/WordPress-based.git
git branch -M main
git push -u origin main
```

**Screenshot:**

![Git Push origin Main](./Images/20.Wordpress_git_push_origin.png)

