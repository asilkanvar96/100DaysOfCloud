# Some AWS Hybrid Services

## Direct Connect

Establish a dedicated(private) network connection from on-prem to AWS. (It never touches the public internet.) It can reduce network costs and increase bandwidth throughput which made your connection more consistent.

<img src='/images/Direct_Connect.png'>

## Site-to-Site VPN

VPN connection refers to the connection between your VPC and your own on-premises network. In AWS, your instance can not communicate with your remote network by default. You can make a connection by using Site-to-Site VPN. It also support IPsec VPN connections.

Components of Site-to-Site VPN are; **Virtual private Gateway - Customer Gateway**

**VPG** is the VPN concentrator on the AWS side of the VPN connection
**CGW** is a physical device or software application on the customer side of the VPN connection.

<img src='/images/AWS-VPN-Components.png'>

**resource:** https://jayendrapatil.com/tag/customer-gateway/

You can also create **multi site-to-site VPN** connections:

<img src='/images/VPN-Connection.png'>

**resource:** https://jayendrapatil.com/tag/customer-gateway/

## AWS Transit Gateway

**Transit Gateway** is a service that can connects multiple VPCs and on-prems networks from a central place like a hub. It acts as a cloud router. It can use with Site-to-site VPN connections and supports both IPv4 traffic and IPv6 traffic.

<img src="/images/hub-and-spoke-design.png">

## Nat Devices

NAT devices are allowing your private subnet resources to connect to the internet (it can also for connecting to other VPCs and on-prems). Its doing that with replaces the source IPv4 address of the instances with the address of the NAT device. When the NAT device sends response traffic to the instances, the device translates the addresses back to the original source IPv4 addresses.

There are two types of services that you can choose.
**NAT Instances**: It is managed by the customer and created with EC2 instance. You can create it from your own AMI.
**NAT Gateway:** Its managed by AWS and its more consistent and easy to use service. You should specify connectivity types, which are public(default) and private.
<img src="/images/NAT-Gateway-vs-NAT-Instance.png">

**resource:** https://jayendrapatil.com/tag/customer-gateway/

## RDS

### Multi-AZ Deployment

In a Multi-AZ deployment, RDS automatically creates a primary DB instance and synchronously replicates the data to the another instance which is in a different AZ. When problem occurs, RDS automatically fails over to the standby instance which is the other instance in a different AZ.

<img src="/images/RDS Multi-AZ Deployment.png">

Customer also can deploy two standby in three AZ with extra functionalities.

<img src="/images/2_Multi-AZ_Deployment.png">
According to AWS automatic failovers typically happen in under 35 seconds.

### Read Replicas

This functionality can be used for read-heavy db workloads. You can create more than two replicas of a given DB source. Its asynchronously replicate all the data in the source DB.

If you need more CPU capabilities but don’t need more storage, you might choose to create read replicas to offload some of the workload to a secondary instance.

<img src="/images/Read-replicas.png">

## AWS Storage Gateway

Its a hybrid solution to connect on-prem apps with cloud-based storage. You can store your on-prems data in AWS cloud environment. They have three types of storage gateways which are file-based, volume-based and tape-based storage solutions.

<img src="/images/Storage_gateway.png">

### S3 File Gateway

It is one of the Storage Gateway types. It supports file interface into S3. NFS and SMB are supported. Can be used with apps and VMs. Its also optimized and provides low-latency access to data through transparent local caching.  It can be used for on-premises data-intensive Amazon EC2-based applications that need file protocol access to S3 object storage. Some use-cases are storing application data files and backup images.

## Amazon ECS Anywhere

Amazon ECS is a container management service. ECS Anywhere is a feature of ECS. It builds on the ease and simplicity of Amazon ECS to provide a consistent experience across your container-based applications for working with tooling and APIs.

<img src="/images/ECS-Anywhere.png">

## AWS System Manager

In order to see and control your whole infrastructure on AWS, System Manager is used. It provides unified user interface to view operational data from multiple AWS services and automate some tasks across your AWS resources even though its in another region.
You can also group your resources and view and automate your tasks group-level.

<img src="/images/System-manager.png">

**For details:** https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html

**AWS Backup ->** Its used to centralize and automate data protection across AWS services and hybrid workloads. It offers a cost-effective, fully managed, policy-based service that is designed to simplify data protection at scale. You can use AWS Backup with AWS Organizations to centrally deploy data protection policies to configure, manage and govern your backup activity.

<img src="/images/AWS Backup.png">
