# Windows File Server, DataSync, and FSx

## Original question

A company is using an on-premises Windows file server to store 1 TB of data. About 5 GB worth of new data is being produced every day. The company has an AWS Direct Connect connection from the on-premises network to the AWS VPC. As part of the ongoing migration process, about half of its Windows-based workload has been migrated to the AWS cloud. The data stored on the on-premises server needs to be available on a **file system for the servers in AWS**.

Which of the following options is the **recommended migration strategy** for this scenario?

**Option A:** Create an Amazon FSx for Windows File Server share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon FSx.

**Option B:** Create a new Amazon Elastic File System (EFS) share on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon EFS. Mount the EFS share on the Windows servers.

**Option C:** Create an Amazon S3 bucket on the AWS management console. Schedule a daily task on AWS DataSync that will replicate the data between the on-premises Windows file server and Amazon S3. Use AWS Transfer Family to access the files.

**Option D:** Use AWS Storage Gateway - File Gateway to create an SMB share on the on-premises data center to replace the existing Windows file server. Point the existing file shares to the new file gateway share.

## Correct answer

- **Option A** is the recommended approach for this scenario.
- **Amazon FSx for Windows File Server** gives you a **fully managed**, **SMB-native** file system **inside the VPC** that **Windows instances** can use like a traditional corporate share.
- **AWS DataSync** runs **scheduled** jobs with **incremental** updates, **bandwidth** controls, and **verification**, which fits **ongoing replication** from the **on-premises Windows file server** over the **Direct Connect** path that is already in place.

## Why it is correct

- The stem asks for a **file system for the servers in AWS**, not merely a place to store **objects** in a **bucket**.
- **FSx for Windows File Server** is built for **SMB**, **Active Directory** integration, and **Windows-style** permissions and behavior.
- **DataSync** is the usual exam answer when you need **scheduled** or **repeated** copy jobs from **on-premises NFS or SMB** into **S3**, **EFS**, or **FSx**, with **throttling** and **integrity checks**.
- About **5 GB per day** of new data is a good fit for **incremental** sync after you seed the initial **1 TB** over **Direct Connect**.

## Why the other options are wrong

- **Option B:** **Amazon EFS** is **NFS-oriented** and fits **Linux-elastic** file workloads best. It is a **weak** primary answer for classic **Windows file server** language compared with **FSx for Windows**. The combination **EFS plus DataSync plus mount on Windows** is a common **workload and storage mismatch** distractor.
- **Option C:** **Amazon S3** is **object storage**. It does not give **Windows applications** the same **SMB file share** experience the stem describes. **AWS Transfer Family** adds **FTP, SFTP, or FTPS** access into **S3**, which still does not replace a **managed Windows file share in the VPC** for general-purpose file serving.
- **Option D:** **AWS Storage Gateway File Gateway** presents **SMB** **on premises** with **S3** as the backing store. That design keeps the **emphasis at the edge** and does **not** meet the goal of hosting the data on an **AWS-resident Windows file system** for **instances in the VPC** as cleanly as **FSx**. It also describes **replacing** the on-premises server with a **local gateway** share instead of **landing** the dataset in **FSx** for **migrated** workloads.

## Trap type

- **Wrong file protocol or workload pairing:** **EFS** (**NFS**, **Linux-leaning**) presented next to **DataSync** for a **Windows file server** story.
- **Object versus file:** **S3** plus **Transfer Family** does not satisfy **SMB file system in the VPC** for **Windows** app servers the way **FSx for Windows** does.
- **Hybrid edge versus cloud-native file:** **File Gateway** on premises backs **SMB** with **S3**; the stem wants data on a **file system for servers in AWS**, which points to **FSx** in the **VPC**, not replacing the server with a **local gateway** share as the primary answer.

## Services involved

- [Amazon VPC](../services/amazon-vpc.md)
- [Amazon FSx for Windows File Server](../services/amazon-fsx-for-windows-file-server.md)
- [AWS DataSync](../services/aws-datasync.md)
- [AWS Direct Connect](../services/aws-direct-connect.md)
- [Amazon Elastic File System (EFS)](../services/amazon-efs.md)
- [Amazon S3](../services/amazon-s3.md)
- [AWS Transfer Family](../services/aws-transfer-family.md)
- [AWS Storage Gateway](../services/aws-storage-gateway.md)

## Pattern tags

- [Hybrid cloud storage migration](../patterns/hybrid-cloud-storage-migration.md)
- [DataSync migration and replication](../patterns/datasync-migration-replication.md)
- [Windows managed file storage (SMB)](../patterns/windows-managed-file-storage-smb.md)
- [File storage vs object storage](../patterns/file-storage-vs-object-storage.md)
- [Storage Gateway hybrid access](../patterns/storage-gateway-hybrid-access.md)

## Question Seed

- Scenario summary: **Hybrid** migration with a **Windows file server** on premises (**~1 TB**, **~5 GB/day** new data), **Direct Connect** into a **VPC**, part of **Windows** workloads already in **AWS**, and a requirement that the data live on a **file system** consumed by **servers in AWS**.
- Correct answer pattern: **Amazon FSx for Windows File Server** as the **managed SMB file system** in the **VPC** for **AWS** instances; **AWS DataSync** on a **schedule** for **incremental replication** from on premises over the **private** path (**Direct Connect**).
- Key services: **Amazon FSx for Windows File Server**, **AWS DataSync**, **AWS Direct Connect**, **Amazon VPC**; distractors use **Amazon EFS**, **Amazon S3**, **AWS Transfer Family**, **AWS Storage Gateway** (**File Gateway**).
- Key signals:
  - **Windows file server** and **SMB** semantics in the scenario.
  - Phrase **file system for the servers in AWS** (not “archive to a bucket”).
  - **Scheduled daily** replication language paired with **DataSync** in the options.
- Constraints:
  - Destination must behave as a **Windows-friendly file share** in **AWS** for **EC2** or other **VPC** compute.
  - **Ongoing** sync after a large initial volume (**incremental** daily churn).
  - **Private network** between on premises and **VPC** is already available (**Direct Connect**).
- Common traps:
  - **EFS** **plus** **DataSync** and “mount on **Windows**.”
  - **DataSync** to **S3** **plus** **Transfer Family** for access.
  - **File Gateway** **replacing** the on-premises file server while **cloud** servers still need **authoritative** **FSx** in **AWS**.
- Why traps are wrong:
  - **EFS** is the wrong primary **protocol** and **workload** fit for classic **corporate Windows** shares versus **FSx for Windows**.
  - **S3** is **object** storage; **Transfer Family** is **FTP-family** protocols into **S3**, not a **VPC SMB file system** for general app file serving.
  - **File Gateway** optimizes **on-premises** **SMB** with **S3** backing; it does not place the **corpus** on **FSx** **in the VPC** for **migrated** **AWS** **Windows** servers as cleanly as the keyed answer.
- Pattern tags:
  - #hybrid-cloud-storage-migration
  - #datasync-migration-replication
  - #windows-managed-file-storage-smb
  - #file-storage-vs-object-storage
  - #storage-gateway-hybrid-access
