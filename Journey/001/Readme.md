<!-- This is a template you can use for quick progress days. It removes a lot of the steps we encourage you to share in the longer template 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

# Day 1 - Storage and Databases in AWS

## Cloud Research

### **Storage on AWS**

need storage for:

- operating system, software, and system files of our app
- static assets, like photos for the employee headshots
- more structured data, such as the name, title, and location of each employee

Object storage often follows a WORM (write once, read many) model.

**File Storage**

- Tree-like hierarchy (consist of folders and subfolders)
- Treats files as a singular unit and each file has metadata(such as file name, file size, date the file was created)
- Ideal for centralized access to files for sharing multiple host computers.
  **Use-cases**
  - Large content repositories
  - Development environments
  - User home directories

**Block Storage**

- Splits files into fixed-size chunks of data called **blocks**. Each block is addressable, blocks can be retrieved efficiently.
- When data is requested, correct order to form of a file orgazined and present back to the requestor.
- Its fast fast and use less bandwidth
- You can change one block (piece of the file) that contains a character even if you want to change **one character** in a GBs of file.
  **Use-cases**
  - for low-latency operations
  - high-performance enterprise workloads(ERP)

**Object Storage**

- Objects are also treated as a single unit of data.
- Objects are stored in a flat structure instead of a hierarchy.
- Each object is a file with unique identifier.
- When you want to change one character, the entire file must be updated.
- Almost any types of data can be stored.
  **Use-cases**
  - large data sets
  - unstuctured files like media assets, static assests, photos

**Storage for EC2**

**EBS**

Like an external storage → externally attach to your instance via network connection.

- Can be attach multiple EC2 instances at one time with EBS multi-attach features, but mostly use one-to-one relationship with an EC2 instance.
- can be detach from one instance and attach another instance in same AZ to reach the data. That means since its separate from instance, it can still be reachable when the instance(computer) goes down.
- Fixed limit for storage since its external and scalable it can be.
  **Use-Cases**
  - OS → it can be used like EBS-backed AMIs
  - DB
  - ERP → since its reliable to run business-critical apps.
  - Throughput-intensive apps
    Types are - HDD and SSD

**Snapshots**

- Incremental backups that saves only changed parts
- when its used, data stored in S3. Interact with EBS console (its a part of the EC2 console), not S3
- Snapshots can be used to create multiple new volumes in both same or different AZ.

**Instance Storage**

Like an internal storage → directly attach to the underlying physical server

- Ephemeral (temporary), lifecycle of your data ties with lifecycle of your EC2 (if you delete your instance instance store is also deleted as well.)
- has a speed advantage which can be helpful for a cluster-based workloads that needs to replicate your data. Also ideal for temporary storages that changes frequently like buffers, caches…

**S3**

Storage that your data can be retrievable from anywhere on the web.

- Object storage type which means that characteristics are flat structure, unique identifiers and file combined with metadata.
- Regional level and need to be selected when you created a bucket. (which is a must to upload a file in S3)
- Bucket name should be unique universally. (Object name is referred as key name)
  **Use cases** → Backups, media hosting, data lakes, static websites.
- Private by default and can be make it public but most of the cases IAM policies are used for more specific reaches from the internet.
- Server-side encryption and client-side encryption are used to encrypt in transit u can use client-side encryption or SSL.
- **Versioning** makes your bucket can keep multiple version of single object. Also protects you from accidental deletions and overwrites. (for deletion it uses marker.)

**Storage Classes**

---

### **Databases**

**RDS**

Managed relational database. It is managed infrastructure based tasks like patching, scaling restoring by itself.
RDS Engines are:

- **Commercial:** Oracle, SQL Server
- **Open Source:** MySQL, PostgreSQL, MariaDB
- **Cloud Native:** Amazon Aurora

Instance families are

- **Standard**, which include general-purpose instances
- **Burstable Performance**, which provides a baseline performance level, with the ability to burst to full CPU usage.
- **Memory Optimized**, which are optimized for memory-intensive applications

EBS volume for storage types are:

- General purpose (SSD)
- Provisioned IOPS (SSD)
- Magnetic storage (not recommended)

Subnet for DB should be private.

-**Automatic Backups** are turned on by default. You can setup period of time for automatic backups while creating instance. Can be between 0 and 35 days and 0 days setting means disables automatic backups. You also have point in time recovery.

-Manual snapshots can be used for needed automated backups longer than 35 days. (similar to EBS snapshots)

-Multi-AZ deployment make copy of your primary DB instances copy to another AZ synchronously as a standby copy. RDS triggers automatically standby DB if there is an failover.

**DynamoDB**

Collection of items which are collection of attributes.

- Need an unique partition key(primary key) and optionally sort key.
- offers encryption at rest
- Horizontally scaled NoSQL
