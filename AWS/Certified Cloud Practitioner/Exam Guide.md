# Cloud Concepts

## 1. Benefits of AWS Cloud

### Design Principles of AWS Cloud

> Knowledge of: Value Proposition of AWS Cloud

Skills in understanding:
- Economies of Scale.
- Benefits of Global Infrastructure
	- Speed of Deployment
	- Global reach
- Advantages of the following:
	- High Availability
	- Elasticity
	- Agility
## Benefits of & Strategies for Migrating to AWS Cloud

## Concepts of Cloud Economics

## 2. Security & Compliance

## AWS Shared Responsibility Model

### 2.2 AWS Cloud Security, Governance, and Compliance

Knowledge of:
- AWS Compliance & Governance Concepts
- Benefits of Cloud Security (eg. Encryption)
- Where to capture and locate logs that are associated with cloud security.
	- Cloud Trail

Skills in:
- Identifying where to find AWS compliance information
	- AWS Artifact
- Understanding compliance needs among geographic locations or industries
	- AWS Compliance
- Describe how customers secure resources on AWS
	- Amazon Inspector
	- AWS Security Hub
	- Amazon GuardDuty
	- AWS Shield
- Identifying different encryption options
	- Encryption in transit
	- Encryption in rest
- Recognizing compliance requirements that vary among AWS services

### 2.3 AWS Access Management Capabilities

Knowledge of:
- Identity & Access Management (IAM)
	- **Users**
		- Mapped to a physical user for access to AWS Console
	- **Groups**
		- Contain users only
	- **Policies**
		- JSON Documents outlining permissions for users, roles, or groups
	- **Roles**
		- IAM Identity with a specific set of permissions
		- For Users, EC2 Instances, and Other AWS Services
	- **Security**
		- MFA
		- Password Policy
	- **AWS CLI**
		- Manage AWS services via cmd-line scripting
	- **AWS SDK**
		- Manage AWS services via preferred programming language
	- **Access Keys**
		- Used to authenticate when using the AWS CLI/SDK
	- **Audit**
		- Credential Reports
			- Can be generated once every four hours
			- Lists all users in the account and the status of their credentials
				- passwords
				- access keys
				- MFA devices
		- Access Advisor
			- Data analytics leverages the "service last accessed" information for accounts, and organizations to optimize the principle of least privilege when it comes to granting permissions.
- Importance of protecting the AWS root user account
	- **AWS Root User Account**
		- Default user and associated credentials provided upon creating a new AWS account.
		- Contains access to all AWS resources.
		- Should not be used unless the following tasks need to be done:
			- Change account settings
				- account name,
				- email address,
				- root user password
				- root user access keys
			- Restore IAM user permissions
				- Suppose the root user account "accidentally" revokes it's admin privileges and their are no other account has permission to restore said privileges, then the IAM root account can be used to restore them.
			- Activate IAM access to the billing and cost management console.
			- View certain Tax invoices
				- VAT invoices from AWS Inc. Amazon Internet Services Private Limited (AISPL)
			- Close the AWS account
			- Register as a seller in the reserved instance marketplace
			- Configure an S3 bucket to enable MFA
			- Signup for AWSGovCloud
- Principle of least privilege
	- A user/group/role is provided the minimum levels of access/permissions needed to perform their tasks.
	- Use AWS Access Advisor regularly to make sure the principle of least privilege is being applied towards users/groups/roles.
- AWS IAM Identity Center
	- Central place to manage users/roles/groups for AWS accounts within organizations
### 2.4 Components & Resources For Security
- Security Features
	- Security Groups
	- Network ACL
	- WAF
- Security Information
	- AWS Knowledge Center
	- AWS Security Center
	- AWS Security Blog
- AWS Trusted Advisor
## 3. Cloud Technology & Services

### 3.1 Deploying & Operating in AWS Cloud
- API, SDK, CLI
- AWS Management Console
- Infrastructure as Code (IaC)
- One-time Operations vs Repeatable Processes
- Deployment models
	- cloud
	- hybrid
	- on-premises
- Connectivity Options
	- AWS VPN
	- Direct Connect
	- Public Internet
### 3.2 AWS Global Infrastructure
- High Availability
	- Multiple AZ
- Regions
	- Multiple Regions
		- Disaster Recovery
		- Business Continuity
		- Low Latency for end users
		- Data Sovereignty
- Availability Zones (AZ)
	- Do not share single points of failure
- Edge Locations
	- Benefits
		- CloudFront
		- Global Accelerator
- Wavelength Zones
- Local Zones
### 3.3 AWS Compute Services
#### EC2
- Instance Size + Types (CPU + RAM)
	- General purpose
		- Balance of compute/memory/networking resources
		- Ideal for web-servers/code repositories
	- Compute optimized
		- Ideal for compute bound applications that benefit from high performance processors.
			- Batch processing workloads
			- media transcoding
			- high performance web servers
			- high performance web servers
			- scientific modeling
			- dedicated gaming servers
			- ad servince engines
			- ML inference
	- Memory optimized
		- Ideal for workloads that process large datasets in memory
	- Accelerated computing (GPU Based)
		- Floating point number calculations
		- Graphics processing
		- Data pattern matching
	- Storage optimized
		- High sequential read/write to very large data sets in local storage
		- Low latency, random I/O operations Per second (IOPS)
	- HPC Optimized
		- High computing workloads at scale
			- Complex simulations
			- Deep learning workloads
