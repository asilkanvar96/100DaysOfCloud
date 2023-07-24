<!-- This is a template you can use for quick progress days. It removes a lot of the steps we encourage you to share in the longer template 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

# Day3- EC2 Auto Scaling and Elastic Load Balancer

## Cloud Research

**Optimization**

- **\*Active-Passive**:\* With an active-passive system, only one of the two instances is available at a time. One advantage of this method is that for stateful applications where data about the client’s session is stored on the server, there won’t be any issues as the customers are always sent to the same server where their session is stored.
    <p>&nbsp;</p>

- **\*Active-Active**:\* A disadvantage of active-passive and where an active-active system shines is scalability. By having both servers available, the second server can take some load for the application, thus allowing the entire system to take more load. However, if the application is stateful, there would be an issue if the customer’s session isn’t available on both servers. Stateless applications work better for active-active systems.

**Issue with Vertical Scaling**

When you have activate-passive system, you are using vertical scaling with stateful. (only one instance is available at a time). It may be good and secure for low load systems which one of them can store meaningful data . Steps are like this

**1-** Stop passive instance since its not getting any traffic

**2-** Change size or type of instance to match for needs. Then, start the instance.

**3-** Shift the traffic to passive instance that means turn it to activate instance.

**4-** Stop the previous activate instance in order to make this instance the passive instance and change the size or type in order to match current activate instance.

We got two problem about this flow which are **limitation** and **not an automated workload**. Manual work for this flow can be bothersome and cause a potential human based error. For the limitation part, when you reached the scalability limit of an instance, you should create another active-passive system in order to match with needs.

For Active-active system, since its stateless, you can create many instance when needed. Its both horizontally scalable and don’t need an human interaction since its stateless (no need to application changes.)

**Auto Scaling**
<img src="/images/auto-scaling.png">
ELB integrates with EC2 Auto Scaling. Health checks are used before ELB send traffic through a new instance. Two types of health checks are mainly focusing on **using TCP** or **sending and returning of HTTP/HTTPS response code.**
<p>&nbsp;</p>

**EC2 Auto Scaling Components**
There are three main components of EC2 Auto Scaling.

- **Launch template or configuration:** What resource should be automatically scaled? All the information of an instance when a new EC2 instance created are stored in launch templates.
    <p>&nbsp;</p>

- **EC2 Auto Scaling Group:** Where should the resources be deployed?
    <p>&nbsp;</p>

  - **Desired capacity**: Represents the initial capacity of the Auto Scaling group at the time of creation. An Auto Scaling group attempts to maintain the desired capacity. It starts by launching the number of instances that are specified for the desired capacity, and maintains this number of instances as long as there are no scaling policies or scheduled actions attached to the Auto Scaling group.
      <p>&nbsp;</p>

  - **Minimum capacity**: Represents the minimum group size. When scaling policies are set, an Auto Scaling group cannot decrease its desired capacity lower than the minimum size limit.
      <p>&nbsp;</p>

  - **Maximum capacity**: Represents the maximum group size. When scaling policies are set, an Auto Scaling group cannot increase its desired capacity higher than the maximum size limit.
      <p>&nbsp;</p>

- **Scaling policies:** When should the resources be added or removed?
    <p>&nbsp;</p>

  - **Simple scaling** relies on a metric as a basis for scaling. For example, you can set a CloudWatch alarm to have a CPU Utilization threshold of 80%, and then set the scaling policy to add 20% more capacity to your Auto Scaling group by launching new instances.
  <p>&nbsp;</p>

  - **Target tracking** policy lets you specify a scaling metric and metric value that your auto scaling group should maintain at all times. Let’s say for example your scaling metric is the average CPU utilization of your EC2 auto scaling instances, and that their average should always be 80%. When CloudWatch detects that the average CPU utilization is beyond 80%, it will trigger your target tracking policy to scale out the auto scaling group to meet this target utilization.
  <p>&nbsp;</p>

  - **Step Scaling** further improves the features of simple scaling. Step scaling applies “step adjustments” which means you can set multiple actions to vary the scaling depending on the size of the alarm breach.

**ELB**

<img src="/images/ELB.png">

**Note : NLB uses a flow hash routing algorithm, when ALB uses round-robin algorithm**

The process of distributing tasks across a set of resources. (controlling the traffic). You can enable it and redirect the traffic when its needed for some set of instances based on an algorithm(such as round-robin).

- It can be work with on-prem servers.
- You can deploy it across multiple AZ.
- The traffic goes through the ELB to instance and goes back also ELB too.

**Health Checks**

ELB checks the health of an instance if its reachable or not. It also works with Auto Scaling in order to create or terminate an instance. If an instance can not pass a health check, it stop sending traffic to it and make EC2 Auto Scaling know that. Then, EC2 Auto Scaling is remove and replace that instance with a new one.

When EC2 Auto Scaling must scale down an instance as a result of a scaling policy, it notifies the ELB that the instance will be terminated. ELB can stop new connections while preventing EC2 Auto Scaling from terminating the EC2 instance until all connections to that instance have terminated. It is known as **connection draining**.

**ELB components**
<img src="/images/ELB_comps.png">

**Listener:** its used for client-side. The client connect to the listener. It can be many listeners for a single load balancer.

**Target group:** Server-side. Its a backend where your traffic goes such as EC2 Instance, Lambda function or an IP address.

**Rule:** For associating a target group to a listener, you should use rules. It can determine the conditions of the flow of traffic.
