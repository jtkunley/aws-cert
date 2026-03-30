# 2. Windows File Server, DataSync, and FSx

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

- Scenario summary: A company keeps data on an on-premises Windows file server and needs it available in AWS for instances already in a VPC, with daily growth, incremental updates, and private connectivity already available.
- Primary driver: The answer must provide a **Windows-style file share inside the VPC**, not only object storage or a share that stays anchored at the edge.
- Decision focus: This question checks whether you select managed SMB file storage in the Region plus scheduled file replication from on premises, instead of NFS-oriented file, object plus transfer protocols, or a hybrid gateway as the main place data lives for cloud workloads.
- Correct answer pattern: Ongoing replication from an on-premises Windows file server into managed Windows file storage in the VPC, using a private network path and a scheduled synchronization service.

- Key services:
  - Amazon FSx for Windows File Server
  - AWS DataSync
  - AWS Direct Connect

- Common distractor services:
  - Amazon Elastic File System (EFS)
  - Amazon S3
  - AWS Transfer Family
  - AWS Storage Gateway (File Gateway)

- Key signals:
  - Windows file server
  - SMB
  - file system in VPC
  - daily replication
  - Direct Connect

- Constraints:
  - The destination must behave like Windows file sharing for applications in AWS.
  - The destination must live where VPC workloads can mount it as their primary file tier.
  - The migration approach must support repeated incremental synchronization after the initial bulk copy.

- Common traps:
  - Choosing Elastic File System with DataSync and mounting it for a classic Windows file-server scenario.
  - Landing files in S3 and using Transfer Family as the main access path for general Windows application storage.
  - Making File Gateway the primary destination for data that migrated Windows instances in the VPC must treat as their file system.

- Why traps are wrong:
  - Elastic File System with DataSync → violates the constraint that the workload is Windows SMB–first rather than NFS-first.
  - S3 with Transfer Family → violates the constraint that the scenario asks for a file system in the VPC, not object storage with FTP-style protocols.
  - File Gateway as the primary cloud destination → violates the constraint that authoritative Windows file storage for instances in AWS should sit in the VPC as managed SMB, not mainly at the on-premises edge.

- Pattern tags:
  - #hybrid-file-migration
  - #windows-smb-shares
  - #vpc-file-storage
  - #incremental-replication
  - #file-versus-object-storage