- AMI - Amazon Machine Image (OS)
	- Region specific but can be copied across regions
	- Analogous to Docker Images
- Storage
	- 
	- S3
		- Scalable
		- Accommodates complex queries
- Security Groups
	- Firewall attached to EC2
- EC2 User Data
	- Script launched at the start of an instance
	- Analogous to Docker RUN command
- Purchasing Options
	- On-Demand
		- Pay by the seconds with minimum 1 minute
	- Spot
		- Use spare EC2 capacity for significantly less then On-Demand pricing
		- Useful for
			- Data analysis
			- batch jobs
			- background processing
			- optional tasks
	- Reserved
		- 1 or 3 year type
		- Can be paid: all upfront, partial upfront, no upfront
		- Standard
			- Cheepest
			- Can be sold on reserved instance market place
		- Convertible
			- Not as cheep as standard
			- Can be converted to other convertible instance types
	- Dedicated
		- Host
			- Control over the server that EC2 is deployed on
		- Instance
			- Running on a host dedicated to the AWS account
#### ELB & ASG
- ELB - Elastic Load Balancers
	- Distribute traffic across EC2 instances accross AZs
	- Supports health checks
	- Types
		- Application (HTTP - L7)
		- Network (TCP -L7)
		- Gateway (L3)
- ASG - Auto Scaling Groups
	- Implement elasticity accross multiple AZ
	- Grow/Shrink EC2 instances based on system demand
	- Replace unhealthy instances
	- Used with ELB
#### Containerized Options
- EKS - Elastic Kubernetes Service
- ECS - Elastic Container Service 
#### Serverless
- Fargate
	- EC2/Storage is managed
- Lambda
### 3.4 AWS Database Services
- EC2 Hosted
	- You take care of everything
- AWS Hosted
	- Integrates easily with CloudWatch for backup/scaling failure notifications
	- RDS/Aurora
	- Automatically replicates to an instance in a different AZ
	- Managed by AWS
		- setup
		- provisioning
		- patching
		- backup
			- every 24h
		- recovery
		- failure detection
#### Relational Databases
- RDS
	- Similar to hosting on EC2 but provisioning and db management is taken care of by AWS
	- Reliability is achieved by turning on Multi-AZ and replicate it synchronously to other standby replicas in different AZs.
	- Supports
		- MySQL/PostgreSQL compatible
		- MariaDB
		- Microsoft SQL Server
		- Oracle
- Aurora
	- MySQL/PostgreSQL compatible
	- Each instance by default has 6 copies spread across 3 AZs
#### NoSQL Databases
- DynamoDB
	- Key-Value
		- Value is structured
	- Fully managed
	- Serverless
	- DynamoDB Accelerator (DAX)
	- Improve read performance and achieve microsecond latency
- DocumentDB
	- Document
		- Value is unstructured
	- MongoDB 
##### In-Memory Databases
- ElastiCache
	- Used to support existing db
- MemoryDB
	- Redis
	- Persists data
#### Other Services
- Warehouse - OLAP: Redshift (SQL)
- Athena: Query data across S3 (serverless & SQL)
- QuickSight: BI Dashboards (serverless)
- QLDB: Financial transactions ledger
	- immutable journal
	- cryptographically verifiable
- Managed Blockchain
	- Hyperledger Fabric
	- Ethereum blockchain
- Glue: ETL
- Neptune: Graph DB
- Timestream: Timeseries
- Elastisearch: Text search accross services (logs)
#### Migration
##### AWS Database Migration Service
- No downtown for source database during migration
- Database synchronization between source and aws continues until otherwise
##### AWS Schema Conversion Tool
- AWS DMS Schema Conversion (DMS SC)
	- Used to converting schema and objects from source db to target aws db
### 3.5 AWS Network Services
#### VPC - By Region
- Subnets
	- seperate sets of ips in your vpc seperated by AZ
- Gateways
	- Internet Gateway
		- Allows instances with public IP to access internet
	- Transit Gateway
		- Route trafic between all VPC and on-premise data centres through direct connect
	- NAT Gateway
		- Allows instances with private IP to access internet
- Peering Connection
	- Connect two VPCs
- Flow Logs
	- Log IP traffic
#### Security
- Network ACL (Access Control List)
	- Allow/Deny list on the subnet level
- Security Groups
	- Firewall for your aws services
#### Route 53
#### Edge Services
- CloudFront
	- CDN
- Global Accelerator
	- Amazon private network to speed up network traffic
#### Network Connectivity Options
- AWS VPN
	- Allow you to access aws services and within on-premise network
