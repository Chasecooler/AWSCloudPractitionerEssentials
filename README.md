# AWSCloudPractitionerEssentials

## Intro to AWS Cloud Concepts 
**SCALABILITY (resize resources as needed), AGILITY (learn from and quickly adapt to change), RELIABILITY, SECURITY**

- **Move from Data Centers to Cloud** -- Before cloud computing, enterprises designed and built own data centers.  If under-planned, risked poor performance; if over-planned (planned for worst case scenario), risked wasting money.  Cloud computing enables customers to access data centers and all of its resources via the internet.  This elastic infrastructure of cloud computing frees enterprises from the constraints of fixed and finite IT infrastructure, and minimizes the uncertainty of forecasting hardware needs.  **ELASTICITY** allows enterprises to easily scale computing resources up (as workload grows) or down (when certain resources are no longer required).  Specifically, the AWS tools Autoscaling and Elastic Load Balancing enable applications to automatically scale up or down based on demand.  With the cloud, customers/enterprises easily adapt their consumption of services to meet seasonal requirements / accommodate new strategic directions.

- **DATA SECURITY** -- Security of customer’s data a top priority for Amazon.

- **HIGH AVAILABILITY AND DEPENDABILITY** -- AWS facilities exist all over the world; as a result, AWS customers can literally have a global reach with just a moment’s notice (lower latency).

- **AGILITY** -- Change management & testing & reliability & capacity planning become more agile and efficient with the AWS cloud.  Since cloud computing learns from and quickly adapts to change, it reduces risks (and reduces the cost of change). 

- **AWS PRIORITIZES RELIABLE COVERAGE** -- The AWS Cloud has a high fault tolerance (system can remain operational even if some components of the system fail).

- **SERVICES** -- Cloud computing offers on-demand delivery of IT resources and applications via the internet; compute and storage resources available whenever needed.  AWS offers compute, storage, databases, analytics, networking, mobile, developer and management tools, IOT, security, and enterprise applications.  AWS’ predeveloped services can be quickly assembled as building blocks – automate software delivery and create security and compliance guardrails.

<br>

## AWS Management Interfaces
**MANAGEMENT CONSOLE, CLI, SDKs (CLI & SDKs are tools to customize AWS features)**

Three ways to use AWS:
- **AWS Management Console (GUI that supports majority of AWS)**
  - Available as a mobile app to access features on the go
  - Resource groups are specific to identities (each user in account can customize)

- **Command Line Interface (CLI – open source tool built for interacting with AWS services)**
  - Programming language agnostic
  - Flexibility to create scripts (automate and repeat deployment of AWS resources)
  - Environments: (i) Linux, (ii) Windows, (iii) Remotely (run commands on Amazon EC2 instances, SSH, or with Amazon EC2 Systems Manager)

- **Software Development Kits (SDKs – offers flexibility to create applications and use AWS in existing applications)**
  - Incorporate the connectivity and functionality of the wider range of AWS Cloud Services into your code
  - Enable applications built on AWS to manage your infrastructure’s code
  - Access AWS using a variety of popular programming languages (JavaScript, Python (boto), PHP, .NET, Ruby, Go, Node.js, C++, Java)

<br>

## AWS Core Services
**EC2, EBS, S3, Global Infrastructure, VPC, Security Groups**

### Elastic Compute Cloud (EC2)
 - **Elastic** – if properly configured, automatically scale servers required by an application according to current demands on that application
 - **Compute** – compute or server resources that are being presented (servers = instances, in AWS lexicon)
 - **Cloud** – cloud-hosted compute resources

Amazon EC2 Instances are (i) pay as you go, (ii) offer a broad selection of hardware and software, and (iii) have global hosting.

**Build and Configure an EC2 Instance** 
 - Login to AWS Console
 - Choose a hosting region
 - Launch EC2 Wizard
 - Select software platform for the instance (choose Amazon Machine Image (AMI))
 - Select hardware capabilities (choose Instance Type)
 - Configure instance Network – default is virtual private cloud (VPC); default auto-assign settings give user a default DHCP address.
 - Add Storage
 - Add Tags – assign the Key Pairs that allow user to connect to instance after it has been launched.
 - Configure Security Group – the set of firewall rules that control the traffic for the instance.
 - Review and Launch
 - Once instance launched, locate public DNS and public IP address; use this DNS info to access EC2 instance via Putty.
