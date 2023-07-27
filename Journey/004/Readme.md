<!-- This is a template you can use for quick progress days. It removes a lot of the steps we encourage you to share in the longer template 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

# New post title here

## Cloud Research

## AWS Compute

### **AWS Lambda**

Lambda is a serverless compute service/function that run in response to events/triggers.

- Even event/triggers occurs, lambda function can run for up to 15 minutes **maximum.** Running environment stays active for a period of time and then it shuts down by itself.
- Since its a FaaS, you are only responsible for your code. Lambda manages all operations such as memory, CPU, network. Downside of this is that you can not customize like an EC2 since you have no control in instance. (you can choose IaaS(EC2) or PaaS(Elastic Beanstalk) if you want more control) Logging is also managed by Lambda. (send it to CloudWatch)

### **AWS API Gateway**

API gateway is fully managed to create, publish, maintain, monitor and sucre APIs at any scale.

- It act as a front door for the applications to reach data, business logic from your backend services.
- You can create either RESTful APIs or WebSocket API.
- It also supports containerized and serverless workloads.
- It can handless accept and process up to hundreds of thousands of concurrent API calls, traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management.
- It has no minimum fees or startup cost. You only pay API calls you receive and the amount of data transferred out. Its also has tiered pricing model.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\API_gateway.png'>

### **EC2**

Provides resizable compute capacity in the cloud. (VMs).

- It has broad number of instance type, size and pricing model to consider.
- You can and should manage the underlying infrastructure.

- Container management tools can be divided into three. Registry, orchestration, and compute.
  **1-** Services that give you a secure place to store and manage your container images→ **ECR**
  **2-** Orchestration that manages when and where your containers run → **ECS**, **EKS**
  **3-** Flexible compute engines to power your containers → **Fargate**

### **ECS**

Fully managed container orchestration service that can be used for deploy, manage and scale containerized applications.

- Perform system operations such as creating custom scaling and capacity rules, and observe and query data from application logs and telemetry.
- Automatic scaling and pay-as-you-go pricing across multiple AWS compute can reduce cost.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\ECS.png'>

### **EKS**

It can provide a way to start, run, and scale Kubernetes.

- Efficiently run distributed training jobs using the latest Amazon Elastic Compute Cloud (EC2) GPU-powered instances, including Inferentia, and deploy training and inferences using Kubeflow.
- On-premises, EKS provides a consistent, fully-supported Kubernetes solution with integrated tooling and simple deployment to AWS Outposts, virtual machines, or bare metal servers.
- Elastic Load Balancing for load distribution.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\EKS.png'>

### **AWS Fargate**

It can be used with ECS to run containers without managing servers or cluster of EC2 instances (serverless.)

- Each Fargate task has its own isolation boundary and doesn’t share the underlying kernel, CPU resources, memory resources, or elastic network interface with another task.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\Fargate.png'>

## AWS Database

### Aurora

Fully managed relational database engine that’s compatible with PostreSQL and MySQL and its a part of RDS actually.

- High throughput enterprise-level database.
- Storage can grows automatically to the 128 tebibytes(TiB).
- It also automates and standardizes database clustering and replication.
- Aurora Serverless automate the processes of monitoring the workload and adjusting the capacity for your databases. Auto scaling exists and you're charged only for the resources that your database clusters consume.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\Aurora.png'>

### **RDS Proxy**

With this, your applications can pool and share database connections to improve their ability to scale. RDS Proxy makes applications more resilient to database failures by automatically connecting to a standby DB instance, while preserving application connections. By using RDS Proxy, you can also enforce AWS Identity and Access Management (IAM) authentication for databases, and securely store credentials in AWS Secrets Manager.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\rds_proxy.png'>

### DynamoDB Streams

DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table, and stores this information in a log for up to 24 hours.

- Each stream record appears exactly one time in the stream.
  DynamoDB Streams supports the following stream record views:

- **KEYS_ONLY** — Only the key attributes of the modified item
- **NEW_IMAGE** —The entire item as it appears after it was modified
- **OLD_IMAGE** —The entire item as it appears before it was modified
- **NEW_AND_OLD_IMAGES** —Both the new and the old images of the item

### **Event-Driven Architectures**

An event-driven architecture uses events to invoke and communicate between decoupled services. It has three main components which are event producers, event routers and event consumers.
A producer publishes an event to the router, which filters and pushes the events to consumers. Producer services and consumer services are decoupled, which means that they can be scaled, updated, and deployed independently.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\event_driven.png'>

### Amazon EventBridge

EventBridge is a serverless event bus service that you can use to connect your applications with data from various sources.

All events that come to EventBridge are associated with an event bus. Rules are tied to a single event bus, so they can only be applied to events on that event bus.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\EventBridge.png'>

### **SNS**

Amazon SNS is a managed service that provides message delivery from publishers to subscribers. Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel.

- It also supports payload-based message filtering

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\SNS.png'>

### Decoupling

### SQS

Amazon SQS is fully managed message queuing service for decoupling.

<img src='C:\Users\Asilkan\Desktop\100DaysOfCloud\100DaysOfCloud\images\SQS.png'>

- Visibility timeout: The length of time that a message received from a queue (by one consumer) won't be visible to the other message consumers.
- Message retention period: The amount of time that Amazon SQS retains messages that remain in the queue. By default, the queue retains messages for 4 days. You can configure a queue to retain messages for up to 14 days.
- Delivery delay: The amount of time that Amazon SQS will delay before it delivers a message that is added to the queue. For more information, see [Amazon SQS delay queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-delay-queues.html).
- Maximum message size: The maximum message size for the queue.
- Receive message wait time: The maximum amount of time that Amazon SQS waits for messages to become available after the queue gets a receive request.
- Enable content-based deduplication: Amazon SQS can automatically create deduplication IDs based on the body of the message.
- Enable high throughput FIFO: This feature enables high throughput for messages in the queue. Choosing this option changes the related options (deduplication scope and FIFO throughput limit) to the required settings for enabling high throughput for FIFO queues.
- Redrive allow policy: This policy defines which source queues can use this queue as the dead-letter queue.
- Message limit size is 256KB that means it contains short messages.