- Direct Connect
	- Connect your on-premise network to aws
### 3.6 AWS Storage Services

#### EBS-Backed
- Per instance
- Network drive
- Mapped to AZ
- Deleted upon termination
- Data is encrypted at rest and in transit between EBS and EC2
#### Instance Store-Backed
- Deleted upon termination
#### EFS/EFS-IA (Infrequent Access)
- NFS Based
- Network file system
- Can be attached to 100s of instances
- Scalable
#### NFx for Windows
- Similar to EFS but for windows
#### S3
- Globally unique name
- Tied to a region
	- Minimum 3 AZ
- Pay for data coming out
##### S3 Security
- IAM Policy
- Bucket policy (public for static site hosting)
- S3 Encryption (turned on by default) for data at rest
##### S3 Versioning + Replication
- Versioning turned off by default
- Replication (must enable versioning)
	- Same-Region
	- Cross Region
##### Storage Classes
- Standard
	- General Purpose
	- Frequently Accessed
- IA
	- Infrequent access
	- Rapid access
- IZ-IA
	- Same as above but stored in 1 AZ
- Intelligent
	- Small monitoring/management fee
	- Moves objects to different S3 tiers depending on their access history
- Glacier
	- Instant
		- Accessed  quarterly
		- Same retrieval speed as standard
	- Flexible
		- Accessed 1-2 times/year
		- SSL for data in transit and encryption for data at rest
		- Data retrieval in minutes
	- Deep
		- Data retention for 7-10years
		- 12hour retrieval times
- Outposts
	- On-premise S3 capabilities
##### Snow Family
##### OpsHub
#### Storage Lifecycle
- Transition actions
	- Objects moving across storage classes
- Expiration actions
	- Objects expiring
#### AWS Storage Gateway
- Allows on-premise services to access AWS storage.
- Caches frequently accessed data
#### AWS Backup
- Services for regularly backing up your S3 storage services
- Use AWS Backup Central Console to monitor your backuped resources
### 3.7 AWS AI/ML
#### AI/ML
- Amazon SageMaker
	- Build/train/deploy ML models at scale
- Amazon Lex
	- Used for building chat bots
- Amazon Transcribe/Poly
	- Transcribe: Speech -> Text
	- Poly: Text to Speech
- Amazon Kendra
	- Generative AI trained against your storage and usage
#### Data Analytics
- Amazon Athena
	- Serverless
	- Allows you to analyze data from S3, and 30 other data sources via SQL/python
- Amazon Kinesis
	- Process and analyze streaming data in realtime
- AWS Glue
	- ETL
### 3.8 Other AWS Services
#### Application Integration Services
- Amazon EventBridge
	- Serverless
	- Eventbus
	- Captures 3rd party events
- Amazon Simple Notification Service (SNS)
- Amazon Simple Queue Service (SQS)
	- Sends message out to everyone
	- Once message consumed, it is destroyed
#### Business Application Services
- AWS Connect
	- Service for setting up customer service contact center
	- Amazon Simple Email Service (SES)
		- Email send/receive service
#### Customer Engagement Services
- AWS Activate (for Startups)
	- Free credits and help to jumpstart your startup
- AWS IQ
	- AWS Certified Freelancers and consulting firms
- AWS Managed Services (AMS)
	- Ongoing management of AWS infrastructure so you can focus on delivering
- AWS Support
	- Developer Support
	- Business Support
	- Enterprise On-Ramp
		- AWS Managed Services
	- Enterprise
#### Developer Tool Services & Capabilities
- AWS AppConfig
	- Part of AWS systemsManager.
	- Central location to deploy app configurations from
- AWS Cloud9
	- Cloud IDE
- AWS CloudShell
	- Instead of using the AWS Console, manage your AWS resources through the cmd-line with AWS CloudShell
- AWS CodeArtifact
	- Manage your artifact versions on AWS
- AWS CodeBuild
	- AWS build service
- AWS CodeCommit
	- AWS Git hosting
- AWS CodeDeploy
	- CD for AWS
- AWS CodePipeline
	- AWS CI + CodeBuild
- AWS CodeStar
	- Get Started Project Templates
	- Integrates all the Code* services into a single dashboard for management
- AWS X-Ray
	- Allows you to debug your AWS distributed services while they are running in production
#### End-User Computing Services
- Amazon AppStream 2.0
	- Stream desktop applications through your browser
- Amazon WorkSpaces
	- VDI Desktops
- Amazon WorkSpaces Web
	- VDI Desktop through browser
#### Front-End Web & Mobile Services
- AWS Amplify
	- Host simple web/mobile apps easily
- AWS AppSync
	- Serverless graphql pub/sub api
#### IoT Services
- AWS IoT Core
	- Gateway to connect IoT devices together
- AWS IoT GreenGrass
	- Gateway to connect IoT devices to AWS services
# Billing, Pricing, and Support

## Compare AWS Pricing Models

## Resources for Billing, Budget, and Cost Management

## Technical Resources & Support Options