<br>

### Elastic Block Store (EBS)
EBS is a storage unit for EC2 instances
 - **Disaster Recovery** – Can backup EBS volume using **snapshots** – AWS allows user to recreate a new volume from a snapshot at any time (like versioning).
 - **Reliability** – EBS volumes designed to be durable and available (data in a volume automatically replicated across multiple servers running in the availability zone).
 - **Security** – Can have encrypted EBS volumes at no additional cost.

**Create, Attach, and Format an EBS Volume to an EC2 Instance**
 - In AWS Console, create EBS volume in same availability zone as EC2 instance(s) to which it will be attached
 - Attach EBS volume to desired EC2 instance from AWS Console
 - Access EC2 instance via SSH; use CLI command *lsblk* to view block storage devices attached to this EC2 instance (this will include the EBS volume just attached through the AWS Console)
 - Can use Linux OS to create a file system on this EBS volume
 - Can mount this EBS volume into a folder on Linux machine
 - At any time can unmount EBS volume from folder – then can detach EBS volume from EC2 instance in AWS Console
 - Once detached/available, can attach this EBS volume to another EC2 instance in same availability zone
<br>

### Simple Storage Service (S3)
Store virtually unlimited number of objects – S3 can handle very large objects such as images, videos, or large data files.
Can access data via AWS Console, CLI, SDKs; can also access data in bucket directly, via REST endpoints (these support HTTP or HTTPS access).

S3 is:
 - **Durable** – data redundantly stored in region
 - **Efficient** – designed for seamless scaling (scales for data growth, application use, and high request volume)
 - **Accessible (offers URL-based access)** – content can be fetched directly over the web (can offload serving of content from your application and allow clients to directly fetch data themselves from S3)

In S3:
 - **Buckets** hold data (retrieved via keys)
 - When creating bucket, name must be DNS-compliant
 - Can add data to bucket via AWS Console (drag and drop) or via AWS CLI.  From AWS Console, can change properties and permissions on a per-object-basis.
 - When retrieving data, can add bucket data to a local folder on an EC2 instance
<br>

### Global Infrastructure
**AWS Global Infrastructure comprised of Regions, Availability Zones, and Edge Locations**
 - **Regions** – geographic areas that host two or more Availability Zones.  Regions are completely separate entities from one another.  Resources in one Region are not automatically replicated to other Regions.  In practice, select a Region that helps minimize latency, lower cost, and adhere to regulatory requirements.
 - **Availability Zones** – collection of data centers in a specific Region.  With reliability in mind, Availability Zones are isolated to protect one Zone from failures in other Zones (if one Zone goes down, the other Zones can handle requests).
 - **Edge Locations** – enable quicker content delivery.  Edge Locations host a Content Delivery Network (CDN) called Amazon Cloud Front.  Requests for content are automatically routed to nearest Edge Location (which is typically located in highly-populated areas) so that the content is delivered faster to the end users.
<br>

### Virtual Private Cloud (VPC)
VPC is the **Networking** AWS service that will meet your networking requirements.

**VPC:**
 - Is a private, virtual network in AWS Cloud (uses same concepts as on-premise networking)
 - Allows complete control of network configuration (ability to isolate and expose resources inside VPC)
 - Offers several layers of security controls (ability to allow and deny specific internet and internal traffic)
 - Is a space into which other AWS services deploy (e.g Amazon EC2 deployed into Amazon VPC and instance protected by structure of network – services inherit security built into network)

**VPC Features:**
 - VPC defines an IP-address space (that is divided into subnets)
 - VPCs are Region-based
 - Each AWS account can create multiple VPCs (that can be used to segregate environments)
 - *IP-address spaces*, *subnets*, and *routing tables* allow you to control what you expose to internet and what you isolate within Amazon VPC.
 - Route tables control traffic between subnets and the internet.  Subnets generally classified as public (direct access to internet) or private (no direct access to internet)
 - *Internet Gateway* needed to make subnets public.
<br>

### Security Groups
Act as built-in firewalls.  Control accessibility to instances.

Control network accessibility to your instances by creating security group rules.
 - HTTP: Port 80
 - HTTPS: Port 443
 - SSH: Port 22

Can create and configure security groups from AWS Console.  Default security group rule denies all inbound traffic and allows all outbound traffic.

<br>

